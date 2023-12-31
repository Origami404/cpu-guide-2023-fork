&emsp;&emsp;数据通路包含了完成处理器所要求的操作所必须的硬件，但数据通路要在控制器的控制下才能有条不紊地工作，才能正确地运行程序并得出程序员想要的结果。

&emsp;&emsp;控制器的功能是根据指令的操作码 (`opcode`) 和功能码 (`funct3`、`funct7`)，产生指令执行所需的控制信号。控制信号一般包括功能选择信号、多路选择信号，如表5-1所示。

<center>表5-1 控制信号分类</center>
<center>

| 控制信号类别 | 作用 | 数据通路的相关部件 |
| :-: | :- | :- |
| 操作选择信号 | 执行某条指令时，选择部件需要完成哪个操作 | 多功能部件 (如NPC、SEXT、ALU、RF、DRAM等) |
| 多路选择信号 | 对多输入源进行选择 | 多路选择器 |

</center>

!!! info "补充说明 :book:"
    &emsp;&emsp;之所以把`RF`、`DRAM`等存储器看作多功能部件，是因为它们兼有读数据、写数据2个功能。从这个角度看，写使能信号的功能就是控制存储器需要完成读操作还是写操作。换言之，使能信号也属于一种操作选择信号。

&emsp;&emsp;为了设计控制器，我们首先需要确定数据通路需要哪些控制信号。

&emsp;&emsp;在上一节“数据通路设计”中，我们通过分析和综合，得出了整个CPU的数据通路。现在，让我们在表4-1的基础上进行扩展——在“综合”的下方新增“操作选择信号”、“多路选择信号”和“分支控制信号”三行；然后通过分析数据通路，得出每个功能部件所需的控制信号，并填入表中，如表5-2所示。

<center>表5-2 扩展数据通路表，添加控制信号</center>
<center><img src = "../assets/t5-2.png"></center>

&emsp;&emsp;接下来，只需要把控制单元和控制信号添加到数据通路图中，即可得到形如图5-1的完整数据通路图。

<center><img src = "../assets/5-1.png" width = 600></center>
<center>图5-1 完整数据通路图 (示例)</center>

&emsp;&emsp;确定了数据通路所需的控制信号之后，我们还需要确定控制信号的取值，进而得出每个控制信号的真值表。

&emsp;&emsp;根据完整的数据通路，结合数据通路表及指令功能，填写形如表5-3所示的控制信号取值表。

<center>表5-3 控制信号取值表 (示例)</center>
<center><img src = "../assets/t5-3.png" width = 600></center>

&emsp;&emsp;确定了各控制信号的取值之后，就可以使用卡诺图对每个控制信号的逻辑表达式进行化简，最终完成控制单元的设计。
