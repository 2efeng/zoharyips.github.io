---
layout: post
title: 一文逛遍所有语言基础！
categories: Markdown
keywords: Markdown, GFM
prism: [javascript, java, php, go, markup]
---

不不不，大大大大哥我错了，两三个语言也在这里逼逼，我我我错了!  
但还敢🤪


> 注：本文所有结论都是个人验证后的结论，错的话肯定是本人出错，因为本文并没有直接照搬任何一个地方的结论。

* TOC
{:toc}

## 语言类型

| Language   |  Type  | 隐式类型转换 | 自动推断类型 |
|:-----------|:------:|:------------:|:------------:|
| Java       | 强静态 |   √ (严格)   |      ×       |
| Go         | 强静态 |      ×       |      √       |
| PHP        | 弱动态 |      √       |      √       |
| Javascript | 弱动态 |      √       |      √       |

* 判断是强类型语言或者弱类型语言有一个简单的方法：如果语言中所有数据类型都能直接相比较，它就是弱类型语言。

* 判断是静态语言或者动态语言同样有一个简单的方法：如果可以在变量声明后赋予其他任意类型的值，即为动态语言。

## 数据类型

### 基本数据类型

基本数据类型即值类型，在语言使用的过程中采用值传递的方式工作

* Java

    | boolean | char | byte | short | int | long | float | double |
    |:-------:|:----:|:----:|:-----:|:---:|:----:|:-----:|:------:|
    | `false` | ` `  | `0`  |  `0`  | `0` | `0`  | `0.0` | `0.0`  |
    |    1    |  2   |  1   |   2   |  4  |  8   |   4   |   8    |

    | Type     | Minimun                | Bit Min    | Maximun                  | Bit Max       |
    |:---------|:-----------------------|:-----------|:-------------------------|:--------------|
    | `char`   | `0`                    | `0`        | `65535`                  | `1 << 16 - 1` |
    | `byte`   | `-128`                 | `-1 << 7`  | `127`                    | `1 << 7 - 1`  |
    | `short`  | `-32768`               | `-1 << 15` | `32767`                  | `1 << 15 - 1` |
    | `int`    | `-2147483648`          | `-1 << 31` | `2147483647`             | `1 << 31 - 1` |
    | `long`   | `-9223372036854775808` | `-1 << 63` | `9223372036854775807`    | `1 << 63 - 1` |
    | `float`  | `1.4E-45`              | `-`        | `3.4028235E38`           | `-`           |
    | `double` | `4.9E-324`             | `-`        | `1.7976931348623157E308` | `-`           |

* Go

    |  bool   | byte | int(8, 16, 32, 64) | uint(8,16,32,64) | rune | uintptr | float32 | float64 | complex(64 128) | string |
    |:-------:|:----:|:------------------:|:----------------:|:----:|:-------:|:-------:|:-------:|:---------------:|:------:|
    | `false` | `0`  |        `0`         |       `0`        | `0`  |   `0`   |   `0`   |   `0`   |     `0+0i`      |  `""`  |
    |    1    |  1   |     1, 2, 4, 8     |    1, 2, 4, 8    |  4   |   4/8   |    4    |    8    |     8, 128      |   -    |

    | Type          | Minimun                | Bit Min    | Maximun                   | Bit Max       |
    |:--------------|:-----------------------|:-----------|:--------------------------|:--------------|
    | `byte`        | `-128`                 | `-1 << 7`  | `127`                     | `1 << 7 - 1`  |
    | `int8`        | `-128`                 | `-1 << 7`  | `127`                     | `1 << 7 - 1`  |
    | `int16`       | `-32768`               | `-1 << 15` | `32768`                   | `1 << 15 - 1` |
    | `int32`       | `-2147483648`          | `-1 << 31` | `2147483647`              | `1 << 31 - 1` |
    | `int64`       | `-9223372036854775808` | `-1 << 63` | `9223372036854775807`     | `1 << 63 - 1` |
    | `uint8`       | `0`                    | `0`        | `255`                     | `1 << 8 - 1`  |
    | `uint16`      | `0`                    | `0`        | `65535`                   | `1 << 16 - 1` |
    | `uint32`      | `0`                    | `0`        | `4294967295`              | `1 << 32 - 1` |
    | `uint64`      | `0`                    | `0`        | `18446744073709551615`    | `1 << 64 - 1` |
    | `rune`        | `-2147483648`          | `-1 << 31` | `2147483647`              | `1 << 31 - 1` |
    | `unitptr(32)` | `0`                    | `0`        | `4294967295`              | `1 << 32 - 1` |
    | `unitptr(64)` | `0`                    | `0`        | `18446744073709551615`    | `1 << 64 - 1` |
    | `float32`     | `1.4e-45`              | `-`        | `3.4028234663852886e+38`  | `-`           |
    | `float64`     | `4.9e-324`             | `-`        | `1.7976931348623157e+308` | `-`           |

    rune 与 byte 类似，在 go 中可用于表示字符，byte 长度为 1 个字节，因此常用于表示 ASCII 字符。
    
    由于 GO 采用 UTF-8 编码，该字符集部分字符 Unicode 编码长度已超过 2 个字节，像 JAVA 的 char 类型由于仅 2 个字节，靠后的字符无力表示，因此 GO 设置了 4 个字节长度的 rune 类型，可表示基本上所有 UTF-8 字符。

