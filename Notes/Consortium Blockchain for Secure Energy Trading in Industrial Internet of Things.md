## Consortium Blockchain for Secure Energy Trading in Industrial Internet of Things


### 概述

这篇文章通过构建**Energy Blockchain区块链**，解决了工业物联网IIOT中点对点能源交易场景下的**安全性和隐私保护**问题；通过建立一个**基于信用的支付模式**和**基于Stackelberg模型的优化定价策略**，解决了交易确认延迟的问题。安全性分析表明文章的方法可以**安全**并**高效**地支持能源区块链中的交易。


### 关键点

- P2P能源交易的问题：
  - 在不受信和不透明的能源市场中，进行庞大的能源交易是不安全的（insecure）；
  - 有能源剩余的节点考虑到自己的隐私泄漏，可能不愿意提供能源；
  - P2P能源交易用于交易审计和确认的中介可能涉及到单点失误和隐私泄漏问题。
- 如何提升交易效率：制定信用制度，通过向信用银行贷款来进行交易。
- 每个能源节点对应一个账户，账户里有很多钱包。能源聚集器（Energy Aggregator）用于管理交易如交易双方的匹配，构成部分有：账户池（节点ID，节点共钥私钥证书，节点钱包们）、内存池和信用银行。
- 系统运作流程：先拿货，再给钱；钱不够，可借贷；隔几日，封区块；挖区块，能赚钱。
- 两种奖励：
  - proof-of-flow：奖励贡献最多的卖家；
  - proof-of-work：奖励挖矿者（挖矿者是EAGs，只有一少部分节点能当EAG，EAGs数量随交易规模扩大而增加）。
- 贷款运作流程：钱不够，申请贷；审核完，拿token；付token，买能源；买完后，重新签；若贷款，有利率；还不上，有惩罚；跑路了，必拉黑。
- SE平衡：关于贷款数额以及贷款利率上，文章用一些公式说明了关于租赁者和银行的SE平衡存在。求得SE平衡点的算法如图：

![SE iteration](https://i.postimg.cc/vZ7kgpNF/Consortium_Blockchain_for_Secure_Energy_Trading_in_Industrial_In.png)Stackelberg

  
### 想法/问题

- 可以作为挖矿者的“Authorized EAGs”是怎样Authorized的？
- 论文中只是阐述的模型的合法情况。若买卖双方有不遵守制度的行为怎么办——比如给货不给钱？
- 会不会有人为了刷销售量而抱团？
- 贷款时为什么要再建一个钱包，直接由贷款人提供一个钱包地址不就好了？
- 公共wallet和银行给的token的关系是什么？
- 贷款这个方面还是写的很详细的，情况考虑较为周到。
- 关于Stackelberg的公式推导比较难理解。
- 为什么对用户满意函数求关于贷款数额的偏导？对银行满意函数求关于贷款利率的偏导？（SE模型问题）



### 未来工作

- 看一下文章提到的P2P能源交易场景，对比出用区块链作为底层架构的好处，参考[Enabling Localized Peer-to-Peer Electricity Trading Among Plug-in Hybrid Electric Vehicles Using Consortium Blockchains](https://ieeexplore.ieee.org/document/7935397/?part=1)。
- 研究一下Stackelberg Model。
  
   


