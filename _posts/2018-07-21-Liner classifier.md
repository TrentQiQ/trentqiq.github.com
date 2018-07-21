---
layout:     post
title:      "线性分类笔记"
subtitle:   ""
date:       2018-07-21
author:     "QiQ"
header-img: "img/BingWallpaper-2018-07-21.jpg"
tags:
    - Liner classifier
    - Deep Learning
---

# 概念
---
### SIFT
SIFT（Scale-invariant feature transform）是一种检测局部特征的算法，该算法通过求一幅图中的特征点（interest points,or corner points）及其有关scale 和 orientation 的描述子得到特征并进行图像特征点匹配，获得了良好效果
### 过拟合 泛化

不知道大家在学车的时候教练教倒库和侧方停车的时候有没有教一串口诀：类似于在车窗的XX框切XX杆的时候打满，切XX的时候回正等等，这个口诀可以顺利让你通过科目二，然而换个车或者换个场地，你就发现并没有卵用... 我们说这只是overfit了某个车和某个场地（训练数据），在新的测试集（新车新场地）上的泛化性能为0。

![image](https://pic2.zhimg.com/80/afa034d52962681db09b4dc1060f8075_hd.png)

图像基础CS231a或CS131
机器学习基础CS229

## [线性分类笔记（上）](https://zhuanlan.zhihu.com/p/20918580)
### 线性分类器

![image](https://pic4.zhimg.com/80/7c204cd1010c0af1e7b50000bfff1d8e_hd.jpg)
一个将图像映射到分类分值的例子。为了便于可视化，假设图像只有4个像素（都是黑白像素，这里不考虑RGB通道），有3个分类（红色代表猫，绿色代表狗，蓝色代表船，注意，这里的红、绿和蓝3种颜色仅代表分类，和RGB通道没有关系）。首先将图像像素拉伸为一个列向量，与W进行矩阵乘，然后得到各个分类的分值

### 偏差和权重合并

![image](https://pic3.zhimg.com/80/3c69a5c87a43bfb07e2b59bfcbd2f149_hd.jpg)

分类评分函数定义为：

$$ \displaystyle f(x_i,W,b)=Wx_i+b $$
分开处理这两个参数（权重参数W和偏差参数b）有点笨拙，一般常用的方法是把两个参数放到同一个矩阵中，同时$x_i$向量就要增加一个维度，这个维度的数值是常量1，这就是默认的偏差维度。这样新的公式就简化成下面这样：

$$\displaystyle f(x_i,W)=Wx_i$$

---
## [线性分类笔记（中）](https://zhuanlan.zhihu.com/p/20945670)

支持向量机，因其英文名为Support Vector Machine，故一般简称SVM，通俗来讲，它是一种二类分类模型，其基本模型定义为特征空间上的间隔最大的线性分类器，其学习策略便是间隔最大化，最终可转化为一个凸二次规划问题的求解。

### 多类支持向量机损失 Multiclass Support Vector Machine Loss

第i个数据中包含图像x<sub>i</sub>的像素和代表正确类别的标签y<sub>i</sub>。评分函数输入像素数据，然后通过公式f(x<sub>i</sub>,W)来计算不同分类类别的分值。这里我们将分值简写为s。比如，针对第j个类别的得分就是第j个元素：s<sub>j</sub>=f(x<sub>i</sub>,W)<sub>j</sub>。针对第i个数据的多类SVM的损失函数定义如下：
$$\displaystyle L_i=\sum_{j\not=y_i}max(0,s_j-s_{y_i}+\Delta)$$


可以看成
$$s_j+\Delta-s_{y_i}$$

SVM的损失函数想要正确分类类别$y_i$的分数比不正确类别分数高，而且至少要高 $\Delta$ 。如果不满足这点，就开始计算损失值。

![image](https://pic4.zhimg.com/80/f254bd8d072128f1088c8cc47c3dff58_hd.jpg)

多类SVM“想要”正确类别的分类分数比其他不正确分类类别的分数要高，而且至少高出 $\Delta$ 的边界值。如果其他分类分数进入了红色的区域，甚至更高，那么就开始计算损失。如果没有这些情况，损失值为0。我们的目标是找到一些权重，它们既能够让训练集中的数据样例满足这些限制，也能让总的损失值尽可能地低。

**正则化**

- L1正则化是指权值向量ww中各个元素的绝对值之和
- L2正则化是指权值向量w中各个元素的平方和然后再求平方根


上面损失函数有一个问题。假设有一个数据集和一个权重集W能够正确地分类每个数据（即所有的边界都满足，对于所有的i都有 $L_{i} =0$ ）。问题在于这个W并不唯一：可能有很多相似的W都能正确地分类所有的数据。一个简单的例子：如果W能够正确分类所有数据，即对于每个数据，损失值都是0。那么当 $\lambda>1$时，任何数乘 $\lambda$W都能使得损失值为0，因为这个变化将所有分值的大小都均等地扩大了，所以它们之间的绝对差值也扩大了。举个例子，如果一个正确分类的分值和举例它最近的错误分类的分值的差距是15，对W乘以2将使得差距变成30。

换句话说，我们希望能向某些特定的权重W添加一些偏好，对其他权重则不添加，以此来消除模糊性。这一点是能够实现的，方法是向损失函数增加一个正则化惩罚（regularization penalty）R(W)部分。最常用的正则化惩罚是L2范式，L2范式通过对所有参数进行逐元素的平方惩罚来抑制大数值的权重：

$$ R(W)=\sum_k \sum_l W^2_{k,l}$$
上面的表达式中，将W中所有元素平方后求和。注意正则化函数不是数据的函数，仅基于权重。包含正则化惩罚后，就能够给出完整的多类SVM损失函数了，它由两个部分组成：数据损失（data loss），即所有样例的的平均损失$$L_i$$，以及正则化损失（regularization loss）。完整公式如下所示：

$$L=\displaystyle \underbrace{ \frac{1}{N}\sum_i L_i}_{data \  loss}+\underbrace{\lambda R(W)}_{regularization \ loss}$$
将其展开完整公式是：

$$L=\frac{1}{N}\sum_i\sum_{j\not=y_i}[max(0,f(x_i;W)_j-f(x_i;W)_{y_i}+\Delta)]+\lambda \sum_k \sum_l W^2_{k,l}$$
其中，N是训练集的数据量。现在正则化惩罚添加到了损失函数里面，并用超参数\lambda来计算其权重。该超参数无法简单确定，需要通过交叉验证来获取。
其中，N是训练集的数据量。现在正则化惩罚添加到了损失函数里面，并用超参数 $\lambda$ 来计算其权重。该超参数无法简单确定，需要通过交叉验证来获取。