## Plasma: Scalable Autonomous Smart Contracts


### 概述

**Plasma** 作为一种**以太坊扩容方案**，对以太坊主链可扩展性的提高通过将大量交易和计算**下放**到侧链来实现。Plasma本质上是一系列运行在以太坊主链上的智能合约，只需处理少量来自侧链的请求，*海量的交易和计算都在侧链上完成*。不同于以太坊主链目前使用的POW共识算法，侧链将使用**POS**等TPS**更高的共识机制**。因此侧链提供了可扩展性，而主链保证了安全性和去中心化。



### 关键点

#### Plasma

- 
- 节点自身被激励去运行一个链；
- 每个人都可以创建一个自定义的Plasma链；
- Plasma是一系列的智能合约，允许在主链里有许多的区块链；
- 主链可以强制Plasma链中的状态。主链是全局计算的强制检查者，但也只计算和惩罚那些存在欺诈的行为。许多的Plasma的区块链可以并存，且有他们独自的商业逻辑和合约术语。在以太坊中，Plasma将会由EVM智能合约组成，并直接在以太坊上运行，但只会执行很小的几次，但可以在非Byzantine的情况下代表不可思议的大量计算和金融账本实体。



### 想法/问题

- 这个文章主要讲的就是分布式以太坊。

- 中文版：

  -  [Plasma白皮书（一）](http://me.tryblockchain.org/blockchain-ethereum-plasma-whitepaper.html)
  -  [Plasma白皮书（二）](http://me.tryblockchain.org/blockchain-ethereum-plasma-whitepaper-2.html)
  -  [Plasma白皮书（三）](http://me.tryblockchain.org/ethereum-blockchain-plasma-whitepaper3.html)
  -  [Plasma白皮书（四）](http://me.tryblockchain.org/blockchain-plasma-whitepaper-4.html)



### 未来工作

- plasma大名鼎鼎，以后要尝试深入了解一下。
  






