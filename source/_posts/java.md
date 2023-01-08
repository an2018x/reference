---
title: Java
date: 2021-03-10 19:50:01
background: bg-[#d33731]
tags:
    - object-oriented
    - class
categories:
    - Programming
intro: |
    快速查阅 JavaSE 语法
plugins:
    - tooltip
---


JDK 安装
--------

### Windows

安装 Chocolatey [Chocolatey 安装](https://chocolatey.org/install)
```shell script
$choco install jdk8
```

### Mac

安装 HomeBrew [HomeBrew 安装](https://brew.sh/index_zh-cn)
```shell script
$brew update
$brew cask install java
```

### Linux {.row-span-2}
Ubuntu/Debain
```shell script
$sudo apt-get update
$sudo apt-get install default-jdk
```
Fedora/Redhat
```shell script
$su -c "yum install java-1.8.0-openjdk"
```


快速开始
--------

### Hello.java {.row-span-2}
```java
public class Hello {
  // Java main 方法，作为程序的入口
  public static void main(String[] args) {
    // 输出: Hello, world!
    System.out.println("Hello, world!");
  }
}
```
使用命令行编译和运行
```shell script
$ javac Hello.java
$ java Hello
Hello, world!
```

### 注释
```java
// 单行注释
 
/*
多行
注释
*/

/**
 * 文档注释
 */
```

### 定义变量 
```java
int num = 5;
float floatNum = 5.99f;
char letter = 'D';
boolean bool = true;
String site = "quickref.me";
```

### 字符串
```java
String first = "John";
String last = "Doe";
String name = first + " " + last;
System.out.println(name);
```
See: [Strings](#java-strings)




### 循环
```java
String word = "QuickRef";
for (char c: word.toCharArray()) {
  System.out.print(c + "-");
}
// Outputs: Q-u-i-c-k-R-e-f-
```
See: [Loops](#java-loops)


### 数组
```java
char[] chars = new char[10];
chars[0] = 'a'
chars[1] = 'b'

String[] letters = {"A", "B", "C"};
int[] mylist = {100, 200};
boolean[] answers = {true, false};
```
See: [Arrays](#java-arrays)

### 类型转换
```java
// Widening conversion (宽化转型)
// byte<short<int<long<float<double
int i = 10;
long l = i;               // 10

// Narrowing (窄化转型)
double d = 10.02;
long l = (long)d;         // 10
// 截尾和四舍五入
double a = 20.5;
long i1 = (long)a;  // 20 
long i2 = Math.round(a); // 21

String.valueOf(10);       // "10"
Integer.parseInt("10");   // 10
Double.parseDouble("10"); // 10.0
```

### 条件语句
```java
int j = 10;

if (j == 10) {
  System.out.println("I get printed");
} else if (j > 10) {
  System.out.println("I don't");
} else {
  System.out.println("I also don't");
}
```
See: [Conditionals](#java-conditionals)

### 控制台输入/输出 {.row-span-1 .col-span-1}
```java
Scanner in = new Scanner(System.in);
String str = in.nextLine();
System.out.println(str);

int num = in.nextInt();
System.out.println(num);
```
----

```java
// 换行打印
System.out.println("Hello");
// 不换行打印
System.out.print("World");
// 格式化打印
System.out.printf(" %d\n", 2023);

// Hello
// World 2023
```

### 面向对象 {.row-span-2 .col-span-2}

```java
public class App {
    public static void main(String[] args) {
        // 使用 new 关键字创建对象
        TestCase testCase = new TestCase();
        testCase.setValue(10);
        testCase.printValue();
        // 静态方法可以直接通过类名访问
        TestCase.printClass();
    }
}

class TestCase {
    // 字段
    private int value;

    // 方法
    public void setValue(int value) {
        this.value = value;
    }

    public void printValue() {
        System.out.println(value);
    }

    // 静态方法
    public static void printClass() {
        System.out.println(
          TestCase.class.getSimpleName()
        );
    }
}
// 10
// TestCase
```



数据类型
-----

### 基本类型 {.col-span-2}
| 基本类型   | 大小     | 默认值 | 范围               | 包装类 |
|-----------|--------|---------|---------------------|------|
| `byte`    | 1 byte | 0       | -128 ~ 127       | `Byte` |
| `short`   | 2 byte | 0       | -2^15^ ~ 2^15^-1 | `Short` |
| `int`     | 4 byte | 0       | -2^31^ ~ 2^31^-1 | `Integer` |
| `long`    | 8 byte | 0       | -2^63^ ~ 2^63^-1 | `Long`|
| `float`   | 4 byte | 0.0f    | IEEE754               | `Float`|
| `double`  | 8 byte | 0.0d    | IEEE754               | `Double`|
| `char`    | 2 byte | \\u0000 | 0 ~ 65535        | `Char`|
| `boolean` | _N/A_  | false   | true / false        | `Boolean` |
| `void`     | _N/A_  | _N/A_   | _N/A_     | `Void` |
{.show-header}

操作符
-------

### 算术操作符

```java
int a = 1, b = 2;
System.out.println(a + b); // 3
System.out.println(a - b); // -1
System.out.println(a * b); // 2
System.out.println(a / b); // 0
System.out.println(a % b); // 1
```

### 一元运算符
```java
int a = 1, b = 2;
System.out.println(a * (+b));
System.out.println(a * (-b));
// 2
// -2
```

### 自动递增/递减
```java
int a = 1;
System.out.println((a++) + " " + a); // 1 2
System.out.println((++a) + " " + a); // 3 3
System.out.println((a--) + " " + a); // 3 2
System.out.println((--a) + " " + a); // 1 1
```

### 算数-赋值运算符 {.row-span-2}

```java
int a, b, c;
a = 1; b = 2;
c = a += b;
System.out.println(a + " " + c);

a = 1; b = 2;
c = a -= b;
System.out.println(a + " " + c);

a = 1; b = 2;
c = a *= b;
System.out.println(a + " " + c);

a = 1; b = 2;
c = a /= b;
System.out.println(a + " " + c);

a = 1; b = 2;
c = a %= b;
System.out.println(a + " " + c);
// 3 3
// -1 -1
// 2 2
// 0 0
// 1 1
```

### 全部运算符 {.row-span-2}
- <a href="javascript:void(0);" data-tooltip="Additive operator (also used for String concatenation)">+</a>
- <a href="javascript:void(0);" data-tooltip="Subtraction operator">-</a>
- <a href="javascript:void(0);" data-tooltip="Multiplication operator">*</a>
- <a href="javascript:void(0);" data-tooltip="Division operator">/</a>
- <a href="javascript:void(0);" data-tooltip="Remainder operator">%</a>
- <a href="javascript:void(0);" data-tooltip="Simple assignment operator">=</a>
- <a href="javascript:void(0);" data-tooltip="Increment operator; increments a value by 1">++</a>
- <a href="javascript:void(0);" data-tooltip="Decrement operator; decrements a value by 1">--</a>
- <a href="javascript:void(0);" data-tooltip="Logical complement operator; inverts the value of a boolean">!</a>
{.marker-none .cols-4}

----

- <a href="javascript:void(0);" data-tooltip="Equal to">==</a>
- <a href="javascript:void(0);" data-tooltip="Not equal to">!=</a>
- <a href="javascript:void(0);" data-tooltip="Greater than">></a>
- <a href="javascript:void(0);" data-tooltip="Greater than or equal to">>=</a>
- <a href="javascript:void(0);" data-tooltip="Less than"><</a>
- <a href="javascript:void(0);" data-tooltip="Less than or equal to"><=</a>
{.marker-none .cols-4}

----

- <a href="javascript:void(0);" data-tooltip="Conditional-AND">&&</a>
- <a href="javascript:void(0);" data-tooltip="Conditional-OR">||</a>
- [?:](#ternary-operator){data-tooltip="Ternary (shorthand for if-then-else statement)"}
{.marker-none .cols-4}

----

- <a href="javascript:void(0);" data-tooltip="Compares an object to a specified type">instanceof</a>
{.marker-none}

----

- <a href="javascript:void(0);" data-tooltip="Unary bitwise complement">~</a>
- <a href="javascript:void(0);" data-tooltip="Signed left shift"><<</a>
- <a href="javascript:void(0);" data-tooltip="Signed right shift">>></a>
- <a href="javascript:void(0);" data-tooltip="Unsigned right shift">>>></a>
- <a href="javascript:void(0);" data-tooltip="Bitwise AND">&</a>
- <a href="javascript:void(0);" data-tooltip="Bitwise exclusive OR">^</a>
- <a href="javascript:void(0);" data-tooltip="Bitwise inclusive OR">|</a>
{.marker-none .cols-4}

字面量
-------

### 基本字面量{.row-span-2}

```java 
int i1 = 0x2f; // 16 进制
int i2 = 0x2F; // 16 进制
int i3 = 0177; // 8 进制
int i4 = 0b010101; // 2 进制, jdk 7 新增
int i5 = 0B010101; // 2 进制, jdk 7 新增
int i6 = 10; // 10 进制，不加前后缀
long l1 = 100l; // Long 类型
long l2 = 100L; // Long 类型(推荐)
float f1 = 0.1f; // float 类型
float f2 = 0.1F; // float 类型
double d1 = 0.1; // double 类型(默认)
double d2 = 0.1d; // double 类型
double d3 = 0.1D; // double 类型
```

### 转换成二进制表示

```java
Long a = 100L;
System.out.println(Long.toBinaryString(a)); 
// 1100100
```

### 下划线

```java
Long a = 1_000_000_000L;
```

### 科学计数法

```java
double a = 1e-2;
double b = 1E2;
System.out.println(a); // 0.01
System.out.println(b); // 100.0
```


Java 字符串
-------

### Basic

```java
String str1 = "value"; 
String str2 = new String("value");
String str3 = String.valueOf(123);
```


### Concatenation
```java
String s = 3 + "str" + 3;     // 3str3
String s = 3 + 3 + "str";     // 6str
String s = "3" + 3 + "str";   // 33str
String s = "3" + "3" + "23";  // 3323
String s = "" + 3 + 3 + "23"; // 3323
String s = 3 + 3 + 23;        // 29
```


### StringBuilder {.row-span-3}
StringBuilder sb = new StringBuilder(10);
```java
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
|   |   |   |   |   |   |   |   |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```
sb.append("QuickRef");
```java
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| Q | u | i | c | k | R | e | f |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```
sb.delete(5, 9);
```java
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| Q | u | i | c | k |   |   |   |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```
sb.insert(0, "My ");
```java
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| M | y |   | Q | u | i | c | k |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```
sb.append("!");
```java
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| M | y |   | Q | u | i | c | k | ! |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```


### Comparison
```java
String s1 = new String("QuickRef"); 
String s2 = new String("QuickRef"); 

s1 == s2          // false
s1.equals(s2)     // true

"AB".equalsIgnoreCase("ab")  // true
```


### Manipulation
```java
String str = "Abcd";

str.toUpperCase();     // ABCD
str.toLowerCase();     // abcd
str.concat("#");       // Abcd#
str.replace("b", "-"); // A-cd

"  abc ".trim();       // abc
"ab".toCharArray();    // {'a', 'b'}
```


### Information
```java
String str = "abcd";

str.charAt(2);       // c
str.indexOf("a")     // 0
str.indexOf("z")     // -1
str.length();        // 4
str.toString();      // abcd
str.substring(2);    // cd
str.substring(2,3);  // c
str.contains("c");   // true
str.endsWith("d");   // true
str.startsWith("a"); // true
str.isEmpty();       // false
```



### Immutable
```java
String str = "hello";
str.concat("world");

// Outputs: hello
System.out.println(str);
```

---

```java
String str = "hello";
String concat = str.concat("world");

// Outputs: helloworld
System.out.println(concat);
```

Once created cannot be modified, any modification creates a new String




Java 数组
-------


### Declare
```java
int[] a1;
int[] a2 = {1, 2, 3};
int[] a3 = new int[]{1, 2, 3};

int[] a4 = new int[3];
a4[0] = 1;
a4[2] = 2;
a4[3] = 3;
```


### Modify
```java
int[] a = {1, 2, 3};
System.out.println(a[0]); // 1

a[0] = 9;
System.out.println(a[0]); // 9

System.out.println(a.length); // 3
```


### Loop (Read & Modify)
```java
int[] arr = {1, 2, 3};
for (int i=0; i < arr.length; i++) {
    arr[i] = arr[i] * 2;
    System.out.print(arr[i] + " ");
}
// Outputs: 2 4 6
```


### Loop (Read)
```java
String[] arr = {"a", "b", "c"};
for (int a: arr) {
    System.out.print(a + " ");
}
// Outputs: a b c 
```


### Multidimensional Arrays
```java
int[][] matrix = { {1, 2, 3}, {4, 5} };

int x = matrix[1][0];  // 4
// [[1, 2, 3], [4, 5]]
Arrays.deepToString(matrix)

for (int i = 0; i < a.length; ++i) {
  for(int j = 0; j < a[i].length; ++j) {
    System.out.println(a[i][j]);
  }
}
// Outputs: 1 2 3 4 5 6 7 
```


### Sort
```java
char[] chars = {'b', 'a', 'c'};
Arrays.sort(chars);

// [a, b, c]
Arrays.toString(chars);
```




控制流
-----------


### If else
```java
int k = 15;
if (k > 20) {
  System.out.println(1);
} else if (k > 10) {
  System.out.println(2);
} else {
  System.out.println(3);
}
```

### Switch {.row-span-2}
```java
int month = 3;
String str;
switch (month) {
  case 1:
    str = "January";
    break;
  case 2:
    str = "February";
    break;
  case 3:
    str = "March";
    break;
  default:
    str = "Some other month";
    break;
}

// Outputs: Result March
System.out.println("Result " + str);
```


### 三元操作符
```java
int a = 10;
int b = 20;
int max = (a > b) ? a : b;

// Outputs: 20
System.out.println(max);
```


### For 循环
```java
for (int i = 0; i < 10; i++) {
  System.out.print(i);
}
// Outputs: 0123456789
```

----

```java
// 逗号表达式
for (int i = 0,j = 0; i < 3; i++,j--) {
  System.out.print(j + "|" + i + " ");
}
// Outputs: 0|0 -1|1 -2|2
```

### for-in 循环
```java
int[] numbers = {1,2,3,4,5};

for (int number: numbers) {
  System.out.print(number);
}
// Outputs: 12345
```
Used to loop around array's or List's


### while 循环
```java
int count = 0;

while (count < 5) {
  System.out.print(count);
  count++;
}
// Outputs: 01234
```

### do-while 循环
```java
int count = 0;

do {
  System.out.print(count);
  count++;
} while (count < 5);
// Outputs: 01234
```

### Continue 语句
```java
for (int i = 0; i < 5; i++) {
  if (i == 3) {
    continue;
  }
  System.out.print(i);
}
// Outputs: 01245
```

### 带标签的 Continue 语句

```java
int i = 0;
label1:
for (;;) {
    for (; i < 10; i++) {
        System.out.print(i);
        if (i == 3) {
            i += 2;
            continue label1;
        }
    }
    break;
}
// 012356789
```

### Break 语句
```java
for (int i = 0; i < 5; i++) {
  System.out.print(i);
  if (i == 3) {
    break;
  }
}
// Outputs: 0123
```

### 带标签的 Break 语句

```java
int i = 0;
label1:
for (;;) {
    for (; i < 10; i++) {
        System.out.print(i);
        if (i == 3) {
            i += 2;
            break label1;
        }
    }
    break;
}
// 0123
```

面向对象基础
--------------

### 构造器

```java
class TestCase {
    /**
     * 无参构造器
     */
    TestCase() {
        System.out.println("TestCase");
    }

    /**
     * 带有参数的构造器
     */
    TestCase(String str) {
        System.out.println(str);
    }
}
TestCase testCase = new TestCase();
TestCase testCase2 = new TestCase("Hello");
// TestCase
// Hello
```

### 方法重载 {.col-span-2}

```java
class TestCase {

    public void printValue(int value) {
        System.out.println("method1: " + value);
    }

    public void printValue(String value) {
        System.out.println("method2: " + value);
    }

    public void printValue(int value1, int value2) {
        System.out.println("method3: ");
        System.out.println(value1);
        System.out.println(value2);
    }
}
TestCase testCase = new TestCase();
testCase.printValue(1);
testCase.printValue("Hello");
testCase.printValue(1, 2);

// method1: 1
// method2: Hello
// method3: 
// 1
// 2

// 注意：不能通过返回值来区分重载
```

### this 关键字

```java
class TestCase {

    private int value = 10;

    public void printValue(int value) {
        System.out.println(value);
        System.out.println(this.value);
    }
}
TestCase testCase = new TestCase();
testCase.printValue(1);
// 1
// 10
```


### 初始化顺序 {.col-span-2}

```java
class TestCase {

    private SubTestCase subTestCase = new SubTestCase("定义时初始化1");

    TestCase() {
        SubTestCase subTestCase = new SubTestCase("构造函数中初始化");
    }

    private SubTestCase subTestCase2 = new SubTestCase("定义时初始化2");

    static {
        SubTestCase subTestCase = new SubTestCase("静态代码块初始化1");
    }

    private static SubTestCase subTestCase3 = new SubTestCase("静态变量初始化");

    static {
        SubTestCase subTestCase = new SubTestCase("静态代码块初始化2");
    }

    {
        SubTestCase subTestCase3 = new SubTestCase("非静态实例初始化");
    }
}

class SubTestCase {

    SubTestCase(String str) {
        System.out.println(str);
    }
}
TestCase testCase = new TestCase();
// 静态代码块初始化1
// 静态变量初始化
// 静态代码块初始化2
// 定义时初始化1
// 定义时初始化2
// 非静态实例初始化
// 构造函数中初始化
```

### 可变参数列表 {.col-span-2}

```java
public class App {
    public static void main(String[] args) {
        printArgs("arg1", "arg2");
    }

    private static void printArgs(String... args) {
        for (String arg : args) {
            System.out.println(arg);
        }
    }
}
// arg1
// arg2
```

访问控制
--------------------

### package(包)

```java
// 定义包
// 定义包
package com.ans20xx;
// 导入包
import java.util.Date;

public class App {
    public static void main(String[] args) {
        System.out.println(new Date());
        // 指定要导入的类位置
        System.out.println(
          new java.util.Date()
        );
    }
}
// Mon Jan 02 19:56:51 CST 2023
// Mon Jan 02 19:56:51 CST 2023
```

### 访问修饰符 {.col-span-2}

```java
public class TestCase {

    SubTestCase subTestCase = 
            new SubTestCase("包访问权限，默认为包访问，同一个包下的类都可以访问");

    private SubTestCase subTestCase2 =
            new SubTestCase("私有访问权限，只能被本类方法访问");

    public SubTestCase subTestCase3 =
            new SubTestCase("公开/接口访问权限，可以被所有类访问");

    protected SubTestCase subTestCase04 =
            new SubTestCase("继承访问权限，只能被该类以及该类的子类访问");
}
```

继承
----------

### extends 和 super {.col-span-2}

```java 
class TestCase {
    
    String value;

    TestCase(String value) {
        this.value = value;
    }

    protected void printValue() {
        System.out.println("value: " + value);
    }
}

/**
 * 使用 extends 关键字来表示继承关系
 * 注意 Java 中一个类不支持同时继承多个类
 */
class SubTestCase extends TestCase {

    SubTestCase(String value) {
        // 使用 super 来调用父类构造器
        super(value);
    }

    /**
     * 使用 @Override 注解表示该方法重写了父类的某个方法
     * 被该注解标注的方法会在编译器被检查命名和参数列表是否正确
     */
    @Override
    public void printValue() {
        super.printValue();
        System.out.println("SubTestCase value: " + value);
    }
}
```

### final 关键字 {.col-span-1}

```java
/**
 * final 关键字用在类上表示该类不能被继承
 */
final class TestCase {

    /**
     * 空白 final
     * 只能在构造器中被初始化一次
     */
    final String value;

    /**
     * 修饰基本类型变量
     * 表示该变量的值不能被改变
     */
    final int num = 10;

    /**
     * final 修饰对象引用，表示该引用不能修改
     */
    final String str = "finalStr";

    TestCase(String value) {
        this.value = value;
    }

    /**
     * final 用来修饰方法参数，
     * 表示该方法参数是只读的
     */
    public void printFinalArg(
        final String arg
    ) {
        System.out.println(arg);
    }

    /**
     * final 用在方法上表示该方法不能被重写
     */
    public final void printValue() {
        System.out.println(
          "value: " + value
        );
    }
}
```

多态
-------


### 向上转型 {.col-span-2}

```java
public class App {
    public static void main(String[] args) {
        TestCase testCase = new SubTestCase1();
        testCase.printClass();
        testCase = new SubTestCase2();
        testCase.printClass();
    }
}

class TestCase {

    public void printClass() {
        System.out.println(TestCase.class.getSimpleName());
    }
}

class SubTestCase1 extends TestCase{

    @Override
    public void printClass() {
        System.out.println(SubTestCase1.class.getSimpleName());
    }
}

class SubTestCase2 extends TestCase{

    @Override
    public void printClass() {
        System.out.println(SubTestCase2.class.getSimpleName());
    }
}
// SubTestCase1
// SubTestCase2
```


Java Collections Framework
--------------------

### Java Collections {.col-span-2}

| Collection                                                                                                         | Interface   | Ordered | Sorted | Thread safe | Duplicate | Nullable           |
|--------------------------------------------------------------------------------------------------------------------|-------------|---------|--------|-------------|-----------|--------------------|
| [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)                                    | List        | Y       | _N_    | _N_         | Y         | Y                  |
| [Vector](https://docs.oracle.com/javase/8/docs/api/java/util/Vector.html)                                          | List        | Y       | _N_    | Y           | Y         | Y                  |
| [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html)                                  | List, Deque | Y       | _N_    | _N_         | Y         | Y                  |
| [CopyOnWriteArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CopyOnWriteArrayList.html)   | List        | Y       | _N_    | Y           | Y         | Y                  |
| [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html)                                        | Set         | _N_     | _N_    | _N_         | _N_       | One `null`         |
| [LinkedHashSet](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html)                            | Set         | Y       | _N_    | _N_         | _N_       | One `null`         |
| [TreeSet](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html)                                        | Set         | Y       | Y      | _N_         | _N_       | _N_                |
| [CopyOnWriteArraySet](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CopyOnWriteArraySet.html)     | Set         | Y       | _N_    | Y           | _N_       | One `null`         |
| [ConcurrentSkipListSet](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentSkipListSet.html) | Set         | Y       | Y      | Y           | _N_       | _N_                |
| [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)                                        | Map         | _N_     | _N_    | _N_         | _N (key)_ | One `null` _(key)_ |
| [HashTable](https://docs.oracle.com/javase/8/docs/api/java/util/Hashtable.html)                                    | Map         | _N_     | _N_    | Y           | _N (key)_ | _N (key)_          |
| [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html)                            | Map         | Y       | _N_    | _N_         | _N (key)_ | One `null` _(key)_ |
| [TreeMap](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)                                        | Map         | Y       | Y      | _N_         | _N (key)_ | _N (key)_          |
| [ConcurrentHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentHashMap.html)         | Map         | _N_     | _N_    | Y           | _N (key)_ | _N_                |
| [ConcurrentSkipListMap](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentSkipListMap.html) | Map         | Y       | Y      | Y           | _N (key)_ | _N_                |
| [ArrayDeque](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayDeque.html)                                  | Deque       | Y       | _N_    | _N_         | Y         | _N_                |
| [PriorityQueue](https://docs.oracle.com/javase/8/docs/api/java/util/PriorityQueue.html)                            | Queue       | Y       | _N_    | _N_         | Y         | _N_                |
| [ConcurrentLinkedQueue](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentLinkedQueue.html) | Queue       | Y       | _N_    | Y           | Y         | _N_                |
| [ConcurrentLinkedDeque](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentLinkedDeque.html) | Deque       | Y       | _N_    | Y           | Y         | _N_                |
| [ArrayBlockingQueue](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ArrayBlockingQueue.html)       | Queue       | Y       | _N_    | Y           | Y         | _N_                |
| [LinkedBlockingDeque](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/LinkedBlockingDeque.html)     | Deque       | Y       | _N_    | Y           | Y         | _N_                |
| [PriorityBlockingQueue](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/PriorityBlockingQueue.html) | Queue       | Y       | _N_    | Y           | Y         | _N_                |
{.show-header .left-text}


### ArrayList
```java
List<Integer> nums = new ArrayList<>();

// Adding
nums.add(2);
nums.add(5);
nums.add(8);

// Retrieving
System.out.println(nums.get(0));

// Indexed for loop iteration
for (int i = 0; i < nums.size(); i++) {
    System.out.println(nums.get(i));
}

nums.remove(nums.size() - 1);
nums.remove(0); // VERY slow

for (Integer value : nums) {
    System.out.println(value);
}
```

### HashMap
```java
Map<Integer, String> m = new HashMap<>();
m.put(5, "Five");
m.put(8, "Eight");
m.put(6, "Six");
m.put(4, "Four");
m.put(2, "Two");

// Retrieving
System.out.println(m.get(6));

// Lambda forEach
m.forEach((key, value) -> {
    String msg = key + ": " + value;
    System.out.println(msg);
});
```

### HashSet
```java
Set<String> set = new HashSet<>();
if (set.isEmpty()) {
    System.out.println("Empty!");
}

set.add("dog");
set.add("cat");
set.add("mouse");
set.add("snake");
set.add("bear");

if (set.contains("cat")) {
    System.out.println("Contains cat");
}

set.remove("cat");
for (String element : set) {
    System.out.println(element);
}
```

### ArrayDeque
```java
Deque<String> a = new ArrayDeque<>();

// Using add()
a.add("Dog");

// Using addFirst()
a.addFirst("Cat");

// Using addLast()
a.addLast("Horse");

// [Cat, Dog, Horse]
System.out.println(a);

// Access element
System.out.println(a.peek());

// Remove element
System.out.println(a.pop());
```

Misc
----


### Access Modifiers {.col-span-2}
| Modifier    | Class | Package | Subclass | World |
|-------------|-------|---------|----------|-------|
| public      | Y     | Y       | Y        | Y     |
| protected   | Y     | Y       | Y        | _N_   |
| no modifier | Y     | Y       | _N_      | _N_   |
| private     | Y     | _N_     | _N_      | _N_   |
{.show-header .left-text}


### Regular expressions
```java
String text = "I am learning Java";
// Removing All Whitespace
text.replaceAll("\\s+", "");

// Splitting a String
text.split("\\|");
text.split(Pattern.quote("|"));
```
See: [Regex in java](/regex#regex-in-java)





### Math methods 

| Method                | Description            |
|-----------------------|------------------------|
| `Math.max(a,b)`       | Maximum of a and b     |
| `Math.min(a,b)`       | Minimum of a and b     |
| `Math.abs(a)`         | Absolute value a       |
| `Math.sqrt(a)`        | Square-root of a       |
| `Math.pow(a,b)`       | Power of b             |
| `Math.round(a)`       | Closest integer        |
| `Math.sin(ang)`       | Sine of ang            |
| `Math.cos(ang)`       | Cosine of ang          |
| `Math.tan(ang)`       | Tangent of ang         |
| `Math.asin(ang)`      | Inverse sine of ang    |
| `Math.log(a)`         | Natural logarithm of a |
| `Math.toDegrees(rad)` | Angle rad in degrees   |
| `Math.toRadians(deg)` | Angle deg in radians   |

### Try/Catch/Finally
```java
try {
  // something
} catch (Exception e) {
  e.printStackTrace();
} finally {
  System.out.println("always printed");
}
```
