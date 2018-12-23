## Plasma: Scalable Autonomous Smart Contracts


### 概述

**Plasma** 作为一种**以太坊扩容方案**，对以太坊主链可扩展性的提高通过将大量交易和计算**下放**到侧链来实现。Plasma本质上是一系列运行在以太坊主链上的智能合约，只需处理少量来自侧链的请求，*海量的交易和计算都在侧链上完成*。不同于以太坊主链目前使用的POW共识算法，侧链将使用**POS**等TPS**更高的共识机制**。因此侧链提供了可扩展性，而主链保证了安全性和去中心化。



### 关键点

#### Plasma

- Plasma **架构**：
  - ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fyfuvbvgzmj313i0dc0u8.jpg)
  - 节点自身被激励去运行一个链；
  - 每个节点都可以创建一个自定义的Plasma链；
  - Plasma是一系列的智能合约，允许在主链里有许多的区块链；
  - 主链可以强制Plasma链中的状态，是全局计算的强制检查者，计算和惩罚那些存在欺诈的行为；
  - 许多的Plasma的区块链可以并存，且有他们独自的商业逻辑和合约术语；
  - Plasma将会由EVM智能合约组成，并直接在以太坊上运行；
  - Plasma执行次数不多，却能代表大量计算得到的金融账本实体。
- **核心部分**：
  - **激励层**——用于持续以优化的价格执行合约，树形地组织子链来提高效率
  - **MapReduce框架**——构建一个状态转换的的欺诈证明
  - **共识机制**——尝试构建一个和比特币的共识激励类似的机制
  - **UTXO提交位图**——保证在主链下的确定的状态转换，同时尽可能降低退出费用，允许在数据不可用或者其它Byzantine行为时可以退出。
- **Externalized Multiparty Channels**
  - ![](https://ws2.sinaimg.cn/large/006tNbRwgy1fyfvae5ys0j318s0lutbt.jpg)
  - Alice 很倒霉，她所在地Plasma 区块被证明是invalid blocks了。区块的创建者受到惩罚了。



### 想法/问题

- 这个文章主要讲的就是分布式以太坊。

- 中文版：

  -  [Plasma白皮书（一）](http://me.tryblockchain.org/blockchain-ethereum-plasma-whitepaper.html)
  -  [Plasma白皮书（二）](http://me.tryblockchain.org/blockchain-ethereum-plasma-whitepaper-2.html)
  -  [Plasma白皮书（三）](http://me.tryblockchain.org/ethereum-blockchain-plasma-whitepaper3.html)
  -  [Plasma白皮书（四）](http://me.tryblockchain.org/blockchain-plasma-whitepaper-4.html)



### 未来工作

- plasma大名鼎鼎，以后要尝试深入了解一下。
  






