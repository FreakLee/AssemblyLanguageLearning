## 汇编简介

[汇编语言（Assembly Language）](https://zh.wikipedia.org/wiki/%E6%B1%87%E7%BC%96%E8%AF%AD%E8%A8%80)是任何一种用于电子计算机、微处理器、微控制器，或其他可编程器件的低级的计算机编程语言，它与计算机硬件的体系结构紧密相关。汇编语言使用符号和助记符来代表计算机指令和数据，这些符号和助记符更容易理解和记忆，相对于机器语言（二进制代码）来说更接近人类可读性。

编程语言大体上经历了机器语言、汇编语言和高级语言（C、C++、Java、Objective-C、Swift等）三个阶段，汇编语言介于机器语言跟高级语言之间。机器语言通过机器指令直接同计算机进行交互，而汇编语言的主体是汇编指令，汇编指令是机器指令的助记符，便于阅读与记忆。

### 汇编语言种类

常见的汇编语言种类包括：

* **x86汇编语言**：用于x86系列处理器的汇编语言，广泛用于个人计算机和服务器。包括Intel和AMD的x86处理器。

* **ARM汇编语言**：用于ARM架构处理器的汇编语言，广泛应用于移动设备、嵌入式系统和一些服务器。

* **MIPS汇编语言**：主要用于嵌入式系统和一些网络设备，如路由器和交换机。

* **PowerPC汇编语言**：用于IBM PowerPC架构处理器，曾在苹果的早期电脑和一些游戏机中使用。

对于移动开发者来说，接触到的更多是ARM汇编（iOS真机设备）和x86汇编（iOS模拟器）。本系列文章主要记录本人学习ARM64汇编语言的过程，也会顺便介绍跟x86汇编一些异同点。最初学习汇编语言还是学生时代，8086汇编跟51单片机。

### 汇编语言的特点
汇编语言具有以下特点：

* **低级别语言**：汇编语言是一种低级别语言，与高级语言相比，更接近底层的计算机硬件和指令集架构。它使用符号化的指令和寄存器来表示底层的操作和数据。

* **直接操作硬件**：汇编语言允许程序员直接操作计算机硬件，包括处理器、内存和设备等。它提供了对底层硬件的细粒度控制，可以执行特定的指令和操作。

* **与机器语言对应**：汇编语言的指令与机器语言指令一一对应。每条汇编指令都对应着底层的机器指令，可以直接在处理器中执行。因此，汇编语言是一种与硬件紧密相关的语言。

* **面向指令集架构**：汇编语言是与特定指令集架构（如x86、ARM等）相关的。不同的指令集架构具有不同的指令集和寄存器，因此编写的汇编语言程序需要适配特定的指令集架构。

* **直接访问内存**：汇编语言可以直接访问内存，包括读取和写入内存数据。程序员可以使用内存地址和偏移量等来操作内存中的数据，实现对变量和数据结构的访问。

* **与高级语言混合使用**：汇编语言常常与高级语言混合使用，以实现对性能关键部分的优化或底层硬件的访问。高级语言编写的程序可以通过嵌入汇编代码来调用底层的汇编指令和功能。

* **高度灵活和可优化**：由于直接操作硬件和底层指令集，汇编语言具有高度的灵活性和可优化性。程序员可以精确地控制程序的执行路径、内存访问和寄存器使用等，以获得更高的性能和效率。

* **可移植性较差**：由于汇编语言与特定的指令集架构相关，不同的架构需要使用不同的汇编语法和指令集。因此，汇编语言程序的可移植性较差，需要根据不同的架构进行适配和调整。

总的来说，汇编语言是一种低级别的、与硬件相关的语言，具有直接操作硬件、与机器语言对应、灵活性高等特点。它在性能优化、底层控制和特定硬件功能实现等方面发挥着重要作用，但可移植性较差，需要针对特定的指令集架构编写和优化代码。

### 汇编语言的作用

汇编语言在计算机科学和软件开发中发挥着重要的作用。以下是汇编语言的几个主要作用：

* **硬件控制**：汇编语言允许程序员直接控制计算机硬件，包括处理器、内存、设备等。通过编写汇编代码，可以实现对硬件的底层操作和控制，实现特定的功能和性能优化。

* **性能优化**：由于汇编语言直接操作底层硬件，能够更精确地控制程序的执行路径、内存访问和寄存器使用等。通过优化汇编代码，可以提高程序的运行效率和性能，尤其是对于对计算密集型任务或对响应时间敏感的应用程序。

* **嵌入式系统开发**：嵌入式系统通常运行在资源受限的环境中，对性能和资源的要求很高。汇编语言在嵌入式系统开发中得到广泛应用，可以精确地控制硬件、优化资源使用和实现实时操作。

* **逆向工程**：汇编语言在逆向工程中发挥重要作用。逆向工程是通过分析和理解已编译的程序来推断其功能和特性。通过查看程序的汇编代码，可以深入了解程序的内部结构、算法和逻辑。

* **操作系统开发**：操作系统是计算机系统的核心软件，负责管理硬件资源、提供服务和支持应用程序的运行。汇编语言在操作系统的内核开发中被广泛使用，以实现对硬件的底层访问和控制。

* **特定硬件功能实现**：一些特定的硬件功能需要直接的底层控制和操作。通过编写汇编代码，可以实现对特定硬件功能的访问和操作，如图形处理、信号处理、加密解密等。

尽管汇编语言在编写和调试方面相对复杂，但它提供了对计算机硬件的直接控制和高度的灵活性。在一些对性能要求高、或对底层硬件控制要求强的应用场景中，汇编语言是一种强大的工具，可以帮助开发者更好地利用底层硬件资源，并实现高效的程序设计和优化。

### 汇编风格
x86/amd64汇编指令的两大风格分别是Intel汇编与AT&T汇编。
<table>
<tbody><tr>
<th>项目</th>
<th>Intel风格</th>
<th>AT&amp;T风格
</th></tr>
<tr>
<td>操作数顺序</td>
<td>目标操作数在前</td>
<td>源操作数在前
</td></tr>
<tr>
<td>寄存器</td>
<td>原样</td>
<td>加%前缀
</td></tr>
<tr>
<td>立即数</td>
<td>原样</td>
<td>加$前缀
</td></tr>
<tr>
<td>16进制立即数</td>
<td>用后缀B与H分别表示二进制与十六进制<br />对于16进制字母开头的要加前缀0</td>
<td>加前缀0x
</td></tr>
<tr>
<td>访问内存长度的表示</td>
<td>前缀BYTE PTR, WORD PTR, DWORD PTR
<p>和QWORD PTR表示字节,字,双字和四字
</p>
</td>
<td>后缀b,w,l,q表示字节,字,双字和四字
</td></tr>
<tr>
<td>引用全局或静态变量var的值</td>
<td>[var]</td>
<td>var
</td></tr>
<tr>
<td>引用全局或静态变量var的地址</td>
<td>var</td>
<td>$var
</td></tr>
<tr>
<td>引用局部变量
</td>
<td colspan="2">需要基于栈指针（rsp）
</td></tr>
<tr>
<td>绝对寻址
</td>
<td>[imm]
</td>
<td>imm
</td></tr>
<tr>
<td>间接寻址</td>
<td>[reg]</td>
<td>(%reg)
</td></tr>
<tr>
<td>基址相对寻址</td>
<td>[reg +imm]</td>
<td>imm(%reg)
</td></tr>
<tr>
<td>变址寻址</td>
<td>[base+index]</td>
<td>(base,index)
</td></tr>
<tr>
<td>变址寻址
</td>
<td>[base+index+imm]
</td>
<td>imm(base,index)
</td></tr>
<tr>
<td rowspan="2">比例变址寻址</td>
<td>[base + index * scale + imm]</td>
<td>imm(base, index, scale)
</td></tr>
<tr>
<td colspan="2">scale只能是1,2,4,8其中的一个数字(1省略不写就是普通变址寻址)
</td></tr>
<tr>
<td>代码注释
</td>
<td colspan="2">单行注释用;+注释内容。例如:
<p>mov &#160; &#160;rax, rdx    ;这里是注释
</p>
</td></tr>
<tr>
<td>注意
</td>
<td colspan="2">这里imm为立即数,base和index为寄存器,scale为伸缩量
</td></tr></tbody></table>

## ARM64架构

[ARM架构](https://zh.wikipedia.org/wiki/ARM%E6%9E%B6%E6%A7%8B)，又称：高级精简指令集机器（Advanced RISC Machine，更早称作艾康精简指令集机器，Acorn RISC Machine），是一个[精简指令集](https://zh.wikipedia.org/wiki/%E7%B2%BE%E7%AE%80%E6%8C%87%E4%BB%A4%E9%9B%86%E8%AE%A1%E7%AE%97%E6%9C%BA)（Reduced Instruction Set Computer，简写RISC）处理器架构家族，其广泛地使用在许多嵌入式系统设计。

ARM64架构，也被称为ARMv8架构或ARM64位架构，是一种基于ARM处理器设计的64位指令集架构。它是ARM Holdings开发的第八代ARM架构，旨在提供更高的性能、更好的能效和更广泛的应用领域支持。

### 历史与发展

* ARM（Advanced RISC Machines）是一家英国公司，专注于低功耗、高性能的RISC（Reduced Instruction Set Computing）架构设计。
* ARM架构最早于1983年推出，经过多代演进和更新，逐渐发展成为广泛应用于移动设备、嵌入式系统和服务器等领域的指令集架构。
* ARM64架构是ARM架构的第八代版本，于2011年首次发布，并逐渐在市场上得到广泛采用。

### 64位指令集架构

* ARM64架构是一种64位指令集架构，与之前的32位ARM架构有很大的区别。
* 64位架构的主要优势在于可以处理更大的内存地址空间，支持更复杂的计算和数据操作。
* ARM64架构提供了更多的通用寄存器和SIMD（Single Instruction, Multiple Data）寄存器，从而提高了并行计算和数据处理能力。

### 寄存器和内存模型

* ARM64架构具有较大的寄存器集合，包括通用寄存器、浮点寄存器和SIMD寄存器，用于存储数据和执行指令。
* ARM64架构采用了统一的虚拟地址空间，支持虚拟内存管理和多级页表机制，以提供更灵活的内存管理和保护机制。
* ARM64架构支持小端字节顺序（Little Endian）和大端字节顺序（Big Endian），可以根据具体需求进行配置。

### 指令集和执行模型

* ARM64架构提供了一套丰富的指令集，包括数据处理指令、加载/存储指令、分支和跳转指令、协处理器指令等。
* ARM64架构引入了新的执行模型，如乱序执行（Out-of-Order Execution）、超标量执行（Superscalar Execution）和动态执行（Speculative Execution），以提高指令级并行和执行效率。
* ARM64架构还支持硬件虚拟化和信号处理扩展，为虚拟化和实时应用提供更好的支持。

### 应用领域和广泛采用：

* ARM64架构被广泛应用于移动设备领域，如智能手机、平板电脑和可穿戴设备等。
* 它还被广泛用于嵌入式系统、物联网（IoT）设备、网络设备和服务器等领域。
* ARM64架构的设计目标之一是提供更好的能效和低功耗特性，因此在便携设备和节能环境中得到了广泛应用。

总体而言，ARM64架构是一种先进的、高性能的64位指令集架构，具有广泛的应用领域和良好的能效特性。它在移动设备、嵌入式系统和服务器等领域的快速发展和广泛采用，对计算技术的发展和智能物联网的普及起到了重要的推动作用。ARM64架构的设计考虑了能效、性能和可扩展性等方面的需求，使其成为许多领域的首选架构。

### ARM相关术语

A64、ARM64和ARMv8是与ARM架构相关的术语，它们在某种程度上相关，但也有一些区别。下面是它们之间的区别与联系：

1、**ARMv8（ARM version 8）**：ARMv8是指ARM架构的第8个版本。它是一种64位的ARM架构，引入了新的指令集和体系结构特性，支持更大的内存寻址空间和更高的性能。ARMv8架构不仅包括了64位的ARM指令集（AArch64），还包括32位的ARM指令集（AArch32）。

2、**ARM64（也称为AArch64）**：ARM64是指ARMv8架构下的64位指令集。它是ARMv8架构中的一部分，用于支持64位应用程序和操作系统。ARM64提供了更大的寻址空间、更多的通用寄存器和更丰富的指令集，以提高性能和效率。

3、**A64**：A64是ARM64架构的一种指令集的简称。它是ARMv8架构中的64位指令集的具体实现，用于执行64位应用程序。A64指令集包含了一系列用于处理整数、浮点数、向量数据和系统级操作的指令。

联系：

* ARMv8是ARM架构的第8个版本，引入了64位的ARM指令集（AArch64）。
* ARM64是ARMv8架构下的64位指令集，用于支持64位应用程序和操作系统。
* A64是ARM64架构的一种指令集的简称，是ARMv8架构中的64位指令集的具体实现。

区别：

* ARMv8是整个架构的版本，包括了64位的ARM指令集（AArch64）和32位的ARM指令集（AArch32）。
* ARM64是ARMv8架构下的64位指令集，专门用于64位应用程序。
* A64是ARM64架构中的一种64位指令集的具体实现，是ARMv8架构中的一部分。

## 第一个汇编程序

### 将C程序或者OC程序转为汇编程序

首先，我们看看最经典的程序Hello World。在iOS中项目，编写一个hello.c文件：

``` c
//.h
#include <stdio.h>

void hello(void);

#endif /* hello_h */

//.c
#include "hello.h"

void hello(void) {
    printf("Hello World");
}
```

接着，使用gcc转换为汇编程序，打开终端进入上述C文件所在目录，输入如下命令：

```
gcc -S -arch arm64 -target arm64-apple-macos hello.c
```

或者使用clang：

```
clang -S -arch arm64 -o output.s hello.c
```

最后，我们看到生成的汇编程序：

``` s
	.section	__TEXT,__text,regular,pure_instructions
	.build_version macos, 12, 0	sdk_version 13, 1
	.globl	_hello                          ; -- Begin function hello
	.p2align	2
_hello:                                 ; @hello
	.cfi_startproc
; %bb.0:
	stp	x29, x30, [sp, #-16]!           ; 16-byte Folded Spill
	mov	x29, sp
	.cfi_def_cfa w29, 16
	.cfi_offset w30, -8
	.cfi_offset w29, -16
	adrp	x0, l_.str@PAGE
	add	x0, x0, l_.str@PAGEOFF
	bl	_printf
	ldp	x29, x30, [sp], #16             ; 16-byte Folded Reload
	ret
	.cfi_endproc
                                        ; -- End function
	.section	__TEXT,__cstring,cstring_literals
l_.str:                                 ; @.str
	.asciz	"Hello World"

.subsections_via_symbols
```

同样的，我们再新建一个ObjC类文件MyObject，里面也实现下Hello World。

``` Objc

//.h
@interface MyObject : NSObject

- (void)hello;

@end

//.m
#import "MyObject.h"

@implementation MyObject
- (void)hello {
    NSLog(@"Hello World");
}
@end
```

终端进入MyObject.m所在目录，输入如下命令：

``` 
clang -S -arch arm64 -o output.s MyObject.m
```

得到汇编程序部分代码如下：

``` s
	.section	__TEXT,__text,regular,pure_instructions
	.build_version ios, 16, 2	sdk_version 16, 2
	.p2align	2                               ; -- Begin function -[MyObject hello]
"-[MyObject hello]":                    ; @"\01-[MyObject hello]"
	.cfi_startproc
; %bb.0:
	sub	sp, sp, #32
	stp	x29, x30, [sp, #16]             ; 16-byte Folded Spill
	add	x29, sp, #16
	.cfi_def_cfa w29, 16
	.cfi_offset w30, -8
	.cfi_offset w29, -16
	str	x0, [sp, #8]
	str	x1, [sp]
	adrp	x0, l__unnamed_cfstring_@PAGE
	add	x0, x0, l__unnamed_cfstring_@PAGEOFF
	bl	_NSLog
	ldp	x29, x30, [sp, #16]             ; 16-byte Folded Reload
	add	sp, sp, #32
	ret
	.cfi_endproc
                                        ; -- End function
	.section	__TEXT,__cstring,cstring_literals
l_.str:                                 ; @.str
	.asciz	"Hello World"
```

最简单的方式，调试时直接显示反汇编，在Xocde工具栏中【Debug】->【Debug Workflow】->【Always Show Disassembyl】

``` s
AssemblyDemo`-[MyObject hello]:
    0x102e7a534 <+0>:  sub    sp, sp, #0x20
    0x102e7a538 <+4>:  stp    x29, x30, [sp, #0x10]
    0x102e7a53c <+8>:  add    x29, sp, #0x10
    0x102e7a540 <+12>: str    x0, [sp, #0x8]
    0x102e7a544 <+16>: str    x1, [sp]
    0x102e7a548 <+20>: adrp   x0, 2
    0x102e7a54c <+24>: add    x0, x0, #0x68             ; @"Hello World"
    0x102e7a550 <+28>: bl     0x102e7a800               ; symbol stub for: NSLog
->  0x102e7a554 <+32>: ldp    x29, x30, [sp, #0x10]
    0x102e7a558 <+36>: add    sp, sp, #0x20
    0x102e7a55c <+40>: ret    
```

对应的hello.c，通过这种方式得到的汇编程序如下：

``` s
AssemblyDemo`hello:
    0x100a0e528 <+0>:  stp    x29, x30, [sp, #-0x10]!
    0x100a0e52c <+4>:  mov    x29, sp
    0x100a0e530 <+8>:  adrp   x0, 0
    0x100a0e534 <+12>: add    x0, x0, #0xa20            ; "Hello World"
->  0x100a0e538 <+16>: bl     0x100a0e898               ; symbol stub for: printf
    0x100a0e53c <+20>: ldp    x29, x30, [sp], #0x10
    0x100a0e540 <+24>: ret    
```

以上，我们可以看到汇编程序有很多汇编指令，比如mov、add、ret、bl等；也看到很多寄存器，如x0、x1、x29、sp等；也看到一些伪指令，如.section、.p2align等；分号“;”后面为注释。汇编程序的要点就是利用这些汇编指令操作寄存器。一般的，汇编指令有三类：
* 汇编指令：机器码的助记符，有对应的机器码。
* 伪指令：没有对应的机器码，由编译器执行，计算机并不执行。
* 其它符号：如+、-、*、/等，由编译器识别，没有对应的机器码。

### 编写第一个汇编程序

有了上面的对汇编语言的初步认识，现在我们自己动手编写第一个简单的汇编程序。在上面这个iOS程序中，新建一个汇编文件myasm.s（.s表明是汇编文件，类似于.c表明是C文件），再创建个同名的头文件myasm.h，在头文件中声明一个函数test()。

``` s
//.h
#ifndef myasm_h
#define myasm_h

void test(void);

#endif /* myasm_h */


//.s
.text
.global _test

_test:

mov x0, #0x2

ret
```

在上述例子中，我们用汇编写了一个函数test，简要解释如下：
* **.text**：一个伪指令，用于定义代码段（或文本段），其中包含程序的实际机器代码。在汇编语言中，程序代码通常存储在代码段中。.text 指令告诉汇编器或链接器，接下来的指令是程序的实际代码，而不是数据或其他类型的信息。
* **.global**：也是一个伪指令，用于声明一个全局标识符，可以是函数、变量或标签。这些全局标识符可以被其他文件或模块引用，使它们在程序的不同部分之间可见。在这里说明_test是全局标识符（在Xcode中要加_，比较偏底层的代码，直接写test会报错：Undefined symbol: _test
）
* **mov x0, #0x2**：将立即数0x2（十六进制表示的整数2）加载到寄存器x0中。这个指令的含义是将2存储在x0寄存器中，覆盖掉原来的值（如果有的话）。在ARM64汇编中，x0是一个通用寄存器，可以用于存储数据。#0x2 表示立即数（immediate），即一个常数值。这个指令的效果是将2存储在 x0 中，以便在程序的后续部分使用。
* **ret**：return的简写，通常用于函数的返回。

在main函数中导入头文件，并调用test()函数，利用LLDB进行断点调试后可以看到，立即数"2"成功存储在了寄存器x0中。

```
(lldb) si 
(lldb) register read x0
      x0 = 0x0000000000000000
(lldb) ni
(lldb) register read x0
      x0 = 0x0000000000000002
(lldb) 
```

## 小结

这节我们主要了解了汇编语言、ARM架构以及第一个最简单的汇编程序。后续我们将逐步学习汇编语言中的常见寄存器、汇编指令等。



