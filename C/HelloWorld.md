# 第一个C语言程序HelloWorld

## 代码示范1

```c
#include <stdio.h>
void main(){
    printf("Hello World!");
}
```

## 代码示范2

```c
#include <stdio.h>
int main(){
    printf("Hello World");
    return 0;
}
```

## 代码拆解

### 头文件

### 主函数

- C语言由函数组成，有且只有一个主函数

- 程序运行，先从main函数运行，由系统自动调用，不需要人为调用

### 返回值

```c
int main(){
    return 250;
}
/*
上面的代码编译成a.exe
返回值在下面的代码中调用并输出
*/
#include <stdlib.h>
#include <stdio.h>
int main(){
    int a = system("a.exe");
    printf("a=%d",a);
}
/*
返回值在不同的平台输出的值不一样
Windows平台：a=250
Linux平台：a=6400
*/
```

### 代码块

- 代码块就是{   }的内部

- 函数的调用必须在代码块内部

## Windows系统下的编译

```bash
gcc hello.c //当前目录产生一个可执行文件a.exe
gcc hello.c -o hello.exe  //指定生成的可执行文件的文件名
gcc day03\hello.c   //会自动在当前目录生成a.exe
a.exe.    //执行该文件,控制台输出Hello World!
```

## Linux系统下的编译

```bash
gcc hello.c   //产生一个可执行文件a.out
gcc hello.c -o hello  //指定生成的可执行文件的文件名
./a.out      //执行该文件,控制台输出Hello World!，必须加当前目录./
```

## Mac系统下的编译

```bash
gcc hello.c   //产生一个可执行文件a.out
gcc hello.c -o hello  //指定生成的可执行文件的文件名
./a.out      //执行该文件,控制台输出Hello World!
a.out       //不加./也可以运行
```

## 编译的注意事项

- Linux编译后的可执行程序只能在Linux运行，Windows编译后的可执行程序只能在Windows下运行
- 64位的Linux编译后的程序只能在64位Linux下运行，32位的Linux编译后的程序只能在32位Linux下运行。
- 64位的Windows编译后的程序只能在64位Windows下运行，32位Windows编译后的程序可以在64位的Windows运行。

## C语言的注释

### 行注释

```c
//我是行注释
```

### 块注释

```c
/*
我是块注释
*/
```

## system函数

### 库名：sodlib.h

### 功能：启动一个外部程序

### 代码示例

```c
#include <stdlib.h>
int main(){
    /*
    系统命令在当前目录执行
    比如可执行程序在.\day03\a.exe,则在当前目录执行day03\a.exe返回的是当前目录的目录结构，而不是a.exe所在	 目录的目录结构
    */
    system("ls");
    /*
    hello.exe如果不在当前目录，则报错
    */
    system("hello.exe");
    /*
    还可以调用系统中的程序
    调用Windows系统中的计算器
    */
    system("calc");
    return 0;
}
```

> C语言所有的库函数调用，只能保证语法是一致的，但不能保证执行结果是一致的，同样的库函数在不同的操作系统下执行结果可能是一样的，也可能是不一样的。
>
> Linux的发展离不开POSIX标准，只要符合这个标准的函数，在不同的系统下执行的结果就可以一致。
>
> Unix和Linux很多库函数都是支持POSIX标准的，但Windows支持的比较差。

## 字符编码

- Windows默认支持的中文编码为gbk,gb2312,ANSI
- Linux默认支持的中文编码为(unicode)

## C语言的编译过程

```c
a.h
/*定义一个变量a，类型为整型*/
int a;

hello.c
/*引入头文件*/
#include "a.h"
int main(){
	return 0;
}
```

### 预处理

- 宏定义展开、头文件展开、条件编译等
- 将代码中的注释删除
- 这里并不会检查语法

```c
hello.i
/*
展开头文件，把头文件里面的代码复制到目标文件里
*/
# 1 "hello.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "hello.c"
# 1 "a.h" 1
int a;
# 2 "hello.c" 2

int main(){
 return 0;
}
```

### 编译

- 检查语法

- 将预处理后的文件编译生成汇编文件

  ```
  hello.s
  /*汇编文件*/
  	.file	"hello.c"
  	.text
  	.comm	a, 4, 2
  	.def	__main;	.scl	2;	.type	32;	.endef
  	.globl	main
  	.def	main;	.scl	2;	.type	32;	.endef
  	.seh_proc	main
  main:
  	pushq	%rbp
  	.seh_pushreg	%rbp
  	movq	%rsp, %rbp
  	.seh_setframe	%rbp, 0
  	subq	$32, %rsp
  	.seh_stackalloc	32
  	.seh_endprologue
  	call	__main
  	movl	$0, %eax
  	addq	$32, %rsp
  	popq	%rbp
  	ret
  	.seh_endproc
  	.ident	"GCC: (x86_64-posix-seh-rev0, Built by MinGW-W64 project) 8.1.0"
  ```

### 汇编

- 将汇编文件生成目标文件（二进制文件）
- 不可执行

### 链接

- 把库链接到最终的可执行程序中
- 生成可执行文件

### 分步编译

```bash
gcc -E hello.c -o hello.i   //预处理
gcc -S hello.i -o hello.s   //编译
gcc -c hello.s -o hello.o   //汇编
gcc hello.o -o hello        //链接
```

### 动态库

> 函数调用需要链接动态库

#### 查询需要的动态库

```bash
ldd hello   //查看hello可执行文件需要的动态库
		 ntdll.dll => /c/Windows/SYSTEM32/ntdll.dll (0x7ffa7f7e0000)
        KERNEL32.DLL => /c/Windows/System32/KERNEL32.DLL (0x7ffa7e7e0000)
        KERNELBASE.dll => /c/Windows/System32/KERNELBASE.dll (0x7ffa7c620000)
        apphelp.dll => /c/Windows/SYSTEM32/apphelp.dll (0x7ffa79720000)
        msvcrt.dll => /c/Windows/System32/msvcrt.dll (0x7ffa7f080000)
        
ldd a.out  //查看a.out可执行文件需要的动态库
		linux-vdso.so.1 (0x00007fff8b4cc000)
		libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fafd0efa000)
		/lib64/ld-linux-x86-64.so.2 (0x00007fafd14ed000)
		
[@David-MBP:demo (master)]$ otool -L a.out
a.out:
        /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1252.200.5)
```

