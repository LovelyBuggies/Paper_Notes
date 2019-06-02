## The Road to Scalable Blockchain Designs

---

### 概述

本文介绍了区块链的性能问题，并概述了区块链on-chain（链上）性能提升的关键方法和可扩展区块链的设计模式。



---

### 区块链扩容

![](https://ws4.sinaimg.cn/large/006tNbRwly1fyhkwio9rzj30u00ejgnr.jpg)

由于区块链的固有缺陷，比特币系统已经变得越来越中心化，并且越来越低效。 为了解决这个问题，大量替代解决方案被提了出来。Off-chain（链外）解决方案允许小型和频繁的交易发生在与主链并行并由主链背书的侧链实例上。 On-chain（链上）解决方案直接修改区块链设计以支持高性能。 我们专注于后者，并总结和讨论近期On-chain（链上）性能提升方面的研究进展。

尽管建立在信息开放和自由的理想之上，互联网已经变得越来越中心化：只有少数大公司可以控制谁可以访问信息。 为了抵消这一趋势，一些建议被提出，以便信息存储和处理不集中在任何单一实体中。

一些人认为只将比特币区块链用作大额交易的结算网络——小规模交易由区块链之外的支付中心处理（off-chain scaling，链外扩展），而另一些人则主张增加区块链本身对所有交易类型的容量 （on-chain scaling，链上扩展）。 作为这一主张的附带结果，链上扩展（on-chain scaling）的支持者最近推出了比特币区块链的支链作为自己的网络，称为比特币现金。 在本文中，我们综述了区块链链上扩展（on-chain scaling）的关键主题和选项。

![Legends used in Models](https://ws1.sinaimg.cn/large/006tNbRwgy1fyhlg5piiuj30iq064q3g.jpg)



---

### 区块链性能

有两个测量指标与区块链扩展性直接相关：**交易吞吐量**（区块链可以处理交易的最大速率）和**延迟**（确认交易已包含在区块链中的时间）。吞吐量和延迟是提升区块链性能的瓶颈问题，从研究的角度也更具挑战性。比特币的交易吞吐量是其区块大小和块间间隔（时间）的函数。在当前块大小为1MB和10分钟块间间隔的情况下，最大吞吐量限制在每秒约7个交易；而创建交易的客户必须平均等待至少10分钟以确保交易包含在区块链中。相比之下，像 Visa 这样的主流支付处理公司可以在几秒钟内确认交易，并且每秒处理吞吐量高达24,000次。目前的研究集中在开发显著提高区块链性能的解决方案，同时保持其去中心化特性。对比特币区块大小和块间间隔的参数化可以在一定程度上提高性能：每秒27次交易吞吐量和12秒延迟。**性能的显著提升需要重新对区块链范型进行根本性的设计。**



---

### 比特币区块链

![Bitcoin Blockchian Model](https://ws2.sinaimg.cn/large/006tNbRwgy1fyhlf0nkbhj30bq09amxe.jpg)

比特币是一个P2P网络，任何节点都可以加入并成为网络的一部分。 如果一个节点收到一个新的区块，它会将其广播到网络的其余节点。 所有节点都可以接收和发送广播，但只有领导者节点才可以向区块链追加信息。为了阻止不诚实的领导者将系统带入泥潭， 这就会涉及到挖矿，这也是领导者节点被称为矿工的原因。 如果矿工幸运地找到哈希难题的答案，它会提出要追加到区块链下一个区块。为了激励矿工解决哈希难题并提出下一个区块，允许成功的矿工为自己支付一些金钱作为报酬或扣除交易输出的一部分作为交易费用。



---

### 区块链新设计

为提高区块链的扩展性开发了许多的重要的设计方案。 我们的研究范围仅限于链上解决方案，而不是将信任委托给侧链的技术。



#### 多区块单一领导

[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf) 分享了比特币的信任模型，将领导者选举与交易序列化解耦。[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)将时间划分为epoch，领导者节点可以在其epoch期间单方面向区块链追加多笔交易，直到新领导者节点被选出。 [Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)中有两种区块：密钥区块和微区块。 密钥区块包含一个难题答案，用于领导者选举。密钥区块还包含一个公钥，用于签署由领导者节点生成的后续微区块。每个区块都包含对前一个微区块和密钥区块的引用。费用会在当前领导者（40％）和下一个领导者（60％）之间分配。与比特币类似，通过增长（聚合所有密钥区块的）最长分支来解决分叉问题。

为了对微区块中创建分叉的领导者节点进行惩罚，后续的领导者节点可以在其关键块（包含被剪枝分叉中的第一个块的头部）之后插入特殊的有毒交易作为欺诈证据。这使恶意领导者节点的报酬无效，报酬的一小部分支付给告发领导者。当一位新领导者选出但前任领导者还没有收到，并继续产生微区块时，分叉也会出现。然而，一旦新领导者选举的宣布达到所有节点，这些分叉就会得到解决。

![Multi-blocks per Leader ](https://ws1.sinaimg.cn/large/006tNbRwly1fyhllo26ywj30c408s3yt.jpg)



#### 集体领导

该方案采用多个领导者共同快速决定是否应该将区块添加到区块链中。[ByzCoin](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_kokoris-kogias.pdf) 通过扩展[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)取代比特币的概率性交易一致性保证，以实现高交易吞吐量。好处在于，区块链仍然是无分叉的即使客户提交的交易将被添加到区块链中，因为所有领导者都立即就区块有效性达成一致。 [ByzCoin](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_kokoris-kogias.pdf)修改了[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)的密钥区块生成机制：一组领导者，而不是单个领导者，产生一个密钥区块，然后是微区块。领导者小组由近期时间窗口的矿工动态组成。每个矿工的投票能力与其在当前时间窗口的挖矿区块数量成正比，这是其哈希能力。当一位新矿工解决难题之后，它将成为现任领导小组的一员，更进一步，替换出最老的矿工。 [ByzCoin](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_kokoris-kogias.pdf)使用与比特币相同的激励模式，但报酬由领导者小组成员按其比例分摊。

![Collective leaders](https://ws2.sinaimg.cn/large/006tNbRwgy1fyhlprcyybj30cc09ot9a.jpg)

领导者小组被组织成一个消息通信树，其中最新的矿工（领导者）在树的根部。领导者运行一个具有线性消息传递复杂度的实用拜占庭容错协议的修改版本，以生成一个集体签名，证明至少三分之二的共识小组成员见证并验证了该微区块。网络中的节点可以以$O_{(1)}$时间复杂度验证该微区块已被共识小组验证为有效。这种设计解决了[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)的限制——恶意领导者节点可以创建微区块分叉：在 [ByzCoin](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_kokoris-kogias.pdf)中，这要求领导者小组成员的三分之二多数为恶意节点。此外，[Bitcoin-NG](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)遭受竞争条件困扰：一位尚未收到新领导者的老领导者节点可能会继续错误地在较早的微区块上进行挖矿。在 [ByzCoin](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_kokoris-kogias.pdf)中，领导者小组成员确保新领导者建立在最新的微区块之上。



#### 平行区块链增长

在这种方法中，多个领导者并行增长区块链的不同部分。比特币具有增长区块链的线性过程：矿工尝试解决难题，找到答案的矿工追加下一个区块。交易可以由多个子节点进行潜在的验证。此外，每次交易还会包含一笔报酬，这笔报酬由验证该交易的交易收取。随着更多的节点直接或间接地验证它，报酬值会降低，因此新节点有更多的动机来验证最新的交易。该系统已被证明是收敛的，这意味着在某一时刻有一个交易连接到之前的所有交易。作为这种图结构的结果，矿工可以并行地增长交易图的不同分支。系统中的正常（非矿工）节点在收到交易时验证它们。除了对交易及其双亲的工作量证明正确性和结构有效性进行标准检查之外，节点还验证该交易不是双花。

![Parallel Blockchain Extension](https://ws3.sinaimg.cn/large/006tNbRwgy1fyhltcu2b9j30jc0f2jsd.jpg)



#### 分片交易

[Elastico](https://www.comp.nus.edu.sg/~loiluu/papers/elastico.pdf)将节点分成称为“委员会”的组，每个委员会管理交易的一个子集（分片）。上部分片处理前10个交易，而下部分片处理后续10个交易。在委员会内，节点运行拜占庭一致性协议以协定交易区块。如果该区块已被足够的节点签名，委员会将其发送给最终委员会。最终委员会将从委员会收到的一系列交易整理到一个最终区块中，然后在其成员之间运行拜占庭一致协议以增长区块链，并将附加区块广播给其他委员会。系统按epoch运行：分配给委员会的节点仅在epoch期间内有效。在这个epoch结束时，这些节点解决当前最终委员会产生的随机字符串难题，并将求解答案发送给下一个最终委员会。因此，在每个epoch，一个节点与委员会中的不同节点搭档，管理一组不同的交易。委员会数量与系统中可用算力成线性比例关系，但一个委员会内的节点数量是固定的。因此，随着更多节点加入网络，交易吞吐量增加而延迟不会增加，因为这里有一个解耦：一致性协议所需的消息与添加到区块链的最终区块的计算和广播之间的解耦。

![Sharding transactions](https://ws1.sinaimg.cn/large/006tNbRwgy1fyhlw2yjx3j30jk0gsjt1.jpg)



---

