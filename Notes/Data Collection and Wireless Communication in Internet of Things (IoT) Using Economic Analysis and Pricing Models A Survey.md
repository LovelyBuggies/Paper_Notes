## Data Collection and Wireless Communication in Internet of Things (IoT) Using Economic Analysis and Pricing Models: A Surve


### 概述

本文综述了**经济模型和定价理论**在解决物联网系统中的**数据收集和通信问题**的应用。


### 关键点

#### Introduction

- 数据收集和通信的问题主要由以下部分组成（参照p.p.2图）：
  - 1. 数据交易和拓扑结构的形成；
  - 2. 资源和能源的分配；
  - 3. 传感器覆盖；
  - 4. 安全性；
  - 5. 相关问题和M2M交流问题。
- **这篇论文需要详细参考的部分：**
	- **Section2主要是介绍IOT服务的通用架构；**
	- **Section3主要是经济定价理论的基础；**

#### Section II —— IOT服务架构

- IOT的关键特性：感知能力、异构性、多寻址模式、高可靠性、自适应能力、安全环境。
- IOT架构如图：

![](https://i.postimg.cc/fy9nVQF1/Data_Collection_and_Wireless_Communication_in_Io_T_Using_Economic.png)

- IOT中可以通过定价理论优化的交易（p.p.3右下）

#### Section III —— IOT中定价理论简述

这个章节指引了我们如何给IOT系统中的资源进行定价，outline如下图，**有十分重要的参考价值**。

![](https://i.postimg.cc/Hnrv1HDJ/Data_Collection_and_Wireless_Communication_in_Io_T_Using_Economic.png)

##### 根据经济学概念进行定价

- 根据成本进行定价：p = C*(1+m)，C是成本，m是卖家期望得到的利润。
- 根据消费者认定的价值进行定价。影响因子：
  - Ve：消费者对商品经济学价值的评估；
  - Vp：消费者对商品效用的评估；
  - Vs：消费者对商家信用的评估；
  - Vm：消费者的消费动机；
  - Vc：消费者消费的消费背景。
- 根据供需平衡进行定价。找到一个供给需求量，使供需达到平衡点：
  - 需求曲线：数据需求量越多，卖家让利，每单位数据的价格越低；
  - 供给曲线：数据供给量越多，买家让利，每单位数据的价格越高；
- 智能数据定价模型（SDP）适用于需求高峰的情况，目标是让减轻网络负荷，让买家在不拥堵的时间段购买资源。具体体现在：数据的价格随时间改变；数据的价格随使用率改变。
- 选项定价：**Black-Scholes期权定价模型。**

##### 根据优化的定价理论

- 博弈论定价：
	- 非合作博弈在IOT系统中的公式化以及Nash均衡。
	- Stackelberg博弈考虑了动态因素。经过证明，Stackelberg博弈中的领导者的回报不小于相应的Nash均衡点回报。
	- 还价博弈。
- 拍卖算法：
	- 密封式拍卖：
		- kth密封式拍卖。
		- VCG拍卖。
	- 公开拍卖：
		- 提出型拍卖。
		- 反向拍卖。
		- 双边拍卖。
	- 组合拍卖。
	- 提价机制。
- 效用最大化。
- 背包问题。 


### 想法/问题

- 几种定价机制及关系要理清，结构在关键点的“Section III —— IOT中定价理论简述”部分。
- 拍卖算法中，是否封闭式需要搞清楚。


### 未来工作

- 双边拍卖算法及应用，可以重新看一下[Enabling Localized Peer-to-Peer Electricity Trading Among Plug-in Hybrid Electric Vehicles Using Consortium Blockchains](https://ieeexplore.ieee.org/document/7935397/?part=1) 这个论文。






