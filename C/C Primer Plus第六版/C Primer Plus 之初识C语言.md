# C Primer Plus 之初识C语言

## 1. 计算机的组成

![image-20201104225211624](https://raw.githubusercontent.com/inconspicuousy-start/image/master/image-20201104225211624.png)

- `CPU` 负责处理程序，承担绝大部分的运算工作。
- `RAM` 随机访问内存（Random Access Memory）是存储程序和文件的工作区。
- `永久内存存储设备` 存储程序和文件，通常指机械键盘、固态硬盘。

## 2. CPU工作原理

![image-20201105003902200](https://raw.githubusercontent.com/inconspicuousy-start/image/master/image-20201105003902200.png)

- 程序加载到内存中，形成一个一个待执行的指令。
- CPU从内存中获取并执行一条指令，然后再从内存中获取并执行下一条指令。
- CPU是通过内部的寄存器存储的指令对应的内存的地址来处理指令的。

### 2.1 指令集

> 指令集指的是CPU能够理解并执行的指令的集合。

## 3. 计算机的工作原理

> 计算机只能明白机器语言，所以存储在计算机中所有的内容都是机器语言，机器语言也就是二进制数字，其中包括CPU执行的指令也是。

## 4. 高级编程语言的执行流程

> 因为计算机只能识别机器二进制指令，所以高级编程语言（如C）都必须经过 `编译器`将原语言编译成计算机能识别的语言。这样只有将原语言转化成计算机能识别的语言，程序才能被执行。

### 4.1 编译器的作用

- 将高级语言转化成机器语言。
- 可以根据不同的CPU，将高级语言转化成当前CPU能识别的指令集对应的机器语言。

有了编译器，高级语言才能真正实现被计算机识别并执行。

## 5. 使用C语言的七个步骤

> C 语言是编译型语言，需要经过编译器将代码编译成计算机可执行的二进制指令程序，所以使用 C 语言大概可以分为七个步骤：
>
> - `定义程序的目标`：确定程序想要实现的功能，达到的目的。
> - `设计程序`：设计实现功能的思路，比如设计流程图等。
> - `编写代码`：根据设计思路用代码实现。
> - `编译`：将代码编译成计算机可执行的程序，编译器一般都自带代码检查功能， 一旦代码出错，就会编译失败。
> - `运行程序`： 运行经过编译后的可执行程序。
> - `测试和调试程序`： 测试和调试程序，查看代码是否实现了预期的功能。
> - `维护和修改代码`：后期发现代码有哪些优化的地方可进行优化，或者对某些功能进行扩展等。

## 6. C语言的执行策略

### 6.1 图解执行策略

![image-20201105120402352](https://raw.githubusercontent.com/inconspicuousy-start/image/master/image-20201105120402352.png)

> 1、编译器负责将.c结尾的源代码转化为.obj结尾的目标代码。目标代码文件一般是以obj结尾，也可能是其他扩展名，有些编译器生成带 `.asm` 扩展名的汇编语言文件，而有些编译器则使用自己特有的格式。
>
> 2、通常情况下目标代码虽然为机器代码，但是还不能被执行，需要通过链接器将针对当前系统的启动代码和库文件代码结合起来形成当前系统的可执行文件（Windows下就是exe结尾的可执行文件）。

简单来说，目标文件和可执行文件都由机器语言指令组成的。然而，目标文件中只包含编译器为你编写的代码翻译的机器语言代码，可执行文件中还包含编写的程序中使用的库函数和启动代码的机器代码。

### 6.2 C语言的模块化

C语言采用 `分而治之` 的方法对程序进行模块化。

C语言可以独立 `编译` 单独的模块，最后再用 `链接器` 合并预编译的模块。通过这种方式，如果只更改某个模块，不必重新编译其他模块。

一般情况下， 单独的模块会在代码中声明自己要合并的其他模块，这样链接器才会去合并对应的模块。

> 注意：
>
> 不同系统中，编译程序和链接程序是有区别的。
>
> 有些系统，必须分别运行编译程序和链接程序；有些系统，编译器会自动启动链接器，用户只需给出编译命令即可。

## 7 C语言标准

当前C语言的标准大致有三个。

- `C90` ：1990年提出。
- `C99`： 1994年提出（对C90增添部分新特性）
- `C11`： 2011年提出（在C90的基础上增添新特性，选择性的支持C99的部分新特性）。

> 注意：
>
> 如果看到标准为 `C1X`则表示的是 `C11`之前的草案标准。

## 7. 不同系统的编译程序

> C语言代码的执行离不开编译器，所以想要在系统上执行C代码，那么必须先安装对应的编译器。

当前比较流行的编译器就是`GNU编译器集合`，也就是 `GCC`，其中就包括 `GCC C编译器`。GCC有各种版本适应不同的硬件平台和操作系统，用 `gcc` 命令便可调用 GCC C编译器。

- UNIX、Linux

直接安装gcc命令即可使用。

- Windows

  1. 下载Cygwin，模仿Linux命令行环境实现编译C语言。
  2. 下载MinGW，可直接在Windows的命令提示模式中运行。

  Windows下Cygwin和MinGW和GCC的最新版本一样，支持C99和C11最新的功能。

> 注意：
>
> 1、除了GCC，还有 `LLVM项目的clang命令`也是比较常见C语言编译器。
>
> 2、在一般系统中，都喜欢使用 `cc` 命令编译C语言， 其实一般系统上是将 `cc`命令作为了 `gcc或者clang`的别名。
>
> 3、gcc或者clang都支持 `-std=c99` 的选项来指定当前使用说明标准来进行编译C语言。
>
> ```shell
> # 按C99标准编译C语言
> gcc -std=c99 xx.c 
> # 按C11之前的草案标准编译C语言
> gcc -std=c1x xx.c
> # 按C11标准编译C语言
> gcc -std=c11 xx.c
> ```