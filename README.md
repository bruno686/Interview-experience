# Interview-experience
> Interview experience and reflection of questions from major companies.
>

BodenAI   	嵌入式视觉算法工程师  					2021.6.16-2pm（✔）

Qihoo360 	NLP算法工程师 								 2021.6.17-3pm

ByteDance   广告推荐算法工程师  						2021.6.21-2pm

Dewu 		   搜索推荐运营 									2021.6.22-11.30am

Xiaomi 		 算法工程师 										2021.6.23-7pm



### 面试题

#### **1.layer normlization 与 batch normlization区别**

**①为什么我们需要normlization？**

- 将分散的数据统一，具有统一规格的数据更能让神经网络学习到规律。
- 就像是在tanh函数中，如果x的值为2，和x的值为100，明明这两个数差距很大，但是经过激活函数后，他们的值都接近于1，区分度不高。

**②normlization有哪些形式，每种形式计算思路是什么？**

Layer 和 batch normalization layer 的输入 minibatch 里的 ![[公式]](https://www.zhihu.com/equation?tex=m) 个tensors 记为 ![[公式]](https://www.zhihu.com/equation?tex=B%3D%5Cleft%5B%5Cbegin%7Bmatrix%7D+%5Cmathbf%7Bx%7D_1+%5C%5C+%5Cvdots+%5C%5C+%5Cmathbf%7Bx%7D_M+%5C%5C+%5Cend%7Bmatrix%7D%5Cright%5D) 。把每个tensor里元素个数记为 ![[公式]](https://www.zhihu.com/equation?tex=K) ，则这个 minibatch 可以展开成 ![[公式]](https://www.zhihu.com/equation?tex=B+%3D+%5Cleft%5B+%5Cbegin%7Bmatrix%7D+x_%7B1%2C1%7D+%26+%5Cldots+%26+x_%7B1%2CK%7D+%5C%5C+%5Cvdots+%26+%26+%5Cvdots+%5C%5C+x_%7BM%2C1%7D+%26+%5Cldots+%26+x_%7BM%2CK%7D+%5Cend%7Bmatrix%7D+%5Cright%5D) 。

Batch normalization 归一化（normalize）B 的每一列（column）。

Layer normalization 归一化（normalize）B 的每一行（row）。

- Batch Normalization 的处理对象是==一批样本==，Batch Normalization 是对这批样本的同一维度特征做归一化。BN应用在深度神经网络中最主要的作用是加速神经网络训练，并使模型训练更加稳定。

- Layer Normalization 的处理对象是==单个样本==， Layer Normalization 是对这单个样本的所有维度特征做归一化。LayerNorm这类归一化技术，目的就是让每一层的分布稳定下来，让后面的层可以在前面层的基础上安心学习知识。

[<img src="https://z3.ax1x.com/2021/06/20/RF3xg0.jpg" alt="RF3xg0.jpg" style="zoom:50%;" />](https://imgtu.com/i/RF3xg0)

[<img src="https://z3.ax1x.com/2021/06/20/RF8Ur8.jpg" alt="RF8Ur8.jpg" style="zoom:50%;" />](https://imgtu.com/i/RF8Ur8)

CNN中使用BN，对一个batch内的每个channel做标准化。**多个训练图像的同一个channel**，大概率来自相似的分布。(例如树的图，起始的3个channel是3个颜色通道，都会有相似的树形状和颜色深度)

RNN中使用BN，对一个batch内的每个position做标准化。**多个sequence的同一个position**，很难说来自相似的分布。(例如都是影评，但可以使用各种句式，同一个位置出现的词很难服从相似分布)

#### **2.自注意力机制**

Attention（注意力）机制如果浅层的理解，跟他的名字非常匹配。他的核心逻辑就是「**从关注全部到关注重点**」。

（1）**计算能力的限制**：当要记住很多“信息“，模型就要变得更复杂，然而目前计算能力依然是限制神经网络发展的瓶颈。

（2）**优化算法的限制**：LSTM只能在一定程度上缓解RNN中的长距离依赖问题，且信息“记忆”能力并不高。

同样，当我们读一句话时，大脑也会首先记住重要的词汇，这样就可以把注意力机制应用到自然语言处理任务中，于是人们就通过借助人脑处理信息过载的方式，提出了Attention机制。

自注意力机制是注意力机制的变体，其减少了对外部信息的依赖，更擅长捕捉数据或特征的内部相关性。自注意力机制在文本中的应用，主要是通过计算单词间的互相影响，来解决长距离依赖问题。

![img](https://pic1.zhimg.com/v2-69e4dd4fbf5d750aeb11bd63644453f0_b.jpg)

![img](https://pic1.zhimg.com/v2-b7f7ec8475c9355cbc3870f13be7c9e8_b.jpg)

#### 3.wide and deep

大部分用户的行为还是具有显然的，直接的，规律可循，wide必不可少。

但是购买行为受上下文影响很大，简单的购买规律下面也许藏匿着更为丰富的上下文原因

#### 4.深度学习正则化方法

1. 数据增强

   数据增强是提升算法性能、满足深度学习模型对大量数据的需求的重要工具。数据增强通过向训练数据添加转换或扰动来人工增加训练数据集。数据增强技术如水平或垂直翻转图像、裁剪、色彩变换、扩展和旋转通常应用在视觉表象和图像分类中。

2. L1和L2正则化

   L1 和 L2 正则化是最常用的正则化方法。L1 正则化向目标函数添加正则化项，以减少参数的绝对值总和；而 L2 正则化中，添加正则化项的目的在于减少参数平方的总和。根据之前的研究，L1 正则化中的很多参数向量是稀疏向量，因为很多模型导致参数趋近于 0，因此它常用于特征选择设置中。机器学习中最常用的正则化方法是对权重施加 L2 范数约束。

3. Dropout

   Dropout 指暂时丢弃一部分神经元及其连接。随机丢弃神经元可以防止过拟合，同时指数级、高效地连接不同网络架构。神经元被丢弃的概率为 1 − p，减少神经元之间的共适应。隐藏层通常以 0.5 的概率丢弃神经元。使用完整网络（每个节点的输出权重为 p）对所有 2^n 个 dropout 神经元的样本平均值进行近似计算。Dropout 显著降低了过拟合，同时通过避免在训练数据上的训练节点提高了算法的学习速度。

4. 早停法

   早停法可以限制模型最小化代价函数所需的训练迭代次数。早停法通常用于防止训练中过度表达的模型泛化性能差。如果迭代次数太少，算法容易欠拟合（方差较小，偏差较大），而迭代次数太多，算法容易过拟合（方差较大，偏差较小）。早停法通过确定迭代次数解决这个问题，不需要对特定值进行手动设置。