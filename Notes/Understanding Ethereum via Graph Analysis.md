## Understanding Ethereum via Graph Analysis


### 概述

本文通过在货币交易、合同创建和调用过程中利用**图谱分析**，特征化了**以太坊的用户**和**智能合约**。



### 关键点

#### Introduction

- 用来特征化交易活动而**构建的图**：
  - money flow graph (**MFG**)
  - smart contract creation graph (**CCG**)
  - smart contract invocation graph (**CIG**)
- 贡献：
  - 第一个对以太坊用图分析的系统描述；
  - 以太坊的内在数据挖掘；
  - 解决以太坊的两个安全问题：攻击取证和异常检测
- EOA —— 外部拥有账户



#### Section V ——图构建

- 交易分布结果：![](https://ws1.sinaimg.cn/large/006tNbRwgy1fye5ifx5fmj30nw0e0jty.jpg)
- 得出的结论：
  1. 几乎所有的用户都在不频繁地转账，但是并不是通过智能合约；
  2. 创建智能合约的用户很少；
  3. 73%的用户不触发智能合约，81%的智能合约不会被触发。
- 图构建用到的**统计学方法**：
  - 全局聚类系数——衡量节点们的聚集程度；
  - Pearson系数——衡量入度和出度的关系；
  - 计算节点重要性用PageRank算法。
- ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fye6fojmekj30qc06m0u5.jpg)
- ![](https://ws2.sinaimg.cn/large/006tNbRwgy1fye6g3f4jaj31a606udik.jpg)
- ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fye6hohjeyj31da09cn0y.jpg)
- ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fye6i18csaj31c807gju3.jpg)



##### 图分析的应用

- **攻击取证**
  - ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fye6l7y254j30m60g2jsu.jpg)
- **异常检测**
  - ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fye6lr8zutj30mu0js77a.jpg)
  - ![](https://ws1.sinaimg.cn/large/006tNbRwgy1fye6n0iu9jj30xq0d0q4q.jpg)



### 想法/问题

- 更多内容，详见[我的博客/以太坊数据挖掘]



