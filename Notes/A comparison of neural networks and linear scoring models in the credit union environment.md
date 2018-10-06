## A comparison of neural networks and linear scoring models in the credit union environment 


### 概述

论文对比了在不同的信用合作社中，神经网路和传统方法的表现。


### 关键点

1. **Introduction**
	- 文章目标：尝试利用丰富的数据库，使用多层感知器（MLP）和模块化神经网络（MNN）两种神经网络，提升信用变量的预测能力。
	- NN方法作为一种非回归方法（non-regression），与其他的非回归方法相比，无需模型的预规范，NN会自己“学习”数据间的内在关系。
	- 信用合作社：
		- 困难：在信用合作社的环境中，独立的信用合作社受限于资金和小样本量，信用评分模型的定制常常被限制。（比如教师信用和保险推销员的信用——significant differences）
		- *于是乎，产生了分歧，对信用合作社都采用一个通用的（generic）模型，还是对每个模型“私人定制”？*
		- *通用模型虽然适用范围广，但肯定不如私人定制好啦...*
	- 当然，传统的技术无法与神经网络产生的精细分辨率相匹配。 
2. **Conventional Model**
	- LDA
		- 求两个输出类的总体均值向量（向量的元素分别是每个类在该特征的平均值）
		- 想办法加权平均向量之间的差异相对于它们的共同协方差最大化。
	- Logistic Regress
		- 对所有的信用参数加权
		- sigmoid（加权和）
3. **Neural Network**
	- 神经网络架构
		- MLP网络架构
		- MNN网络架构（应用于通用模型） 
	- 神经网络训练
		- MLP网络训练
		- MNN网络训练
	- 神经网络大小 
		- 前向选择特征
		- 反向剔除特征
4. **数据样本和模型构建**
	- 数据取样
		- 表一：有关信用的变量
	- 模型构建
	- 数值实验
5. **结果比较**
	- 结果衡量：
		- 每个信用合作社有很多数据集，数据集有坏账率。
		- 应用不同的模型定制方法可以得到相关的**总预测准确率**和**坏账预测准确率**。
			- 表二给出了定制模型的表现。
			- 表三给出了通用模型的表现。
	- 定制模型：
		- 总预测准确率：mlp_c > lr_c > lda_c
		- 坏账预测准确率：mlp_c > lr_c > lda_c
	- 通用模型：
		- 总预测准确率：lr_c > lda_c > mlp_g > mnn_g
		- 坏账预测准确率：mlp_g > lr_g > mnn_g > lda_g
	- 讨论
		- 定制模型的结果总是比通用模型好，说明信用社有着显著的不同。
		- 考虑到通用模型的个体信用社非均匀性，MNN就能发挥作用了。


### 想法/问题

- 个体信用社的差异与[Neural network credit scoring models](https://www.researchgate.net/profile/David_West6/publication/223425357_Neural_Network_Credit_Scoring_Models/links/5ae9c71c45851588dd826629/Neural-Network-Credit-Scoring-Models.pdf)中提到的（p.p.1145 Table 3）个体信用差异关系？
- NN好处：神经网络提供的一个特殊优势是，模型的预规范是不需要的。（**对比Logistic回归的坏处**）
- 结果比较表的理解十分重要。
- 对于个人研究，目前倾向于采用定制MLP，因为通用模型比较麻烦[Neural network credit scoring models](https://www.researchgate.net/profile/David_West6/publication/223425357_Neural_Network_Credit_Scoring_Models/links/5ae9c71c45851588dd826629/Neural-Network-Credit-Scoring-Models.pdf)。


### 未来工作

- 参考[Neural network credit scoring models](https://www.researchgate.net/profile/David_West6/publication/223425357_Neural_Network_Credit_Scoring_Models/links/5ae9c71c45851588dd826629/Neural-Network-Credit-Scoring-Models.pdf)通用模型，找出Logistic Regression坏处和superior model的定义。

   






