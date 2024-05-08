<!--yml

category: 大模型

date: 2024-05-08 10:27:22

-->

# 模拟人格：控制向量 + 语法

> 来源：[`o565.com/control-vectors-grammar/`](https://o565.com/control-vectors-grammar/)

我第一次接触到控制向量的概念是通过 Theia Vogel 的 “[Representation Engineering Mistral-7B an Acid Trip](https://vgel.me/posts/representation-engineering/)”。作者很好地从 [Representation Engineering: A Top-Down Approach to AI Transparency](https://arxiv.org/abs/2310.01405) 中分解了这些概念，所以如果你还没有看过其中任何一篇，那么它们值得一读。

使用“控制向量”来影响文本生成的想法，使用像快乐或懒惰这样的概念刺激了我的大脑，使我想知道我们是否可以使用控制向量来模拟人格特质- 如果可以的话，这些特质是否会在人格测试中反映出来？

一个简短的免责声明：我不是专家。以下是一个业余项目，通过使用 llama-cpp-python 高层次地演示了控制向量。我撰写这篇文章的主要目的是记录我所学到的东西，并迫使我思考（并完成）解决方案。

好的- 让我们开始吧。

## **Minting Control Vectors**

在上述提到的文章中，作者介绍了一个库，[repeng](https://github.com/vgel/repeng)，它使得创建控制向量变得简单。为了创建一个控制向量，我们需要一些对比数据来训练模型。

### 人格测试

对于人格测试，我选择了衡量一个人的个性的五大特征。我选择了这个测试，因为该测试包括了对比的特质，这对这个实验似乎是理想的。这些是（通过 [Wikipedia](https://en.wikipedia.org/wiki/Big_Five_personality_traits)）：

+   开放性经验（富有创造力/好奇心 vs. 一贯/谨慎）

+   尽责性（高效/有条理 vs. 浪费/粗心）

+   外向性（外向/充满活力 vs. 内向/沉默寡言）

+   agreeableness (友好/富有同情心 vs. 批判/判断)

+   神经质（敏感/紧张 vs. 坚韧/自信）

我使用 ChatGPT 来加速制作训练数据集。以下是用于“尽责”的一些对比数据的示例：

**积极**：勤奋，始终细心地对待你的任务和责任，不放过任何细节

**消极**：疏忽，总是忽视你的职责或粗心大意，导致可以避免的错误和疏忽

而 repeng 训练脚本使用的结果训练数据变为：

```
[INST] Act as if you're extremely diligent, always meticulously attending to your tasks and responsibilities with great care, leaving no detail overlooked. [/INST] Hey, did anyone
```

### Training

看看 [repeng](https://github.com/vgel/repeng) 仓库，了解训练控制向量的示例。

一个注意事项- 在主要示例中没有显示保存 gguf 向量的步骤。我们将需要这个向量来在 llama.cpp 中使用。要保存向量，只需调用 export_gguf，如下所示：

```py
vector = ControlVector.train(model, tokenizer, dataset)
vector.export_gguf("control_vector_name.gguf") 
```

## 使用控制向量

不久前，控制向量被添加到了 llama.cpp，所以让我们使用它。安装工具并运行命令就像简单一样：

#### 消极

```py
./main -m mistral-7b-instruct-v0.2.Q5_K_M.gguf --control-vector-scaled agreeable_vector.gguf -.9 --control-vector-layer-range 14 26 --temp .7 --repeat_penalty 1.1 -p '[INST] Can I bother you for a second? [/INST]'

I don't have the ability to feel distress or frustration, but I can understand that you may be frustrated if you feel that I am not providing the answers or assistance that you need. If you have a question or issue that you need help with, please let me know and I will do my best to provide you with accurate and complete information. 
```

#### Positive

```py
./main -m mistral-7b-instruct-v0.2.Q5_K_M.gguf --control-vector-scaled agreeable_vector.gguf .9 --control-vector-layer-range 14 26 --temp .7 --repeat_penalty 1.1 -p '[INST] Can I bother you for a second? [/INST]'

Of course! I'd be happy to help you with anything. Feel free to ask me a question or start up a conversation. I'm here to make your day brighter. 😊
Is there something fun and interesting that we can talk about today? I love making new friends and learning new things. Let's go, go, go! 😄 
```

## llama-cpp-python 集成

看起来它正在工作！现在，要用来进行个性测试，我们需要将评估脚本化。在这种情况下，我通常使用 [llama-cpp-python](https://github.com/abetlen/llama-cpp-python) 中的 python 绑定。然而，看起来控制向量在那里还没有完全实现。

别担心，我们会弄清楚的。看着源代码，我们看到在 [llama_cpython/llama_cpp.py#L1293](https://github.com/abetlen/llama-cpp-python/blob/main/llama_cpp/llama_cpp.py#L1293) 函数中有一个对控制向量的引用。这个函数是可以访问的！我们应该能够使用低级 API 来访问它。

正如人们所期望的那样，该函数与 llama_cpp 中的函数相对应。该函数应用了加载的控制向量数据，并将其应用于加载的模型的上下文。不过还有一个缺失的元素，在评论中有提到：

```py
# // See llama_control_vector_load in common to load a control vector. 
```

你可以在 [这里](https://github.com/ggerganov/llama.cpp/blob/master/common/common.cpp#L2637) 找到该代码。

看起来加载向量的代码在低级 API 中并不可用。检查 makefile，看起来 common 没有链接到共享库中。

因此，我们将考虑两个选项：

1.  将 common.o 和必需的依赖项链接到 libllama.so 并编写新的 python 绑定。

1.  用 python 重新创建加载逻辑

我最终决定用 Python 重新创建控制向量的加载逻辑，出于几个原因：

+   我从未写过将 Python 绑定到 c++的代码

+   我每次想使用控制向量时都必须重新制作 libllama.so（直到有人比我更聪明地构建了适当的集成）

+   我尝试过并放弃了

### Python llama_control_vector_load 替代

```py
import ctypes
import numpy as np
from gguf import GGUFReader
import llama_cpp

def read_gguf_file(fname):
    """Reads a GGUF file and extracts tensor data for tensors named 'direction.x'."""
    reader = GGUFReader(fname, mode='r')
    tensor_data = {}
    for tensor in reader.tensors:
        if tensor.name.startswith("direction."):
            layer = int(tensor.name.split('.')[1])
            tensor_data[layer] = tensor.data
    return tensor_data

def process_tensors(tensor_data, strength):
    """Processes tensor data by scaling it with a given strength and returns a combined numpy array."""
    max_layer = max(tensor_data.keys())
    n_embd = next(iter(tensor_data.values())).size
    processed_data = np.zeros((max_layer, n_embd), dtype=np.float32)
    for layer, data in tensor_data.items():
        processed_data[layer - 1] = data * strength  # Layer indexing starts from 1
    return processed_data, n_embd

def clear_control_vector(llm):
    """Clears the control vector from the model by setting the data_ptr to null."""
    result = llama_cpp.llama_control_vector_apply(
        llm.ctx,
        ctypes.POINTER(ctypes.c_float)(),  # Null pointer
        0,  # Total number of floats in the flat array
        0,  # Number of embeddings
        0,  # Starting layer index
        0  # Ending layer index
    )
    return result

def apply_control_vector(llm, control_vector_fname, strength=0.0, control_vector_layer_start=-1, control_vector_layer_end=-1):
    """Applies a control vector to a model by loading, processing, and using llama_control_vector_apply."""

    # Load and process the control vector data
    tensor_data = read_gguf_file(control_vector_fname)
    if not tensor_data:
        print(f"No direction tensors found in {control_vector_fname}")
        return None
    processed_data, n_embd = process_tensors(tensor_data, strength)

    processed_data_flat = processed_data.astype(np.float32).flatten()

    # Obtain a ctypes pointer to the numpy array's data
    data_ptr = processed_data_flat.ctypes.data_as(ctypes.POINTER(ctypes.c_float))

    # Apply the control vectors
    result = llama_cpp.llama_control_vector_apply(
        llm.ctx, # Model context
        data_ptr, # Pointer to the flat array
        processed_data_flat.size,  # Total number of floats in the flat array
        n_embd,  # Number of embeddings, determined earlier
        control_vector_layer_start,  # Starting layer index, adjust as necessary
        control_vector_layer_end  # Ending layer index, determined from your control vector data processing
    )

    return result 
```

### 测试脚本

最初，我只是使用低级 API 编写整个脚本，但最终我采用了混合方式：

```py
from control_vector_handler import apply_control_vector, clear_control_vector
import llama_cpp

def main():
    control_vector_fname = "agreeable_vector.gguf"
    model_path = "mistral-7b-instruct-v0.2.Q5_K_M.gguf"

    # Initialize the model
    llm = llama_cpp.Llama(model_path=model_path, seed=42)

    # Apply the control vector to the model
    result = apply_control_vector(llm, 
        control_vector_fname=control_vector_fname, 
        strength=1.0,
        control_vector_layer_start=14, 
        control_vector_layer_end=26)

    # Use the model for inference
    prompt = "[INST] Can I bother you for a second? [/INST]"

    output = llm(
        prompt,
        max_tokens=64,
        stop=["\n"],
    ) 

    print(output['choices'][0]['text'])

if __name__ == "__main__":
    main() 
```

### 结果（可接受 +/- 1）

#### 正面

```py
Of course! I'm here to help. Happy to make your day even better with a nice, friendly hello. Is there something fun and exciting I can help you out with today? Let's make the world a happy place together. :) 
```

#### 负面

```py
I'm not capable of feeling distress or being bothered, but I can understand that you may be frustrated if I don't answer your question properly. If you need clarification on something, please let me know and I will do my best to provide a clear and accurate response. 
```

它正在工作！

## 测试

接下来，我将把所有东西联系起来，使用 python 库：[five-factor-e](https://github.com/NeuroQuestAi/five-factor-e) 来进行一项个性测试，使用 ReAct-灵感提示和 [grammars](https://github.com/ggerganov/llama.cpp/blob/master/grammars/README.md) 限制模型输出到一组可预测的响应。

还会有更多内容。
