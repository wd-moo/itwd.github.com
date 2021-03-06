---
layout: post
title: ch4-线性分类之判别模型
category: 机器学习
tags: [机器学习, PRML]
description: 概述一下线性分类相关的一些知识, 本文主要是判别函数法，包括LDA、感知器等方法
---

本篇主要是概述一下线性分类相关的一些知识。分类的目标是在给到一个D维的输入数据X，预测它的类别c（假设共K个类别，一般而言，各个类别是互斥的）。输入空间可以被分割为不同的决策区域(decision regions),这些区域的平面称之为决策边界(decision boundaries或decision surfaces，本文使用决策平面)。这一章，主要考虑线性分类器，即决策平面是输入x的线性模型。如果数据可以完全被线性决策平面分割，称之为线性可分（linearly separable）。笔记分三部分，这是第一部分：判别法部分。

<!-- more -->

注：本文仅属于个人学习记录而已！参考Chris Bishop所著[Pattern Recognition and Machine Learning(PRML)](http://research.microsoft.com/en-us/um/people/cmbishop/PRML/)以及由Elise Arnaud, Radu Horaud, Herve Jegou, Jakob Verbeek等人所组织的Reading Group。

###目录
{:.no_toc}

* 目录
{:toc}


###1.判别函数法
在PRML第一章，提到解决决策问题的三种方法：

- a).独立得到各个类别$$C_k$$下$$p(x \mid C_k)$$,之后使用贝叶斯法则得到$$p(C_k \mid x)$$。这种方法称之为生成模型(generative models)，因为根据$$p(x \mid C_k)$$，可以通过抽样生成输入空间中的数据点。
- b).直接得到$$p(C_k \mid x)$$，并根据决策理论得到x的类别。这种直接得到后验概率的方式称之为判别模型(discriminative models)。
- c).寻找一个函数f，称之为判别函数(discriminant function),能够直接把输入的x映射到类别。

这里先从判别(discriminant)函数的方法说起。先从二元分类说起，即K=2，类别只有两类$$t \in  \lbrace0,1 \rbrace$$。使用$$y(x) = w^Tx + w_0$$作为线性判别函数,其中$$w$$是权重向量(weight vector),$$w_0$$是偏差项（bias，也可以称之为截距项）。偏差取负后，也称之为阈值(threshold)。如果$$y(x)  \ge 0$$，则赋予x为类别$$C_1$$，反之为$$C_2$$。那么，决策平面就是$$y(x) = 0$$，是D维输入空间下的D-1为超平面。在决策平面上的点x，满足y(x)=0,即x与w是相互垂直的。

在多类别中，即K > 2的情况。这里需要注意t的表示，如果k=5，类别是2，那么t表示为$$(0,1,0,0,0)^T$$，有两种方式，如下图所示。第一种是one-versus-the-rest（下图左侧图），即我们可以把数据分成是否是$$C_1$$类，构建一个分类器，依次可以建立K-1个模型（如果都不是，就是最后一类）。另一种是one-versus-one（下图右侧图），即每两个类在一起，构建一个分类器，一共可以建立K(K-1)/2个分类器。注意这两种方法都导致了一些模糊区域（ambiguous regions，即可以是1类，也可以是2类），见下图的问号区域。

<img src="/images/prml/ch4_discriminant_k_class.jpg" height="100%" width="100%">

使用判别的方法可以避免出现以上模糊区域的问题，即判别函数由k个线性函数组成，$$y_k(x) = w_k^Tx + w_{k0}$$，如果对于所有不等于k的j，有$$y_k(x) > y_i(x)$$那么，类别为$$C_k$$。那么决策平面是$$y_k(x)=y_j(x)$$，这些超平面组合成最终的决策平面。这种判别得到的决策区域总是相互连接并且都是凸的（即区域内任意两点的连线仍然在该区域内）。

那么我们怎么得到这些权重呢？这里提供三种方法来求取这些权重值。分布是基于最小二乘法、Fisher线性判别和感知器(perceptron algorithm)

