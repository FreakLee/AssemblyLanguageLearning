## 寄存器

以下是ARM64架构中的一些常见寄存器：

1、**通用寄存器（General Purpose Registers）**： 31 个通用寄存器。每个寄存器可用作 64 位 X 寄存器 （X0..X30），或作为 32 位 W 寄存器 （W0..W30）

* x0-x7：x0到x7是通用寄存器，用于存储数据和计算结果。它们可以用于存储整数值、指针和地址。
* x8：间接结果位置寄存器。在函数调用期间，它保存返回地址。
* x9-x15：这些寄存器也是通用寄存器，用于存储数据和计算结果。
* x16-x30：这些寄存器也是通用寄存器，用于存储数据和计算结果。其中，x30寄存器也称为链接寄存器（Link Register）或LR。

2、**特殊寄存器（Special Registers）**：

* sp（或x31）：sp寄存器是栈指针寄存器（Stack Pointer Register），用于指向当前栈顶。它存储了栈中最新分配的内存地址。
* xZR（或x31）：xZR寄存器也称为零寄存器（Zero Register），始终包含值0。它在执行某些指令时可以用作常量零的来源。
* x31既可以用作栈指针寄存器（sp），也可以用作零寄存器（xzr）。这是ARM64架构的设计选择，为了简化指令编码和执行。

3、**程序计数器寄存器（Program Counter Register）**：

* pc（或ip）：pc寄存器是程序计数器寄存器，包含当前正在执行的指令的地址。它用于指示下一条要执行的指令的位置。

4、**状态寄存器（Status Registers）**：

* cpsr（或nzcv）：cpsr寄存器是当前程序状态寄存器（Current Program Status Register），用于存储条件码、中断状态和执行模式等信息。条件码（Condition Flags）用于存储最近一次算术或逻辑操作的结果。

5、**浮点寄存器（Floating Point Registers）**：

* v0-v31：v0到v31是浮点寄存器，用于存储浮点数和向量数据。每个寄存器的大小为128位，可以存储单精度浮点数、双精度浮点数和向量数据。

6、**系统寄存器（System Registers）**：

* 系统寄存器用于控制和配置处理器的特定功能，如异常处理、访存控制等。这些寄存器包括ELR（Exception Link Register）、SPSR（Saved Program Status Register）等。

