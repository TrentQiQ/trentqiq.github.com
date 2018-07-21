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

--- 
## [线性分类笔记（中）](https://zhuanlan.zhihu.com/p/20945670)

支持向量机，因其英文名为Support Vector Machine，故一般简称SVM，通俗来讲，它是一种二类分类模型，其基本模型定义为特征空间上的间隔最大的线性分类器，其学习策略便是间隔最大化，最终可转化为一个凸二次规划问题的求解。

### 多类支持向量机损失 Multiclass Support Vector Machine Loss

第i个数据中包含图像x<sub>i</sub>的像素和代表正确类别的标签y<sub>i</sub>。评分函数输入像素数据，然后通过公式f(x<sub>i</sub>,W)来计算不同分类类别的分值。这里我们将分值简写为s。比如，针对第j个类别的得分就是第j个元素：s<sub>j</sub>=f(x<sub>i</sub>,W)<sub>j</sub>。针对第i个数据的多类SVM的损失函数定义如下：
![image](https://www.zhihu.com/equation?tex=%5Cdisplaystyle+L_i%3D%5Csum_%7Bj%5Cnot%3Dy_i%7Dmax%280%2Cs_j-s_%7By_i%7D%2B%5CDelta%29)

可以看成s<sub>j</sub>+![image](https://www.zhihu.com/equation?tex=%5CDelta)-s<sub>y</sub><sub>i</sub>

SVM的损失函数想要正确分类类别y_i的分数比不正确类别分数高，而且至少要高![image](https://www.zhihu.com/equation?tex=%5CDelta)。如果不满足这点，就开始计算损失值。

![image](https://pic4.zhimg.com/80/f254bd8d072128f1088c8cc47c3dff58_hd.jpg)

多类SVM“想要”正确类别的分类分数比其他不正确分类类别的分数要高，而且至少高出![image](https://www.zhihu.com/equation?tex=%5CDelta)的边界值。如果其他分类分数进入了红色的区域，甚至更高，那么就开始计算损失。如果没有这些情况，损失值为0。我们的目标是找到一些权重，它们既能够让训练集中的数据样例满足这些限制，也能让总的损失值尽可能地低。

**正则化**

- L1正则化是指权值向量ww中各个元素的绝对值之和
- L2正则化是指权值向量w中各个元素的平方和然后再求平方根