###2.最小二乘分类
类别$$C_k$$可以用$$y_k(x) = w_k^Tx+w_{k0}$$，为方便,这一节我们用$$y(x) = w^Tx$$，即这里的w是原始w和偏差项合并，x是原始x合并了1。回想一下回归里，目标T是多列，得到的$$W = (X^TX)^{-1}X^TX$$。这里我们直接拿过来就可以用。对于每个y，都会得到一个介于0到1之间的值，但是这些值并不代表概率值！毕竟他们的和不为1。这里注意t的表示，如果二元，也要表示成(1,0)种向量的形式！

最小二乘法的缺点就是对异常值非常敏感！这里不再细说。此外，最小二乘法用到了$$y_k - E(t \mid x)$$, 而这里的$$y_k$$只能是0或1，而$$E(t \mid x)$$应该表示是否是该类的概率值，直接使用$$WX$$来表示显得太粗糙（甚至可能得到大于1的结果）！之后会有一些拓展来解决这些问题！

###3.Fisher线性判别

####3.1 二元分类

我们可以用另一个视角来看分类，即把分类问题看成降维！首先还是考虑二元分类，输入D维度的x，降维得到一维的$$y = w^Tx$$，如果$$y \ge -w_0$$，那么类别为$$C_1$$，反之为$$C_2$$。那么我们怎么确定这个投影矩阵w呢？

最开始，我们先让投影后的类别之间分开最大。考虑二元分类，类别$$C_1$$中有$$N_1$$个观测值，均值为$$m_1 = \frac{1}{N_1} \sum_{n \in C_1} x_n$$，类别$$C_2$$中有$$N_2$$个观测值，均值为$$m_2 = \frac{1}{N_2} \sum_{n \in C_2} x_n$$。

一个简单的标准是使用投影后均值之间的差，来表示类别之间的分开大小。那么我们有：$$m'_2 - m'_1 = w^T(m_2 - m_1)$$ 这里，$$m'_k = w^Tm_k$$，表示投影后类别$$C_k$$的均值(注意：这里带一撇的表示投影后，不带的表示原始数据)。这个值可以通过放大w而增大，为此我们对w进行约束$$\mid \mid w \mid \mid = 1$$。通过拉格朗日乘子法，可以知道w是正比于$$m_2-m_1$$，即正比于原始数据均值的差。但是，这里存在一个问题，如下图所示：下图左侧图中类别间均值的差大于右侧图，但是左侧图的投影中重合的地方明显大于右侧图，即右侧图分类误差更小。

<img src="/images/prml/ch4_discriminant_fisher1.jpg" height="100%" width="100%">

