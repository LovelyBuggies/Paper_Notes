## Enabling Localized Peer-to-Peer Electricity Trading Among Plug-in Hybrid Electric Vehicles Using Consortium Blockchains


### 概述

这篇文章提出了一个**局部的点对点能源交易系统**（PETCON），来摆脱了**受信中介的单点失误和隐私泄漏问题**；同时利用**迭代双边拍卖算法**给能源定价和能源供给量，来**最大化社会福利**。实验表明以上方法能够提升安全性和隐私性保护，同时可以最大化社会福利。


### 关键点

- 用迭代双边拍卖算法对能源进行定价，使社会福利最大化。

![Double Auction](https://i.postimg.cc/m2h4wcRZ/Enabling_Localized_Peer-to-_Peer_Electricity_Trading_Among_Plug-i.png)


### 想法/问题

这个论文作为[Consortium Blockchain for Secure Energy Trading in Industrial Internet of Things](http://folk.uio.no/yanzhang/IEEETIIBlockchain2018.pdf)的前序，架构层基本上与它相同（除了贷款银行），不同之处在于这篇论文用双边拍卖的算法对市场中的数据进行了定价。

#### 区块链问题

- 为什么卖家PHEV要从LAGs内存池最后一个区块来验证交易？它又是怎么验证的？
- 交易过程中block chain的变化在文中比较含糊。比如：
  - 1. 买家给钱之后，卖家要检查一下LAG中的区块链确认收钱；
  - 2. 买家生成交易记录，卖家进行数字签名，上传至LAG进行审计，一段时间后被封装成块并经历LAGs共识阶段后放入内存；
  - 既然是审计之后构建区块，那么卖家检查的区块是什么？难道有两条链？
- 会不会存在“倒卖能源”赚取差价的问题？
- 因为是局部市场，会不会存在囤积能源抬价的问题？

#### 定价问题

（双边多对多拍卖——未完待续。。。）


### 未来工作

- 了解一下双边拍卖算法——Double Auction。
- 看一些常见的拍卖算法和适用的场景[参考p.p.8](https://ieeexplore.ieee.org/abstract/document/7496795/)
  
   






