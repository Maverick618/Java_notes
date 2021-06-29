---
title: 小学期 Java 学习笔记
date: 2021-06-28 23:41:10
tags:
- Java 学习笔记
categories:
- 编程语言
---

<p align='center'>
<a href="https://blog.csdn.net/weixin_45575873?spm=1011.2124.3001.5343" target="_blank">CSDN @Mαverick      </a>
<a href="https://github.com/Maverick618" target="_blank">Github @Maverick618</a>

# JAVA 小学期

## HelloWorld

```java
public class HelloWorld{  // 主类，必须为public 且 类名与文件名相同
	public static void main(String args[]){ // public static void String 缺一不可
        									// System.lang.String 默认已被 import
		System.out.println("HelloWorld!");  // 有ln则自动换行
    }
}
// 习惯上类名/函数名后加 {


import java.util.* // 调入包util的所有类
import java.util.Scanner // 调入包util内的Scanner

```

## 数据类型与从C++到Java

### 数据类型

- boolean 和 整型不能相互转换

- boolean 不能进行数值运算，只能进行逻辑运算

- 基本类型：整型(byte, short, int, long)、浮点、布尔和字符char(unicode, 0~65535) 放在栈内

  其余类型(数组也是)放入堆内(隐式new)，称为引用数据类型

  0.0 默认是double , 0.0f才是float

  `float = 0.0`会报错

- 数据类型的默认值

  |    数据类型    |  默认值  |
  | :------------: | :------: |
  |      byte      |    0     |
  |     short      |    0     |
  |      int       |    0     |
  |      long      |    0L    |
  |      char      | '\u0000' |
  |     float      |   0.0F   |
  |     double     |   0.0D   |
  |    boolean     |  false   |
  | reference type |   null   |

- char 可以直接转 int 但 int 转 char 要强制类型转换(char)
- 用关键字final声明常量
- String类型：是一个类，可以调用方法(重载了加法运算符: 字符串拼接)，而 char 是基本数据类型
- 求余运算： (-3) % 5
- 顶层父类：Object

tips：带标签的break， continue

```java
A: for(;;)
	for(;;)
	 for(;;)
	 	break A; // 直接跳出三层循环

if(a = 5){...} //会报错，因为不支持int到Boolean 的隐式类型转换
```

### 从C++到Java

#### 引用类型

- 没有拷贝构造
  -  `Classname objectname2 = objectname1`  不会产生新的对象
  - `objectname3 = objectname1` 不是对象间的数据赋值，而是引用地址复制，二者实际指向同一对象
  - `objectname1 == objectname2` 实际上是比较对象的存放地址也即引用是否相等，而非对象数据是否相等
    - 解决办法之一：为需要比较的类写equals函数
- 参数总是值传递
  - 基本类型发生值复制
  - 引用类型发生地址的赋值，实质就是传引用
    - 即Java中**没有**`void  fun(Classname &objectname)`里的 **‘&’** 

#### 单继承与多个接口

- 只有一种继承方式，相当于C++的公有继承
- 只能有一个父类
- 一个类可以实现多个接口

#### 默认虚函数

- 在Java中，方法缺省情况下是虚的，可以使用final关键字使之声明为非虚方法(与C++相反)。

#### 模板、泛型、反射和多线程

- java 不支持模板但支持泛型，且支持反射和多线程

### 输出注释与规范

- println 自动换行而print不换
- \t:  tab转义字符
- \n:  换到下一行第一个字符
- 注释：
  - 单行： //
  - 多行： /*   */
  - 文档注释： /** */

### 第一次作业

```java
/**
* Q1:编写JAVA程序，实现接收用户输入的正整数，输出该数的阶乘
*       要求：限制输入的数据在1-10之间，无效数据进行提示，结束程序
*       输出结果如：4！=1*2*3*4=24
*/

import java.util.Scanner;

public class hw2{
    public static void main(String args[]){
        Scanner input = new Scanner(System.in);
    
        int inputNum = input.nextInt();
        while(inputNum < 0 || inputNum > 11){
            System.out.println("Input Invalid!");
            input.nextInt();
        }
        
        int answer = 1;

        System.out.print(inputNum + "!=");
        for(int i = 1; i <= inputNum; i++){
            System.out.print(i);
            answer *= i;
            if(i < inputNum)
                System.out.print("*");
        }
        System.out.println("=" + answer);
    }
}
```

```java
/**
* Q2:编写JAVA程序，实现输出1--100之间所有不能被7整除的数，并求和
*    要求：每输出4个数据换行显示
*/
public class hw1{
    public static void main(String[] args){
        int count = 1;
        int sum = 0;
        for (int i = 1; i < 101 ; i++){
            if(i % 7 != 0){
                System.out.print(i + " ");
                sum += i;
                if( count++ % 4 == 0)
                    System.out.println();
            }
        }
        System.out.println("\nSum = " + sum);
    }
}
```

