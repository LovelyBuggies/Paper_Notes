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

- **功能**
  - **接口：**
    - 功能：记录当前档位控制器的状态：闲置或换挡
    - 使用者：driver 或者档位改变算法的专门组件（自动驾驶模式？）
  - **档位控制：**换挡五步
    - ![](https://ws2.sinaimg.cn/large/006tNbRwgy1fy1pth7ispj30uw0d4wgl.jpg)
- **环境**
  - 齿轮箱：
    - 100～300毫秒内设置档位；
    - 100～200毫秒释放档位；
    - 如果逾期完成，将会进入错误状态。
  - 离合器：功能和齿轮箱类似
    - 100～150毫秒开闭。
  - 引擎：三个控制模式
    - 正常转矩
    - 零转矩
    - 同步速度
- **要求**（如图）
  - 性能要求：时间限制
    - 正常情况下1s内换档
    - 所有情况1.5s内换档
  - 可预测性
    - 无死锁、活锁
    - 离合器在改变转矩情况下关闭
    - 改变引擎时，齿轮箱设置档位
  - 功能
  - 错误检测
  - ![](https://ws1.sinaimg.cn/large/006tNbRwly1fy3skqsai0j30uw0bcach.jpg)



#### Section 5

每个部分的正式设计



#### Section 6

把上面的要求总结成了十六个验证公式

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fy3snnehmjj31b80u0tfo.jpg)![](https://ws4.sinaimg.cn/large/006tNbRwgy1fy3snvcp26j31a008o75n.jpg)

#### Conclusion

吹水的