* PHP

    | Boolean | Integer | Float  | String | Array  |
    |:-------:|:-------:|:------:|:------:|:------:|
    | `NULL`  | `NULL`  | `NULL` | `NULL` | `NULL` |
    |    1    |   4/8   |  4/8   |   -    |   -    |

    | Type          | Minimun                | Bit Min    | Maximun                   | Bit Max       |
    |:--------------|:-----------------------|:-----------|:--------------------------|:--------------|
    | `Integer(32)` | `-2147483648`          | `-1 << 31` | `2147483647`              | `1 << 31 - 1` |
    | `Integer(64)` | `-9223372036854775808` | `-1 << 63` | `9223372036854775807`     | `1 << 63 - 1` |
    | `Float(32)`   | `1.4e-45`              | `-`        | `3.4028234663852886e+38`  | `-`           |
    | `Float(64)`   | `4.9e-324`             | `-`        | `1.7976931348623157e+308` | `-`           |

    由于 PHP 是动态类型语言，变量声明时并不需要指定类型，对于**未赋值的变量一律以 `null` 表示**，因此对于 PHP，没有默认值这一说的😲

    同时需要注意的是，Php 的 Array 本身采用的是值传递的方式，但 Array 内的元素若为 Object 类型，复制数组是新数组的成员将是一个引用。即 PHP 的**数组复制采用浅复制**的方式。

* Javascript

    |   Boolean   |   Number    |   String    |  Function   |   Symbol    |
    |:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
    | `undefined` | `undefined` | `undefined` | `undefined` | `undefined` |
    |      1      |     4/8     |      -      |      -      |      -      |

    JS 同样是动态类型语言，变量声明时并不需要指定类型，对于**未赋值的变量一律为 `undefined`**，因此对于 JS，也没有默认值这一说；

    这里 JS 和 PHP 的不同在于，JS 对于**未声明**或**已声明但未知类型**的变量，其类型和变量值都是 `undefined`，对于**已声明但指向空**的变量，其类型为 object，其值为 `null`；  
    而 PHP 对于一个变量，无论是**已声明但未知类型**还是**已声明但指向空**，值和类型都为 `null`，而 PHP 不允许使用**未声明**的变量，哈哈。

    而且 JS 使用一个 Number 类型把其他语言的 int 和 float 合起来了，事实上 JS 对于 Number 的计算都是基于浮点数计算的，如果 JS 中没有 parseInt 这个方法的话，估计都忘了 Int 是啥了。

## 变量

### 变量声明与赋值

* Java：

    ```java
    int int1;
    int int1 = 10;
    int int1, int2;
    int int1 = 10, int2 = 20;
    ```

* Go 

    ```go
    var int1 int
    var int1 int = 10
    var int1 = 10
    int1 := 10                      // 初始化声明，仅在函数体中可用
    var int1, int2 int
    var int1, int2 int = 10, 20
    var int1, int2 = 10, 20
    int1, int2 := 10, 20
    var (                           // 一般用于声明全局变量
        int1 int
        string1 string
    )
    var (
        int1 int = 10
        string1 string = "Hello"
    )
    ```

* PHP

    ```php
    $int1 = 10;
    ```

* JS

    ```javascript
    let int1;                       // 块级作用域
    let int1 = 10;
    let int1, int2;
    let int1 = 10, int2 = 20;
    
    var int1;                       // 函数/全局作用域
    var int1 = 10;
    var int1, int2;
    var int1 = 10, int2 = 20;
    ```

### 静态变量

> Wiki: 在程序执行前系统就为之静态分配（也即在运行时中不再改变分配情况）存储空间的一类变量。

静态变量：实例共享变量

* Java

    ```java
    class TestCase {
        // qualifier static type identifier
        public static int int1;
        public static int int2 = 10;
    }
    ```

    调用：类名.变量名
    
    ```java
    System.out.println(TestCase.int1);
    ```

    Java 不支持静态局部变量，对静态变量的支持以类或接口为基础

* Go

    Go 不支持静态变量，但静态局部变量可以通过闭包实现：

    ```go
    func main() {
        staticVariable := 1
        testFunc := func() {
            fmt.Println("x:", x)
            staticVariable++
        }
        for i := 0; i < 10; i++ {
            testFunc()
        }
    }
    ```

* PHP

    ```php
    class TestCase {
        // qualifier static identifier = value;
        public static $int1;
        public static $int2 = 20;
        public function testFunc() {
            // static identifier = value;
            static $int3 = 10;
        }
    }
    ```
    
    调用：类名::变量名，或实例::变量名；局部静态变量生效范围为定义区块，直接访问即可
    
    ```php
    echo TestCase::$int1;
    echo $testCase::$int1;
    ```

* JS

    JS 不支持静态变量；静态局部变量可以简单通过闭包实现：

    ```javascript
    let func = (() => {
        var localStaticVariable = 0;
        return function() {
            localStaticVariable += 1;
            console.log(localStaticVariable);
        }
    })();
    ```
    
    而且 JS 支持类变量，所以我自己想了静态全局变量的一种写法，比较简单易懂，风格也和其他语言比较统一：

    ```javascript
    function TestCase() {
        // 类首次加载时执行，类似于静态变量的初始化
        if(typeof TestCase._initilized === "undefined") {
            TestCase.staticVariable = 0;
            TestCase._initilized = true;
        }

        /* 对象定义属性，让每个实例的属性指向类属性 */
        Object.defineProperty(this, "staticVariable", {
            configurable: true,
            enumerable: true,
            get() {
                return TestCase.staticVariable;
            },
            set(newVal) {
                TestCase.staticVariable = newVal;
            }
        })
    }
    let a = new TestCase();
    let b = new TestCase();
    a.staticVariable;       // 0
    b.staticVariable;       // 0
    a.staticVariable = 100;
    a.staticVariable;       // 100
    b.staticVariable;       // 100
    ```