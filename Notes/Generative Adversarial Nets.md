## Generative Adversarial Nets 

---

### 概述

**大名鼎鼎的 GAN 生成对抗网络。**



---


### 关键点

- ![](https://ws4.sinaimg.cn/large/006tNc79ly1g2ihka8rqkj30y00asadv.jpg)
- ![](https://ws1.sinaimg.cn/large/006tNc79ly1g2ihgq52b9j30s40dsq3y.jpg)
- ![](https://ws4.sinaimg.cn/large/006tNc79ly1g2ihkn2ahkj30z40mktdm.jpg)
- $$\arg \mathop{\min}_{G}\mathop{\max}_{D}V(D,G)=\mathbb{E}_{ \boldsymbol x\sim p_{data}(\boldsymbol x)} [\log D(\boldsymbol x)] + \mathbb{E}_{ \boldsymbol z\sim p_{ \boldsymbol z}(\boldsymbol z)} [\log {(1-D(G(\boldsymbol z)))}]$$
- 这个看论文好像效率不高，[看一下李宏毅的GAN](https://www.bilibili.com/video/av27418372)，系统讲解各种GAN。由浅入深，比较好理解。
- [GAN zoo](https://github.com/hindupuravinash/the-gan-zoo)
- 一个[好库 😼](https://github.com/eriklindernoren/PyTorch-GAN#gan)



---

