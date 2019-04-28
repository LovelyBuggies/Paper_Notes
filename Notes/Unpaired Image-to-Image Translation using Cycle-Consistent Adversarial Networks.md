## Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks 

---

### 概述

主要就是用 **Cycle-Consistent 融合 GAN** 的方法解决 **Image-to-Image** （风格迁移）问题。这个又叫 Cycle-GAN。



---


### 关键点

- ![模型架构](https://ws2.sinaimg.cn/large/006tNc79ly1g2ih1050onj30s80eu0uc.jpg)
- ![算法](https://ws2.sinaimg.cn/large/006tNc79ly1g2ih1pxv1sj30ys0gmwiv.jpg)
-  ![结果图](https://ws3.sinaimg.cn/large/006tNc79ly1g2ih6yn2epj31b40le13q.jpg)
- Adversarial losses:  $\mathcal{L}_{GAN}(G,D_y,X,Y)=\mathbb{E}_{ \boldsymbol y\sim p_{data}(\boldsymbol y)} [\log D_Y(\boldsymbol y)] + \mathbb{E}_{ \boldsymbol x\sim p_{data}(\boldsymbol x)} [\log {(1-D_Y(G(\boldsymbol x)))}]$
- Cycle Consistency losses:  $\mathcal{L}_{cyc}(G,F)=\mathbb{E}_{ \boldsymbol x\sim p_{data}(\boldsymbol x)} [\|F(G(\boldsymbol x))-\boldsymbol x\|_1] + \mathbb{E}_{ \boldsymbol y\sim p_{data}(\boldsymbol y)} [\|G(F(\boldsymbol y))-\boldsymbol y\|_1]$
- Final Objective: $\arg \mathop{\min}_{G,F}\mathop{\max}_{D_{X},D_{Y}}\mathcal{L}(G,F,D_X,D_Y)=\mathcal{L}_{GAN}(G,D_y,X,Y) 
  ​    +\mathcal{L}_{GAN}(G,D_X,Y,X)+\mathcal{L}_{cyc}(G,F)$

- 关于Cycle-GAN的其他资源：
  - [效果大全](https://junyanz.github.io/CycleGAN/)
  - [GitHub仓库](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix)
  - [GAN zoo](https://github.com/hindupuravinash/the-gan-zoo)
  - 一个[好库 😼](https://github.com/eriklindernoren/PyTorch-GAN#gan)

---

### 未来工作

- 这个论文的总结主要体现在我的课程项目报告 [Cycle-Consistent Adversarial Network picks up Monet’s Paintbrush](https://www.overleaf.com/read/ytwtvbszxzcv) 中。
- 从GAN 到Pix2Pix 到Cycle-GAN， 看看下一个里程碑是什么。



---




