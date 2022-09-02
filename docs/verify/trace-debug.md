&emsp;&emsp;在CPU下板测试中，如果数码管显示卡在某一个功能点，没有继续计数，一种方法是可以采用Trace来进一步定位错误点。


!!! warning "注意 :loudspeaker:"
    &emsp;&emsp;**Trace测试时，DRAM地址不需要减去0x4000；下板测试时，DRAM地址才需要减去0x4000。**

    ``` Verilog
    1|    wire [31:0] waddr_tmp = waddr;// - 16'h4000;
    2|     
    3|    data_mem dmem (
    4|        .clk    (cpu_clk),
    5|        .a      (waddr_tmp[15:2]),
    6|        .spo    (rdata),
    7|        .we     (we),
    8|        .d      (wdata)
    9|    );
    ```

- ***Step1***：进入`cdp-test`目录，输入`make`命令以重新编译；

- ***Step2***：输入`make run TEST=start`以运行start测试。

&emsp;&emsp;例如，某次测试时报错，`debug_wb_pc`显示了`0x000018f8`，如下图所示。

<center><img src = "../assets/t-1.png" width = 400></center>

&emsp;&emsp;打开start.dump文件，找到PC值为`0x000018f8`的指令，即可定位到具体出错的指令，如下图所示。

<center><img src = "../assets/t-2.png" width = 650></center>

&emsp;&emsp;显然，在上述例子中，mycpu执行到auipc指令时出错。