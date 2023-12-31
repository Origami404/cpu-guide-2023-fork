&emsp;&emsp;在上一节“功能部件设计”中，我们为数据通路的路径设计了所需的“顶点”。现在，我们需要根据指令功能，将这些功能部件连接起来，形成路径的“边”。

&emsp;&emsp;设计数据通路的基本思想是：根据每条指令的功能描述和指令格式，推演出指令执行过程所需的功能部件及其输入输出信号之间的连接关系，即指令级数据通路。

&emsp;&emsp;在推演的过程中，还将分析功能部件需要执行的具体功能，并据此再推演相应的控制信号取值。

&emsp;&emsp;本课程采用表格驱动设计的方法来构建数据通路，即通过数据通路表来描述数据通路。表4-1给出了6条miniRV指令构建数据通路表的示例。

<center>表4-1 表格驱动的数据通路设计示例</center>
<center><img src = "../assets/t4-1.png"></center>
**<font size = 0.8>注：表中的“X.Y”表示X部件的Y输出信号。</font>**

!!! hint "Tips :bulb:"
    &emsp;&emsp;需要注意的是，表4-1所示的数据通路表仅仅是一个示例。在建模过程中，可能会面临基本功能部件不满足需求的问题，因此需要修改并完善已有基础功能部件，或者设计新的功能部件。

&emsp;&emsp;对所有的指令进行分析，并将数据通路表填写完整后，就得到了每一条指令执行时的数据通路。为了设计CPU，我们还需要将所有指令的数据通路综合起来。

&emsp;&emsp;综合的方法是：在如表4-1所示的数据通路表的最后新增一行“综合”，代表CPU的整个数据通路；然后将各个部件的输入信号全部整合到最后一行。

&emsp;&emsp;在数据通路表中，有些功能部件的输入信号具有2个以上的输入源，如RF的wD端口有3个输入来源。我们已经学习过数字逻辑设计的课程，可知此时需要新增一个多路选择器来满足此需求。因此，在综合数据通路表时，需要视情况添加多路选择器 (或采用其他方式处理多输入源的问题，如添加输入端口等)，如图4-1所示。

<center><img src = "../assets/4-1.png" width = 500></center>
<center>图4-1 添加多路选择器，以解决多输入源的问题</center>

&emsp;&emsp;对于不同格式的立即数造成的多输入源问题，也可以使用上述方法进行综合和连接，但会造成线网资源的浪费，因此也可使用拓展输入信号位宽的方法，将指令码中可能是立即数的比特位全部输入到`SEXT`扩展部件当中。

&emsp;&emsp;最后，将综合完成的数据通路表图形化，即可构建出CPU的数据通路图。
