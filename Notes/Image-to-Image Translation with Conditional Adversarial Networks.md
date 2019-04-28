## Image-to-Image Translation with Conditional Adversarial Networks

---

### 概述

主要就是用 **Pix2Pix 融合 GAN** 的方法解决 **Image-to-Image** （风格迁移）问题。这个又叫 Cycle-GAN。



---


### 关键点

- ![](https://ws4.sinaimg.cn/large/006tNc79ly1g2ihqzk7fjj30z20pqwkc.jpg)
- $\mathcal{L}_c GAN(G,D)=\mathbb{E}_{x,y} [\log D(x,y)] + \mathbb{E}_{x,z} [\log {(1-D(x,G(x,z))}]$
- $\mathcal{L}_{L1}(G)=\mathbb{E}_{x,y,z} [\|\log {(y-G(x,z))}\|_1]$
- $\arg \mathop{\min}_{G}\mathop{\max}_{D}\mathcal{L}_c GAN(G,D)+\lambda \mathcal{L}_{L1}(G)$



---

### 未来工作

- 这个论文的总结主要体现在我的课程项目报告 [Cycle-Consistent Adversarial Network picks up Monet’s Paintbrush](https://www.overleaf.com/read/ytwtvbszxzcv) 中。
- 其实看了Cycle-GAN就觉得他有点鸡肋了
- 从GAN 到Pix2Pix 到Cycle-GAN， 看看下一个里程碑是什么。
- 一个[好库 😼](https://github.com/eriklindernoren/PyTorch-GAN#gan)

---




