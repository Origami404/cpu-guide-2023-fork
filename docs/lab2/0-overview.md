## 1. 实验目的

&emsp;&emsp;（1）理解单周期CPU工作过程；

&emsp;&emsp;（2）理解指令存储器和数据存储器的哈佛结构存储；

&emsp;&emsp;（3）熟悉miniRV指令集；

&emsp;&emsp;（4）掌握单周期CPU设计与实现方法。



## 2. 实验内容

&emsp;&emsp;本实验要求同学们在Minisys开发板 (芯片型号：<font color = blue>**XC7A100TFGG484-1**</font>) 上实现支持miniRV-1指令集的单周期CPU。

&emsp;&emsp;要求所实现单周期CPU的时钟频率<u>不低于25MHz</u>。

&emsp;&emsp;miniRV指令集如表1-1所示。其中，黑色字体的24条指令必做，蓝色字体的13条选做。

<center>表1-1 miniRV指令概述</center>
<center><img src = "../assets/1-1.png" width = 550></center>

!!! info "关于miniLA :loudspeaker:"
    &emsp;&emsp;miniLA指令集如表1-1A所示。其中，黑色字体的25条指令必做，蓝色字体的13条选做。

    <center>表1-1A miniLA指令概述</center>
    <center><img src = "../assets/1-1A.png" width = 550></center>