我们看到重合是因为分布的方差较大导致的。Fisher提出了一个方法，即使得投影后不同类别的样本点越分开越好，同类的越聚集越好，也就是类间方差（这是个人翻译，不一定准，有人用“散度”）越大越好，类内方差越小越好，这种方法称之为Fisher线性判别法也称之为线性判别分析(LDA, Linear Discriminant Analysis)。我们知道投影后，类别$$C_k$$内的方差是 $$s_k^2 = \sum_{n \in C_k}(y_n - m'_k)^2$$，这里$$y_n = w^Tx_n$$，那么类内方差和为$$s_1^2 + s_2^2$$。Fisher准则(Fisher criterion)就是类间方差和类内方差的比值，即

$$J(w) = \frac{(m'_2 - m'_1)^2}{s_1^2 + s_2^2}$$

合起来就是：

$$J(w) = \frac{w^TS_Bw}{w^TS_Ww}$$，其中$$S_B$$表示between-class（类间）方差矩阵，即$$S_B = (m_2 - m_1)(m_2 - m_1)^T$$（注意有一撇和没有一撇的区别以及大小写的区别，多了投影矩阵w，可以自己代入化简得到）, $$S_W$$表示within-class（类内）方差矩阵，即$$S_W = \sum_{k=1}^2 \sum_{n \in C_k} (x_n - m_k)(x_n - m_k)^T$$。对J(w)取导数，可以得到：

$$\frac{2S_Bw}{w^TS_Ww} + \frac{(w^TS_Bw)(2S_Ww)}{(w^TS_Ww)(w^TS_Ww)} = 0$$

最后得到：$$(w^TS_Ww)S_Bw = (w^TS_Bw)S_Ww$$。从$$S_B$$的定义里可以看出$$S_Bw$$总是正比于$$m_2 - m_1$$，而且我们不关心w值得大小，只关心w的方向（最终的结果也只是看方向），那么对刚才求导取0得到的式子，我们可以舍弃因子项$$w^TS_Ww$$和$$w^TS_Bw$$，然后都乘以$$S_W^{-1}$$得到：$$w \propto S_W^{-1}(m_2 - m_1)$$。这个式子(把正比换成等于号，不影响结果)就是Fisher线性判别公式(Fisher’s linear discriminant)。严格意义上说，它并不是一个判别函数，只是选择了一个数据投影到一维空间的方向而已。但是，我们可以引入阈值$$y_0$$，使得$$y(x) \ge y_0$$时，类别为$$C_1$$，反之为$$C_2$$。

这里扩展一下，就是对于J(w),如果我们限制分母为1，即$$\mid \mid w^TS_Ww \mid \mid =1$$，那么对于求导后的式子$$(w^TS_Bw)S_Ww = (w^TS_Ww)S_Bw = S_Bw$$，令$$\lambda = w^TS_Bw$$，两边乘以$$S_W^{-1}$$,则有$$S_W^{-1} S_Bw = \lambda w$$，即$$w$$是矩阵$$S_W^{-1}S_B$$的特征向量。（这里可以一开始就增加限制分母为1，之后用拉格朗日乘子法得到$$L(w) = w^TS_Bw - \lambda(w^TS_Ww - 1)$$，求解更容易,结论一样）

####3.2 与最小二乘的关系
最小二乘法的目标是使得预测的类别尽可能的接近目标值；而Fisher准则的目标是输出空间下的类别间尽可能的分开。接下来，可以看到：在二元分类下，Fisher可以看成是最小二乘的一个特例！

这里对于二元分类，我们不在使用t=(0,1)这种表达，而是采用如果是类别$$C_1, t = N/N_1$$，如果是类别$$C_2, t = -N/N_2$$，代入之后得到：

$$E = \frac{1}{2} \sum^N_{n=1}(w^Tx_n + w_0 - t_n)^2$$

对$$w,w_0$$分别求导之后，经过化简可以得到，$$w_0 = -w^Tm$$; $$m = \frac{1}{N} \sum_{n=1}^N x_n$$; $$(S_W + \frac{N_1N_2}{N}S_B)w = N(m_1 - m_2)$$，可以看出：$$w \propto S_W^{-1}(m_2 - m_1)$$

####3.3多元分类
现在考虑多元分类，即K > 2的情况，这里假设维度D > K，否则就没法降维了，降维后维度为D'，那么我们使用线性模型有$$y_k = w_k^Tx, k=1,...,D'$$。如果把这些y用一个向量表示，权重也用矩阵表示，那么有：$$y = W^Tx$$。注意这里依旧没有偏差项。那么这个时候的类内方差如下：

$$S_W = \sum^K_{k=1} S_k$$，其中，$$S_k = \sum_{n \in C_k}(x_n-m_k)(x_n-m_k)^T; \ \ m_k = \frac{1}{N_k} \sum_{n \in C_k} x_n$$。

类间方差是$$S_B = \sum^K_{k=1} N_k(m_k-m)(m_k-m)^T$$。

在投影后的D'空间里，$$s_w = \sum^K_{k=1} \sum_{n \in C_k}(y_n-\mu_k)(y_n-\mu_k)^T; \ \ s_B=\sum^K_{k=1}N_k(\mu_k-\mu)(\mu_k-\mu)^T$$, 其中$$\mu_k = \frac{1}{N_k} \sum_{n \in C_K}y_n; \ \ \mu_=\frac{1}{N} \sum^K_{k=1}N_k \mu_k$$。

我们的目标还是使得投影后不同类别的样本点越分开越好，同类的越聚集越好，也就是类间方差越大越好，类内方差越小越好。那Fisher准则可以表示为$$J(W) = Tr \lbrace s_W^{-1}s_B  \rbrace$$，之后化简得到:
$$J(w) = Tr  \lbrace (WS_WW^T)^{-1}(WS_BW^T) \rbrace$$，这个直接推导，或者采用拉格朗日乘子法都可以得到：权重w是$$S_W^{-1}S_B$$矩阵的前D'个特征值对应的特征向量！

关于Fisher准则，需要强调的一点是$$S_B$$是由K个矩阵相加得到的，每一个矩阵都是秩为1的两个向量叉乘得到的，里面用到了均值向量$$\mu$$可以由其他向量$$\mu_k$$线性组合得到，因此，$$S_B$$的秩最大值为K-1！即最多有K-1个不为0的特征值！也就是说，我们最终投影（降维）后的空间维度不超过K-1。此外，由于$$S_W^{-1}S_B$$不一定是对称阵，因此得到的K-1个特征向量不一定正交，这也是与PCA不同的地方。

###4.感知器
另一个线性判别模型是感知器(the perceptron algorithm),它用于二元分类，输入x经过了非线性变化得到输入特征$$\Phi(x)$$，感知器的模型表达如下：

$$y(x) = f(w^T \Phi(x))$$， 其中f是非线性激活函数(activation function)，如果$$a \ge 0, f(a) = +1 $$，如果$$a < 0, f(a) = -1$$。这里需要注意一点向量$$\Phi(x)$$包含偏差项$$\Phi_0(x)=1$$。这里二元分类里，t不再是0或1，而是1或-1。这个算法可以通过最小化误差函数来优化得到权重w。一个比较合适的误差函数是错误分类的样本总数，但是这个函数是w的分段常值函数，不连续，所以梯度基本都是0，故无法采用梯度下降法。

这里我们使用一个替代的误差函数，称之为感知器准则(perceptron criterion),考虑到$$t \in (1,-1)$$，那么所以正确分类的样本都满足$$w^T \Phi(x_n)t_n > 0$$，如果线性可分的话，那最终感知器准则会达到0,话句话就是说我们想要优化的对象等价如下：

$$E_P(w) = - \sum_{n \in M} w^T \Phi_n t_n$$, 这里M表示错误分类的样本。那么这个函数就是分段线性的，可以使用随机梯度下降法，结果如下：

$$w^{(\tau +1)} = w^{\tau} - \eta \nabla E_p(w) = w^{\tau} + \eta \Phi_n t_n$$

其中$$\eta$$是学习速率(learning rate)。注意这个训练是针对错误分类的样本进行的更新，如果是正确分类的话，则权重无需更新！

感知器由一个非常简单的解释：我们用感知器函数测试每一个训练函数，如果分类正确，就放过；如果分类错误，如果是1类，我们就在原权重向量上增加这个样本的$$\Phi_n$向量，如果是-1类，就减去。这种向量的加减，作用就是不断的改变权重w的方向（毕竟我们不关心w的大小，只关心它的方向）。我们也可以证明v这个更新会使得误差函数降低，即：

$$-w^{(\tau+1)T} \Phi_n t_n = -w^{(\tau)T}\Phi_n t_n - (\Phi_n t_n)^T \Phi_n t_n < -w^{(\tau)T}\Phi_n t_n$$

这里，我们假设$$\eta=1$$，使用了$$\mid \mid \Phi_n t_n \mid \mid ^2 > 0$$，但是这并不意味着错误分类数会减少！甚至可能因为这一次的权重更新，导致之前正确分类的样本被错误分类，因此感知器的学习算法并不能保证达到全局最小值。然而，感知器收敛定理(perceptron convergence theorem)表明：如果线性可分，那么感知器一定可以通过有限次数的迭代达到收敛！但是收敛过程中，我们不知道是收敛慢还是无法线性可分导致还未收敛的。如果线性不可分，那么一定不会收敛。即使收敛了，也会有不同的权重，这跟初始化权重、样本学习顺序等等都有关系。

除了难以训练之外，感知器也不能够产生概率化的结果。但它最大的限制是基于基函数的线性组合（也是之前讨论几个模型的限制！）。当然，还有其他的一些缺点导致感知器无法应用于复杂分类问题，这些都需要去阅读相关论文。然而，感知器也被发展过，比如适应机(adaline,adaptive linear element),它的模型形式和感知器一样，只是采用了不同的训练方式。

