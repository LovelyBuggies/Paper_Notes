## Formal Design and Analysis of a Gear Controller an Industrial Case Study using UPPAAL

### 概述

UPPAAL kit 的应用实例，实现一个档位控制器的正式建模。



### 关键点



#### Introduction

- Uppaal 作为档位控制器的检查工具，用来确保控制器在每个状态下都运行良好，满足特定要求。
- section 2：实时软件系统的语义和模型；
- section 3：定义了检查安全性和反应时间等特性的逻辑；
- section 4、5：档位控制系统和工作要求；
- section 6：section 3 的Uppaal实现；
- section 7：conclusion



#### Section2

- 时间转移系统（timed transition systems）和迹（timed traces）
- 自动机（automata）和数据变量（data variables）
- 自动机系统（automata system）



#### Section 3

- 语法和语义
- 定义了三个检查用的 automata

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fy1okk8nfnj30u00w10up.jpg)

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fy1ok6vb30j30ue0u0gob.jpg)

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fy1ol0e2u8j30u00udjvh.jpg)



#### Section 4

档位控制系统通过三个组件齿轮箱、离合器和引擎来变化档位。

**接口：**

- 功能：记录当前档位控制器的状态：闲置或换挡
- 使用者：driver 或者档位改变算法的专门组件（自动驾驶模式？）

**档位控制：**换挡五步

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fy1pth7ispj30uw0d4wgl.jpg)





### 想法/问题

- 