这只是ARM64架构中的一些常见寄存器，还有其他特殊寄存器和系统寄存器，用于处理异常、访存控制等。具体使用和用途可以参考[ARM64的体系结构手册](https://developer.arm.com/documentation/102374/latest/)和编程指南。

## 指令

### 指令格式

ARM64 汇编指令的基本格式如下：

```
<opcode> {<cond>}{<flags>} <operand1>, <operand2>{, <operand3>}
```

其中，各部分的含义如下：

* \<opcode>：指令操作码，表示要执行的操作。例如，add、sub、mov等。
* {\<cond>}：条件码，用于指定执行指令的条件。例如，eq表示等于，ne表示不等于，gt表示大于等于，等等。条件码是可选的，如果省略，则表示指令将始终执行。
* {\<flags>}：标志位，用于指定指令的一些特殊行为或选项。例如，s表示更新条件码，w表示写回操作数等。标志位也是可选的，根据指令的需求进行设置。
* \<operand1>, \<operand2>, \<operand3>：操作数，表示指令要操作的寄存器、立即数或内存地址等。操作数的类型和数量取决于具体的指令。

### 指令类型

在ARM64汇编语言中，有多种指令类型，包括但不限于以下几种：

* 数据处理指令（Data Processing Instructions）：用于对数据进行算术、逻辑、位操作等处理的指令，例如加法、减法、与运算、或运算等。

* 分支指令（Branch Instructions）：用于控制程序流程跳转的指令，包括无条件分支、条件分支、函数调用等。

* 加载存储指令（Load/Store Instructions）：用于从内存加载数据到寄存器或将数据从寄存器存储到内存的指令，例如加载字（word）、加载双字（double word）、存储字等。

* 控制指令（Control Instructions）：用于控制程序执行流程的指令，例如设置程序状态寄存器（PSR）、异常处理等。

* 浮点指令（Floating-Point Instructions）：用于进行浮点数运算的指令，包括浮点加法、浮点乘法、浮点比较等。

* 向量指令（Vector Instructions）：用于进行向量操作的指令，支持同时对多个数据进行并行操作，提高运算效率。

除了上述指令类型，ARM64还具有一些特殊指令，如访问系统寄存器的指令、访问寄存器和内存的指令等。每种指令类型都有其特定的操作码和操作数格式，开发者可以根据需要选择适当的指令来编写ARM64汇编代码。

下面分类学习一些常见指令的用法。

## 数据处理指令

### MOV

MOV（Move）指令是数据处理指令（Data Processing Instructions）中的一种。它用于将数据从一个位置（如寄存器、内存等）移动到另一个位置，并可以进行一些基本的数据转换操作。MOV指令在汇编语言中常用于数据的加载、存储和传递。

在ARM64汇编语言中，MOV指令的基本语法为：
``` 
MOV destination, source
```

其中，destination表示目标操作数（通常是寄存器或内存位置），source表示源操作数（可以是立即数、寄存器或内存位置）。

MOV指令可以用于以下几种常见的操作：

1、将立即数（Immediate）加载到寄存器中：

```
MOV register, #immediate
```

2、将一个寄存器的值复制到另一个寄存器中：

```
MOV destination_register, source_register
```

3、将一个寄存器的值存储到内存中：

```
MOV [memory_location], register
```

4、将内存中的值加载到寄存器中：

```
MOV register, [memory_location]
```

比如：
```
;mov指令用法
;1、将立即数（Immediate）加载到寄存器中
mov x0, #0x2

;2、将一个寄存器的值复制到另一个寄存器中
mov x1, x0
```

通过断点调试，我们可以看到立即数2都加载到了寄存器x0和x1中。

```
(lldb) register read
General Purpose Registers:
        x0 = 0x0000000000000002
        x1 = 0x0000000000000002
        x2 = 0x0000000000000000
```

### ADD

在ARM64架构中，ADD（Addition）指令是一种算术指令（Arithmetic Instruction），用于执行加法操作。它可以用于将两个操作数相加并将结果存储在目标操作数中。ADD指令可以操作寄存器和立即数，并且支持多种寻址模式。

ADD指令的基本语法如下：

```
ADD destination, source1, source2
```

其中，destination表示目标操作数，source1和source2表示源操作数。ADD指令将source1和source2的值相加，并将结果存储在destination中。目标操作数可以是寄存器或内存位置。

以下是一些常见的ADD指令示例：

1、将两个寄存器的值相加并将结果存储到另一个寄存器中：

```
ADD x0, x1, x2
```

2、将一个寄存器和一个立即数相加并将结果存储到另一个寄存器中：

```
ADD x0, x1, #0x10
```

3、将一个寄存器的值与内存中的值相加并将结果存储到另一个寄存器中：

```
ADD x0, x1, [#0x1000]
```

首先，我们将上一篇的汇编函数 test() 声明稍微改一下，但是实现部分不做任何处理

```
int test(int a, int b)
```

然后在 main() 函数中调用一下这个函数：

``` c
int result0 = test(3,4);
int result1 = test(4,3);
printf("result0 = %d,result1 = %d",result0,result1);
//result0 = 3,result1 = 4
```
注释result0相关的代码，然后再看看寄存器里面的数据，x0存了4，x1存了3，返回的是x0。
```
General Purpose Registers:
        x0 = 0x0000000000000004
        x1 = 0x0000000000000003
```

可以猜想对于test()函数的实现部分，可以是如下样子：

``` 
add x0, x0, x1
```

此时，对于main()函数中的这段代码，如期输出了7：
``` c
//int result0 = test(3,4);
int result1 = test(4,3);
printf("result1 = %d",result1);
```




