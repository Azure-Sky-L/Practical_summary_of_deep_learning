#### 深度（机器）学习基础：

- 损失函数(loss function)：网络如何衡量在训练数据上的性能,即网络如何朝着正确的方向前进

+ 优化器(optimizer): 基于训练数据和损失函数来更新网络的机制

- SVM: 目标是通过在属于两个不同类别的两组数据点之间找到良好决策边界(decision boundary)来解决分类问题

    + SVM 通过两步来寻找决策边界:
    
         - 1.将数据映射到一个新的高维表示,这时决策边界可以用一个超平面来表示(如果数据是二维的,那么超平面就是一条直线)
         
         + 2.尽量让超平面与每个类别最近的数据点之间的距离最大化,从而计算出良好决策边界(分割超平面),这一步叫作间隔最大化(maximizing the margin)
    
* 决策树(decision tree): 是类似于流程图的结构,可以对输入数据点进行分类或根据给定输入来预测输出值

- 随机森林(random forest): 它引入了一种健壮且实用的决策树学习方法,即首先构建许多决策树,然后将它们的输出集成在一起

+ 深度学习从数据中进行学习时有两个基本特征:

    - 第一,通过渐进的、逐层的方式形成越来越复杂的表示

    + 第二,对中间这些渐进的表示共同进行学习,每一层的变化都需要同时考虑上下两层的需要
    
- 关于类和标签的说明：在机器学习中,分类问题中的某个类别叫作类(class)、数据点叫作样本(sample)、某个样本对应的类叫作标签(label)

#### 神经网络的数学基础

- 神经网络的核心组件是层(layer),它是一种数据处理模块,你可以将它看成数据过滤器，进去一些数据,出来的数据变得更加有用。大多数深度学习都是将简单的层链接起来,从而实现渐进式的数据蒸馏(data distillation)

+ 张量(tensor)：存储在多维 Numpy 数组中的数据，一般由三个关键属性来定义: 轴的个数（阶）、形状、数据类型

- 标量(scalar): 仅包含一个数字的张量

+ 向量(vector): 数字组成的数组，也叫一维张量

- 矩阵(matrix)：向量组成的数组

+ 转置(transposition)：对矩阵做转置是指将行和列互换

+ 广播包含以下两步：
    
    - 向较小的张量添加轴(叫作广播轴),使其 ndim 与较大的张量相同
    
    + 将较小的张量沿着新轴重复,使其形状与较大的张量相同
    
- 反向传播(backpropagation)：将链式法则应用于神经网络梯度值的计算（有时也叫反式微分,reverse-mode differentiation)

#### 神经网络入门

+ 训练神经网络主要围绕四个方面: 层、输入数据、损失函数、优化器

- 典型的 Keras 工作流程：
    
    + 定义训练数据:输入张量和目标张量
    
    - 定义层组成的网络(或模型),将输入映射到目标
    
    + 配置学习过程:选择损失函数、优化器和需要监控的指标
    
    - 调用模型的 fit 方法在训练数据上进行迭代
 
+ 为什么要使用激活函数? 如果没有 relu 等激活函数(也叫非线性), Dense 层将只包含两个线性运算——点积和加法

* logitic 不是回归是分类

- [K 折交叉验证](./K-折交叉验证.py)：这种方法将可用数据划分为 K 个分区(K 通常取 4 或 5),实例化 K 个相同的模型,将每个模型在 K - 1 个分区上训练,并在剩下的一个分区上进行评估,模型的验证分数等于 K 个验证分数的平均值

#### 机器学习基础

+ 分类和回归术语表：
    
    - 样本(sample)或输入(input): 进入模型的数据点
    
    + 预测(prediction)或输出(output): 从模型出来的结果
    
    - 目标(target): 真实值，对于外部数据源,理想情况下,模型应该能够预测出目标
    
    + 预测误差(prediction error)或损失值(loss value): 模型预测与目标之间的距离
    
    - 类别(class): 分类问题中供选择的一组标签，例如,对猫狗图像进行分类时,“狗”和“猫”就是两个类别
    
    + 标签(label): 分类问题中类别标注的具体例子

    - 真值(ground-truth)或标注(annotation): 数据集的所有目标,通常由人工收集。
    
    + 二分类(binary classification): 一种分类任务,每个输入样本都应被划分到两个互斥的类别中
    
    - 多分类(multiclass classification): 一种分类任务,每个输入样本都应被划分到两个以上的类别中,比如手写数字分类
    
    + 多标签分类(multilabel classification): 一种分类任务,每个输入样本都可以分配多个标签。举个例子,如果一幅图像里可能既有猫又有狗,那么应该同时标注“猫”标签和“狗”标签，每幅图像的标签个数通常是可变的

    - 标量回归(scalar regression): 目标是连续标量值的任务，预测房价就是一个很好的例子,不同的目标价格形成一个连续的空间
    
    + 向量回归(vector regression): 目标是一组连续值(比如一个连续向量)的任务，如果对多个值(比如图像边界框的坐标)进行回归,那就是向量回归

    - 小批量(mini-batch)或批量(batch):模型同时处理的一小部分样本(样本数通常为 8~128)，样本数通常取 2 的幂,这样便于 GPU 上的内存分配

+ 监督学习(supervised learning)：给定一组样本(通常由人工标注),它可以学会将输入数据映射到已知目标

- 无监督学习：是指在没有目标的情况下寻找输入数据的有趣变换,其目的在于数据可视化、数据压缩、数据去噪或更好地理解数据中的相关性

+ 自监督学习：没有人工标注的标签的监督学习

- 自编码器(autoencoder)：是有名的自监督学习的例子

- 降维(dimensionality reduction)和聚类(clustering)都是众所周知的无监督学习方法

+ 三种经典的评估方法:简单的留出验证、K 折验证,以及带有打乱数据的重复 K 折验证

- 数据预处理的目的是使原始数据更适于用神经网络处理,包括向量化、标准化、处理缺失值和特征提取

+ 防止神经网络过拟合的常用方法包括: 获取更多的训练数据、减小网络容量、添加权重正则化、添加 dropout

- L1 正则化(L1 regularization): 添加的成本与权重系数的绝对值[权重的 L1 范数(norm)]成正比

+ L2 正则化(L2 regularization): 添加的成本与权重系数的平方(权重的 L2 范数)成正比，神经网络的 L2 正则化也叫权重衰减(weight decay)

- 防止神经网络过拟合的常用方法包括:
  
  - 获取更多的训练数据
  + 减小网络容量
  - 添加权重正则化
  + 添加 dropout

-  ![为模型选择正确的最后一层激活和损失函数](./webwxgetmsgimg.jpeg)

+ 使用预训练网络有两种方法:特征提取(feature extraction)和微调模型(fine-tuning) 

- 冻结(freeze)一个或多个层是指在训练过程中保持其权重不变。(如果不这么做,那么卷积基之前学到的表示将会在训练过程中被修改。因为其上添加的 Dense 层是随机初始化的,所以非常大的权重更新将会在网络中传播,对之前学到的表示造成很大破坏)
