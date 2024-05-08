<!--yml
category: 面试
date: 2022-07-01 00:00:00
-->

# Google人工智能面试·真·题（附参考答案+攻略）

> 来源：<https://zhuanlan.zhihu.com/p/35978758>

> 安妮 栗子 发自 泽浩寺  
> 量子位 出品 | 公众号 QbitAI

![](https://pic4.zhimg.com/v2-f796da6b2585a3712a4c5204cfa02098_b.jpg)

![](https://pic4.zhimg.com/80/v2-f796da6b2585a3712a4c5204cfa02098_hd.jpg)

可能每个程序猿，都想过加入Google。

然而想要“应试”成功，考验的不仅仅是开发人员的编程技术，还能侧面考验着参赛者的渠道来源是否广泛、背景力量是否强大、脑洞回路是否清奇……

不过，梦是要做的，简历是要投的，说不准面试就来了呢？所以，我们需要为万一砸到头顶的面试，做好一万的准备。

前有万千过桥的应聘大军**发回攻略**，后有民间编程大神发现**隐藏关卡**……是时候来总结一份Google应聘指南了。

P.S. 这份攻略也不仅仅适用于Google（中途落榜的励志哥还被亚马逊挖走了呢~）

## **面前必毒（20道·真·题）**

![](https://pic4.zhimg.com/v2-dac457ad950c95a8a1e87acb167a5901_b.gif)

![](https://pic4.zhimg.com/v2-dac457ad950c95a8a1e87acb167a5901_b.jpg)

Google的技术面试流程就是各家的标配而已，先远程后现场。

面试以强度闻名，可能看看问题就想回家了。这些题目全部由Glassdoor收集统计。不过，顺便看下参考答案也是好的。

**1、求导1/x。**

> 答：-1/x2

![](https://pic3.zhimg.com/v2-9a2a88174f917007f7c483f17600f7f6_b.jpg)

![](https://pic3.zhimg.com/80/v2-9a2a88174f917007f7c483f17600f7f6_hd.jpg)

> 用Python是这样。

![](https://pic4.zhimg.com/v2-611b8d6cadf36d889cc5e59b9e8eb0bf_b.jpg)

![](https://pic4.zhimg.com/80/v2-611b8d6cadf36d889cc5e59b9e8eb0bf_hd.jpg)

**2、画出log (x+10)曲线。**

> 答：如图。只要把logx的图像左移10格。

![](https://pic1.zhimg.com/v2-67aa6e7ce45dcbd7e065d12316bb7b4c_b.jpg)

![](https://pic1.zhimg.com/80/v2-67aa6e7ce45dcbd7e065d12316bb7b4c_hd.jpg)

> 用Python是这样。

![](https://pic1.zhimg.com/v2-365c91bb728b5eb6b2d7104e616ec594_b.jpg)

![](https://pic1.zhimg.com/80/v2-365c91bb728b5eb6b2d7104e616ec594_hd.jpg)

**3、怎样设计一次客户满意度调查？**

> 答：第三题就这么抽象了。不知从何说起的我决定指引各位，可以在搜索引擎里查询一下：“客户满意度和客户忠诚度的计算标准”。

**4、一枚硬币抛10次，得到8正2反。试析抛硬币是否公平？p值是多少？**

**5、接上题。10枚硬币，每一枚抛10次，结果会如何？为了抛硬币更公平，应该怎么改进？**

![](https://pic1.zhimg.com/v2-d22cd771bfa30d1d2fb3037f0d5d7e77_b.gif)

![](https://pic1.zhimg.com/v2-d22cd771bfa30d1d2fb3037f0d5d7e77_b.jpg)

> 答：小数定律或许可以帮到你。  
> 附一个参考资料：[https://medium.com/@lorenz.rumberger/i-think-a-more-advanced-answer-for-the-coin-toss-game-would-use-the-bayesian-method-569696e89271](https://link.zhihu.com/?target=https%3A//medium.com/%40lorenz.rumberger/i-think-a-more-advanced-answer-for-the-coin-toss-game-would-use-the-bayesian-method-569696e89271)

**6、解释一个非正态分布，以及如何应用。**

![](https://pic3.zhimg.com/v2-7f912f1ef96943eb8e56fc5b87d0ca84_b.gif)

![](https://pic3.zhimg.com/v2-7f912f1ef96943eb8e56fc5b87d0ca84_b.jpg)

> 答：不知道面试者遇到是怎样的分布。不过，上个月MIT发表了用妖娆的伽玛分布，帮助自动驾驶系统在浓雾里保持如炬目光的算法。  
> 详情传送门：[点这里](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzIzNjc1NzUzMw%3D%3D%26mid%3D2247495843%26idx%3D4%26sn%3Ddb0fcef1bc290b84ac0c185ade54cdf9%26scene%3D21%23wechat_redirect)

7、为什么要用特征选择？如果两个预测因子高度相关，系数对逻辑回归有怎样的影响？系数的置信区间是多少？

![](https://pic1.zhimg.com/v2-cc77690173f676c4fd71efb5a6eedded_b.gif)

![](https://pic1.zhimg.com/v2-cc77690173f676c4fd71efb5a6eedded_b.jpg)

> 答：需要处理高维数据的时候，很多模型都吃不消。特征选择可以让我们在给数据降维的同时，不损失太多信息。  
> 参考资料传送门：[https://towardsdatascience.com/why-how-and-when-to-apply-feature-selection-e9c69adfabf2](https://link.zhihu.com/?target=https%3A//towardsdatascience.com/why-how-and-when-to-apply-feature-selection-e9c69adfabf2)

**8、K-mean与高斯混合模型：K-means算法和EM算法的差别在哪里？**

> 答：CSDN博主JpHu说，K-Means算法对数据点的聚类进行了“硬分配”，即每个数据点只属于唯一的聚类；而GMM的EM解法则基于后验概率分布，对数据点进行“软分配”，即每个单独的高斯模型对数据聚类都有贡献，不过贡献值有大有小。  
> 传送门：[https://blog.csdn.net/tingyue_/article/details/70739671](https://link.zhihu.com/?target=https%3A//blog.csdn.net/tingyue_/article/details/70739671)

**9、使用高斯混合模型时，怎样判断它适用与否？(正态分布)**

![](https://pic1.zhimg.com/v2-e53968f0ba2f2f37f746599a4ddec0cc_b.jpg)

![](https://pic1.zhimg.com/80/v2-e53968f0ba2f2f37f746599a4ddec0cc_hd.jpg)

> 答：依然，请前往以下页面。  
> 详情传送门：[https://stats.stackexchange.com/questions/260116/when-to-use-gaussian-mixture-model](https://link.zhihu.com/?target=https%3A//stats.stackexchange.com/questions/260116/when-to-use-gaussian-mixture-model)

**10、聚类时标签已知，怎样评估模型的表现？**

> 答： CSDN博主howhigh说，如果有了类别标签，那么聚类结果也可以像分类那样计算准确率和召回率。但是不应该将分类标签作为聚类结果的评价指标，除非你有相关的先验知识或某种假设，知道这种分类类内差距更小——  
> 详情传送门：[https://blog.csdn.net/howhigh/article/details/73928635](https://link.zhihu.com/?target=https%3A//blog.csdn.net/howhigh/article/details/73928635)

**11、为什么不用逻辑回归，而要用GBM？**

![](https://pic1.zhimg.com/v2-0bda02ed7c3b90e67f51c058cd0f9d5b_b.jpg)

![](https://pic1.zhimg.com/80/v2-0bda02ed7c3b90e67f51c058cd0f9d5b_hd.jpg)

> 答：逻辑回归 (LR) 是二元线性分类器。决策边界是线性的，通常适于处理线性问题。如果要捕捉非线性关系，就需要复杂的特征工程，来增强模型的表达能力。  
>   
> GBDT是由多棵决策树组成，最终结果是所有树的结论累加而成。能够发现许多有区分性的特征，更细地划分特征空间。可以处理线性和非线性数据。  
>   
> 参考答案传送门：  
> [https://www.zhihu.com/question/54626685/answer/140610056](https://www.zhihu.com/question/54626685/answer/140610056)

**12、每年应聘Google的人有多少？**

> 答：两百万。大多数人可能都只是顺便投一下，看看会不会中奖。

![](https://pic2.zhimg.com/v2-0cfab53b9b1dd2745b78fcc946b4d951_b.jpg)

![](https://pic2.zhimg.com/80/v2-0cfab53b9b1dd2745b78fcc946b4d951_hd.jpg)

当然，技术题是出不完的，也是答不完的——以下统一不给答案了，请进行自我测试，并注意考试时间。

**13、你给一个Google APP做了些修改。怎样测试某项指标是否有增长**

**14、描述数据分析的流程。**

**15、高斯混合模型 (GMM) 中，推导方程。**

**16、怎样衡量用户对视频的喜爱程度？**

**17、模拟一个二元正态分布。**

**18、求一个分布的方差。**

**19、怎样建立中位数的Estimator？**

**20、如果回归模型中的两个系数估计，分别是统计显著的，把两个放在一起测试，会不会同样显著？**

![](https://pic2.zhimg.com/v2-5ade06e697fe70ff8eca3d32bc9c3421_b.jpg)

![](https://pic2.zhimg.com/80/v2-5ade06e697fe70ff8eca3d32bc9c3421_hd.jpg)

## **不只是技术**

除了这些深刻的技术问题，Google历年的面试中，总有一些直击灵魂的神秘考题。BI也统计了一些，例如：

*   一辆校车可以放进多少个高尔夫球？
*   擦一遍西雅图所有的窗户需要多少钱？
*   井盖为什么是圆的？

再来个长的：

> 你只有两个生鸡蛋，是可以无比坚固也可以无比脆弱的鸡蛋。在一百层的高楼里，在两个鸡蛋都阵亡之前，怎么才能知道它们最高能从几楼摔下来不碎？需要多少步？

鸡蛋表示：

![](https://pic2.zhimg.com/v2-38454b59cddc4ce1b178c1a07a67b2ed_b.jpg)

![](https://pic2.zhimg.com/80/v2-38454b59cddc4ce1b178c1a07a67b2ed_hd.jpg)

  

很好奇，脑洞考题是怎样打分的。友情提示：上述几道题，有些是可以抖机灵的……

如果你想知道答案和更多类似题，可以在量子位公众号（ID：QbitAI）对话界面，回复：“**神秘题**”三个字。

## **史上最正统Google面试宝典**

真题谈完了。虽然面试准备是个老生常谈的话题，但下面这份宝典无论如何你都要看看。

论“血统”，这份宝典最为正宗，因为它是Google招聘官网上专门为“Future Googler”准备的。一起看看招聘方亲自对面试者提出了哪些建议——

![](https://pic4.zhimg.com/v2-5c44f2f923b06487471dcc2ff465bfa1_b.jpg)

![](https://pic4.zhimg.com/80/v2-5c44f2f923b06487471dcc2ff465bfa1_hd.jpg)

**预测面试题**：面试前，你基本可以预测出90%的问题了。“为什么想申请这份工作”“你曾经解决过什么问题”等问题基本在面试中必现，写20个出来先提前准备着有益无害。

**计划**：写出极可能出现的问题后，针对列出你的清单上的每一个问题，写下你的答案。这将帮助你加深对这些问题的印象，是面试时能对答如流的利器。

**Plan B&C**：针对上面这些问题，Google招聘人员建议你最好能准备3个答案。这些备用答案能在第一位面试官不喜欢你的故事时，帮你征服下一位面试官。

**解释**：面试官想要了解你的想法，所以在面试过程中需要展示你的思维过程和最后的解决方案。这个环节不仅是在评估你的技术能力，还在评估你解决问题的灵活性。

**讲故事**：Google面试官希望以会“讲故事”。有一个很有意思的面试小技巧，就是每个问题都应该用一个故事来回答。比如“你怎样领导……”的问题最好就举个例子讲个故事吧~

![](https://pic4.zhimg.com/v2-6250389b1453ee8525fc2a84c85bec31_b.gif)

![](https://pic4.zhimg.com/v2-6250389b1453ee8525fc2a84c85bec31_b.jpg)

**探讨**：在面试过程中你可能会不自觉进入一些问题“圈套”，这是面试官想深入了解当你遇到技术难题中你看重哪些信息，希望看到你如何处理这个问题以及你解决问题的主要方法，这时一定要就你的思维过程进行讨论。

**改进**：思考如何改进你现在的解决方案，让面试官知道你在做什么，为什么要这样做。

**练习**：最后应聘者要时刻谨记熟能生巧。模拟面试环节，自信说出你的答案，直到你能清晰而简明地讲述每一个故事。

看来，准备Google的面试是个时间活~除了技术能力需要过硬以外，单单面试时这20×3个问题的准备也得准备不少时间呢。

对了，已经应聘成功的Google工程师们还给你提了一些技术类问题的“备考”建议，听听老人言，助你面试一臂之力。

[谷歌工程师面试_腾讯视频​v.qq.com![图标](https://pic3.zhimg.com/v2-a772a2982020f0c43d39432a93d041da_180x120.jpg)](https://link.zhihu.com/?target=https%3A//v.qq.com/x/page/j0506uecfxc.html)

## **对，有隐藏关卡！**

应聘Google的方法只有内推、校招和发简历社招这三种？Naive，小看Google工程师的脑洞了，据多位大神在博客上透露，Google的应聘来源还有**秘密渠道**。

如果Google捕捉到你在搜索某个特定的编程术语，可能就会有人邀请你申请这个职位。就有人能解锁这种隐藏关卡~

小哥Max Rosett曾遇到过一个有趣的故事。在用Google搜索“Python lambda函数列表解析”时，搜索界面分裂并向后折叠，一个方框弹出来写着“你在使用我们的语音”，还邀请他去挑战一下。

![](https://pic2.zhimg.com/v2-3cf6f864a82547387e33420fb5d2c6a4_b.jpg)

![](https://pic2.zhimg.com/80/v2-3cf6f864a82547387e33420fb5d2c6a4_hd.jpg)

点击“挑战”后，页面跳转到一个叫“foo.bar”的页面，还会出现一道限时挑战题。连续攻破六道题后，foo.bar邀请这位挑战者提交个人信息。后来，就有招聘人员来要简历了。

![](https://pic2.zhimg.com/v2-28e89de0363ac22ec486d8fe413b3217_b.jpg)

![](https://pic2.zhimg.com/80/v2-28e89de0363ac22ec486d8fe413b3217_hd.jpg)

这个foo.bar的地址如下:

[https://www.google.com/foobar/](https://link.zhihu.com/?target=https%3A//www.google.com/foobar/)

不过**莫激动**，没有得到Google的邀请这个网页还是没有办法注册的~

故事的最后给我们的启示，可能是多用Google搜索……

## **Google式“高考”**

关于Google面试这事，其热度和难度无异于产业内的“高考”，千军万马过独木桥的景象又出现了。

这其中有个想进Google工作“励志哥”John Washam火了，这位小哥大学时修经济学，韩国当兵退伍后去教授英语，但对于代码和Google的渴望没有磨灭，他励志专门腾出八个月的时间全职准备Google面试，实现自己的目标！

![](https://pic4.zhimg.com/v2-d71b4ac381ce18760edbb14b76c52b35_b.jpg)

![](https://pic4.zhimg.com/80/v2-d71b4ac381ce18760edbb14b76c52b35_hd.jpg)

“励志哥”John Washam

这是一场“苦行僧”式的修行，小哥曾三周攻读1000页的C++书，也在GitHub上收获了21000多个star，还做了1792张电子卡片方便复习……读书、写代码和听讲座的时间总共1000多个小时了。

![](https://pic3.zhimg.com/v2-8a6bd2a446304bb306102b55b555a2f9_b.jpg)

![](https://pic3.zhimg.com/80/v2-8a6bd2a446304bb306102b55b555a2f9_hd.jpg)

励志哥的夏季阅读书单，只是准备过程中很小一部分

八个月的刻苦准备后，小哥……还是落选了，甚至连电话面试都没有就被直接拒绝了。

但努力总会有回报，被拒后的小哥目前就职于亚马逊。

Google虽好，也不能贪杯哦。

— **完** —

欢迎大家关注我们的专栏：[量子位 \- 知乎专栏](https://zhuanlan.zhihu.com/qbitai)

诚挚招聘

量子位正在招募编辑/记者，工作地点在北京中关村。期待有才气、有热情的同学加入我们！相关细节，请在量子位公众号(QbitAI)对话界面，回复“招聘”两个字。

[量子位 QbitAI](https://zhuanlan.zhihu.com/qbitai) · 头条号签约作者

վ'ᴗ' ի 追踪AI技术和产品新动态

