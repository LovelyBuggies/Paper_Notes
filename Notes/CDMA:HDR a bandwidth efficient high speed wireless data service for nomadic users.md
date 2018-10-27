## CDMA/HDR: a bandwidth efficient high speed wireless data service for nomadic users

### 概述

这个论文提出了一个由移动用户提供**非常高数据速率**的下游Internet访问的方法。通过**优化分组数据协议**以及**其他网络和编码技术**来**大幅度提高吞吐量**的方法。

### 关键点

- 无线数据传输速率目前还无法与有限网络的数据传输速率媲美，但这不是研究的重点。
- 推动无线数据传输服务的是移动用户快速、低延迟的互联网接入的需求。
- Section II **移动用户的特征和感知需求**；
- Section III **探索数据传输的速率和延迟需求特征**；
- Section IV **为这种需求定制的系统模型**。

#### Section II

- 满足移动用户的需求：
  - 不对称性：比起uplink，更高的downlink速率；
  - 没有太多延迟；
- 目标：
  - 满足移动用户需求
  - 在现有蜂窝基础设施中，最小化时间和花费
  - 仅通过在数字基带上不同于现有蜂窝和个人通信系统(PCS)的终端

#### Section III

- CDMA用来高效地进行uplink和downlink
- 一般认为uplink是瓶颈，但downlink才是：
  - Uplink 来自多个低功率发射机的累积干扰在统计上趋于稳定；
  - Downlink 受到少数其他大功率基站的干扰；
- 但是软切换虽然大大减少了干扰(干扰本身增加了容量)，但总体上还是减少了前向链路容量，因为必须在新增加的基站中分配额外的CDMA载波。
- 而在反向链路上，多用户的快速、准确的功率控制对于操作和容量实现显然是至关重要的，而在第一个CDMA标准的制作中，最初的感觉是正向链路的功率控制要慢得多。

#### Section IV

- 对三个原则进行了探讨：
  - Channel Measurement
  - Channel Control
  - Interference suppression and mitigation
- 不平等延时用来提升系统的吞吐量：
  - 根据信噪（SNR）水平分成N类；
  - 对于每一类数据传输速率为![](https://latex.codecogs.com/gif.latex?R_n)，频率为![](https://latex.codecogs.com/gif.latex?P_n)：
  - 情况1:槽均匀分配，平均吞吐量![](https://latex.codecogs.com/gif.latex?R_{av}=\sum\limits_{n=1}^{N}P_nR_n)；
  - 情况2:想让大伙儿延迟差不多，每个用户被分配与它的速率成反比的槽数![](https://latex.codecogs.com/gif.latex?F_n=\frac{k}{R_n})，![](https://latex.codecogs.com/gif.latex?R_{av}^{'}=R_{av}=\frac{\sum\limits_{n=1}^{N}P_nR_nF_n}{\sum\limits_{n=1}^{N}P_nF_n})
  - 情况3:保证公平、保证吞吐量：![](https://ws2.sinaimg.cn/small/006tNbRwgy1fwmt2hfr02j30uy0a8q3u.jpg)


### 想法/问题

- 讲的不是很清楚啊，尤其是吞吐量的那部分。






