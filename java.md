# 一、Java入门

## 一、java能干什么

1、**桌面应用开发**：各种税务应用软件、IDEA、Clion、Pycharm、WebStorm、PhpStorm(因为java语言比较规范，漏洞比较少，所以用Java语言编写的编译工具就比较健壮，不会有那么多的漏洞和安全性的问题)

2、**企业级应用开发**：微服务、springcloud，所谓企业级应用其实就是开发服务器，服务器可能需要承载每秒钟几十万甚至几百万的访问量，就目前而言，只有**java**和**go**语言能承载这么大的访问量。就像天猫、淘宝、京东、阿里云这些企业级应用就是用java开发的。

3、**移动应用开发或嵌入式设备的软件的开发**：鸿蒙、amdroid都可以用java开发，包括很多医疗设备中的软件都是用java开发的，机械臂里的控制程序也是用java开发的。

4、**科学计算**：matlab(这个软件可以用来做科学计算，仿真模拟)就是用Java开发的。

5、**大数据开发**：hadoop(是大数据中的一个框架，logo是一头大象)就是用java开发的。

6、**开发游戏**：我的世界就是用java开发的。

## 二、Java的主要特性

1、面向对象

2、安全性

3、多线程：可以同时干多件事情

4、简单易用

5、开源

6、跨平台

## 三、Java的跨平台原理

- Java语言的跨平台是通过虚拟机实现的。
- Java语言不是直接运行在操作系统里面的，而是运行在虚拟机中的。
- 针对不同的操作系统，安装不同的虚拟机就可以了。

## 五、JRE和JDK

**JDK(Java Development kit)：**Java开发工具包，其中包括JVM(Java virtual machine)：Java虚拟机，真正运行java程序的地方、核心类库，是java的公司提前写好的一些东西，程序员直接拿来用就可以了、开发工具，就像javac.exe java.exe这些开发工具。

**JRE(Java Runtime Environment)：**java的运行环境。其中包括JVM、核心类库、运行代码时需要的工具。

# 二、Java基础概念

## 一、字面量

**null为什么不能直接打印出来**

1、Java中字面量的分类：正数、小数、字符、字符串、布尔值、空。

2、特殊的字面量：制表符：'\t'：在打印的时候，把前面字符串的长度补齐到8，或者8的整倍数，最少补1个空格，最多补8个空格。

## 二、变量的注意事项

1、只能存一个值

2、变量名不允许重复定义

3、一条语句可以定义多个变量

```java
int a = 100, b = 200, c = 300;
```

5、**变量在使用之前一定要进行赋值(初始化)**

6、变量的作用域范围

## 三、计算机的存储规则

在计算机中任意数据都是以二进制的形式存储的

在计算机中，颜色采用光学三原色

### 一、计算机中图片如何存储

1、像素：每一个小格子就是一个像素

## 五、Java中的数据类型

java中的数据类型分为两类：基本数据类型和引用数据类型。

### 一、基本数据类型

四类八种

![image-20250604153139918](img/image-20250604153139918.png)

**整数一般默认为int，小数一般默认为double**

整数和小数取值范围大小关系：double>float>long>int>short>byte

long类型的量需要在数值后加上L后缀。float类型的量需要在数值后加上F做后缀。（大小写均可）

### 三、基本数据类型与引用数据类型的区别

1、基本数据类型中存储的是真实的数据，基本数据类型的变量名就是其存储空间的名字。特点：将基本数据类型的变量赋值给其他变量时，赋的也是真实的值。

![image-20250612160452666](img/image-20250612160452666.png)

引用数据类型的变量中存储的是真实数据存储空间的地址值。

![image-20250612160805235](img/image-20250612160805235.png)

## 六、标识符

所谓标识符就是我们自己给**类、方法、变量**等起的名字。

![image-20250604193556537](img/image-20250604193556537.png)

## 七、键盘录入

Java已经帮我们把操作系统与键盘之间的代码写好了（发现键盘、配对键盘、连接键盘、组合键盘、验证键盘、监控键盘、扫描键盘、获取键盘等），写在了Scanner这个类中了。我们只需要会用Scanner这个类就可以了。

### 第一套体系

nextInt()  接收整数     nextDouble()  接收小数，即使键盘输入的是整数，它最后也会转成double的形式。

**这套体系遇到空格、制表符、回车、就停止接收了。**

next() 接收字符串，即使键盘录入的是123这样的整数之类的，它最后也会转换成字符串的形式。

### 第二套体系

nextLine()  接收字符串

**这套体系可以接收空格、制表符、遇到回车才停止接受数据**

**键盘录入的两套体系不能混用。**

# 三、运算符

## 一、算数运算符

### 一、算数运算符的普通用法

1、在代码中，如果有**小数参与运算**的话，运算结果**可能是不精确的**。目前只需要记住这个结论就行，后续会解释为什么。

**问题**：Scanner类的底层原理

2、**全是整数的运算得到的结果也是整数，如果要得到小数，需要有小数参与计算。**

### 二、算数运算符的高级用法

1、数字进行运算时，类型不一样是不能进行运算的，需要转换成一样的类型才能运算。

#### 一、”+“法操作的三种情况

**1、数值相加**

**2、字符串相加**

（1）当”+“操作中出现字符串时，这个”+“操作此时就是一个字符串连接符，而不是一个运算符，结果是将前后的数据都当成字符串进行拼接，产生的那个新的字符串。当变量和字符串相加时，会将**变量中的值**与字符串相拼接。

![image-20250605104527718](img/image-20250605104527718.png)

（2）连续进行”+“操作时，是**从左到右逐个执行**的。

![image-20250605104640084](img/image-20250605104640084.png)

![image-20250605105204976](img/image-20250605105204976.png)

3、字符相加

#### 二、类型转换

**1、隐式类型转换（自动类型提升）**

把取值范围小的类型的量转换成取值范围大的类型

（1）隐式转换的两种提升规则

**取值范围**小的类型的量和取值范围大的类型的量在进行运算时，取值范围小的类型的量会先提升为大的，然后再进行运算。

**byte short char这三种类型的数据在进行运算时，都会先转换为int类型再进行运算**。

（2）隐式转换小结

![image-20250605103038340](img/image-20250605103038340.png)

**2、强制类型转换**

（1）如果把一个取值范围大的数据类型的数据，赋值给一个取值范围小的数据类型的变量，是不允许直接赋值的，如果非要这么做的话就需要进行强制类型转换。

（2）格式：目标数据类型 变量名 = （目标数据类型）被强转的数据

（3）**注**：如果被强转的数据数值太大，超过了目标数据类型能接受的范围，那么会发生错误，至于为什么会发生错误，发生错误的原理是什么，在第二阶段会讲。

#### 三、字符的+操作

![image-20250606095709929](img/image-20250606095709929.png)

## 二、自增自减运算符

![image-20250606100434020](img/image-20250606100434020.png)

## 三、赋值运算符

1、赋值运算符包括：=     +=     -=    *=    /=     %=

2、**细节**：+=     -=    *=    /=     %=	这些运算符底层都隐藏着一个**强制类型转化**

```java
public class AssigningoperatorDemo1 {
    public static viod main (String[] args) {
        short s = 1;
        s += 1;
        //等同于：s = (short)(s + 1)
    }
}
```



## 五、关系运算符

![image-20250606105622400](img/image-20250606105622400.png)

## 六、逻辑运算符

### 一、普通逻辑运算符

![image-20250606105705243](img/image-20250606105705243.png)

### 二、短路逻辑运算符

短路与：&&         短路或：||

## 七、三元运算符/三元表达式

**注：三元表达式的结果一定要用，否则会报错。**

## 八、运算符的优先级

![image-20250607100944085](img/image-20250607100944085.png)

## 九、源码、反码、补码

字节是计算机中最小的存储单元。源码一个字节能表示的最大值是01111111 转成十进制是+127

### 一、什么是源码

源码：十进制数据的二进制表现形式，最左边的是符号位，0为正，1为负。

利用源码对正数进行计算是没有问题的。

**但是如果是负数，就会有问题，实际结果和正确的结果正好在数轴上是反方向的。**

### 二、反码

#### 反码出现的目的：

**为了解决源码不能进行负数的计算而产生。**

#### 如何得到一个数的反码

正数的补码反码是其本身，负数的反码是符号位保持不变，其余取反，0变1，1变0。

#### 反码的弊端：

有负数参与运算的时候，如果运算结果没有跨过0，那么结果是正确的，如果运算结果跨过了0，那么结果就是错误的，会和正确的结果差一。

### 三、补码

#### 补码出现的目的：

为了解决利用反码进行负数计算时运算结果跨0的问题。

#### 如何得到一个数的补码：

正数的补码是其本身，负数的补码是在其反码的基础上+1。

另外补码还能多记录一个特殊的值-128，该数据在一个字节下，没有源码和反码。

#### 补码的厉害之处：

因为补码对于正数和负数的运算都是没有任何问题的，所以在计算机中数字的存储和运算，都是以补码的形式进行的。

### 五、一些可以用源码、反码、补码解释的运算符

![image-20250607150242522](img/image-20250607150242522.png)



#### 1、&符号两边都是数字



```java
package com.it.ls.logicoperator;

public class LogicTest2 {
    public static void main(String[] args) {
        int a = 200;
        int b = 10;
        System.out.println(a & b);
    }
}
```



![image-20250607150407822](img/image-20250607150407822.png)

**没有短路符号，只能写一个&。否则编译都不通过。**

#### 2、|符号两边都是数字



```java
package com.it.ls.logicoperator;

public class LogicTest2 {
    public static void main(String[] args) {
        int a = 200;
        int b = 10;
        System.out.println(a | b);
    }
}
```



![image-20250607150635019](img/image-20250607150635019.png)

**没有短路符号，只能写一个|。否则编译都不通过。**

#### 3、<<左移运算

左移一次就是乘2。

```java
package com.it.ls.logicoperator;

public class LogicTest2 {
    public static void main(String[] args) {
        int a = 200;
        //int b = 10;
        System.out.println(a << 2);
    }
}
```

![image-20250607151035485](img/image-20250607151035485.png)

#### 5、右移运算

右移一次就是除一次2。

```java
package com.it.ls.logicoperator;

public class LogicTest2 {
    public static void main(String[] args) {
        int a = 200;
        //int b = 10;
        System.out.println(a >> 2);
    }
}
```



![image-20250607151757936](img/image-20250607151757936.png)

# 五、流程控制语句

## 一、顺序语句

## 二、分支语句

### 一、if语句

### 二、switch语句

#### 1、格式说明

![image-20250607161258873](img/image-20250607161258873.png)

1、表达式的取值必须为byte、short、int、char、JDK5以后可以是枚举、JDK7以后可以是String。

2、case后面的值只能写字面量，不能写变量。

3、case后面的值是不允许重复的。

#### 2、switch的其他知识点

##### 1、default的位置和省略

1、位置：default不一定是写在最下面，我们可以写在任意位置，只不过是习惯写在最下面。

2、省略：default可以省略，语法不会有问题，只不过是不建议省略。

##### 2、case穿透

![image-20250607162447937](img/image-20250607162447937.png)

使用场景：

如果多个case中的语句体重复了，我们可以考虑使用case穿透简化代码。

##### 3、JDK12提出的新特性

switch语句可以这样写：

相当于利用了一个{}把break给简化了。

```java
package com.it.ls.switchdemo;

public class SwitchDemo2 {
    public static void main(String[] args){
        int number = 3;
        switch(number){
            case 1 -> {
                System.out.println("一");
            }
            case 2 -> {
                System.out.println("二");
            }
            case 3 -> {
                System.out.println("三");
            }
            default -> {
                System.out.println("没有这个选项！");
            }
        }
    }
}
//如果花括号中只有一条语句，那么花括号可以省略。
package com.it.ls.switchdemo;

public class SwitchDemo2 {
    public static void main(String[] args){
        int number = 3;
        switch(number){
            case 1 -> System.out.println("一");
            case 2 -> System.out.println("二");
            case 3 -> System.out.println("三");
            default -> System.out.println("没有这个选项！");
        }
    }
}
```



如果switch语句执行后，是一个结果，那么可以将这个switch语句赋值给一个**变量**。

##### 5、switch和if-else if的各自的使用场景

如果要对一个范围进行判断，就可以用if-else if。如果是想要将有限个东西一一列举出来，就用switch。

## 三、循环语句

### 一、for循环

for循环中可以定义多个循环变量

```java
package com.it.ls.arraydemo;

public class ArrayTest7 {
    public static void main(String[] args) {
        int arr[] = {1, 2, 3, 4, 5};
        for (int i = 0, j = arr.length - 1; i < j; i++, j --) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```



### 二、while循环

### 三、for循环与while循环对比

#### 1、相同点

运行规则都是一样的

#### 2、不同点

for循环中，控制循环的变量，因为归属for循环的语法结构中，在for循环结束后就不能再被访问到了。

while循环中，控制循环的变量，对于while循环来说不归属其语法结构中，在while循环结束后，该变量还可以继续使用。

**但是以上说法不绝对，如下图，for循环的循环控制变量也可以脱离for循环的语法结构，从而使其在循环结束后也可以继续访问到。**

![image-20250607202648765](img/image-20250607202648765.png)

#### 3、在使用习惯上的不同点

for循环：知道循环次数或循环范围

while循环：不知道循环次数和范围，只知道循环结束的条件。

### 五、循环高级

#### 1、标记思想

例题：判断一个整数是否为质数

```java
package com.it.ls.infiniteloop;

import java.util.Scanner;

public class ZhiShu {
    public static void main(String[] args) {
        System.out.println("请输入一个整数：");
        Scanner sc = new Scanner(System.in);
        int number = sc.nextInt();
        boolean flag = true;
        for (int i = 1; i <= number; i++) {
            if (number % i == 0 && i != number && i != 1) {
                System.out.println("不是质数！");
                flag = false;
                break;
            }
        }
        if (flag) {
            System.out.println("是质数！");
        }
    }
}
```

### 六、获取随机数

Random类，这个类可以生成一个随机数。

```java
import java.util.Random
    Random r = new Random();
	int number = r.nextInt(100);
//生成0~99之间的随机数
	//生成任意范围的随机数，比如生成7~15之间的随机数
	int number = r.nextInt(9) + 7
```



# 六、数组

## 一、数组介绍

数组指的是一种容器，可以用来存储**同种数据类**型的多个值。但同种数据类型不可以限定太死，可以发生隐式数据类型转换的类型都可以存到一个数组中。

## 二、数组的定义与静态初始化

### 一、数组的定义

![image-20250608190449076](img/image-20250608190449076.png)

### 二、数组的静态初始化

初始化：就是在内存中，为数组容器开辟存储空间，并将数据存入到数组中的过程。

![image-20250608191701469](img/image-20250608191701469.png)

**数组一旦创建之后，长度就确定了，不能发生变化**。

### 三、数组的地址值

![image-20250611100438672](img/image-20250611100438672.png)

## 三、数组元素访问

## 五、数组遍历

**开发建议：一个循环只做一件事情。**

## 六、数组的动态初始化

![image-20250611104415979](img/image-20250611104415979.png)

## 七、数组动态初始化和静态初始化的区别

![image-20250611112425111](img/image-20250611112425111.png)

## 八、二维数组

### 一、二维数组的应用场景

当我们需要把数组分组管理的时候，就需要用到二维数组。**在里面存储的一维度数组的长度可以不一样**。

### 二、二维数组的内存图

#### 一、普通情况

![image-20250618134337195](img/image-20250618134337195.png)

#### 二、特殊情况1

![image-20250618134744753](img/image-20250618134744753.png)

#### 三、特殊情况2

![image-20250618134940046](img/image-20250618134940046.png)

![image-20250618135021645](img/image-20250618135021645.png)

![image-20250618135047552](img/image-20250618135047552.png)

# 七、Java内存空间

1、在JDK7以及之前，方法区与堆空间都是连在一起的，在实际的的物理内存中也是连在一起的，但这样的设计不好，会导致很多问题，**至于什么问题后续讲**。

2、从JDK8开始，取消了方法区，新增了元空间。把原来方法区的多种功能进行拆分，有的功能放进了堆中，有的功能放进来元空间中。为了更好的理解，我们暂时还是把这块区域叫做方法区。

## 一、Java内存分配

### 一、栈

方法运行时使用的内存，比如main()方法运行，进入栈中执行。比如程序刚开始运行时，就会把main()方法加载到栈中去运行。

### 二、堆

存储对象或者数组，凡是用new来创建的，都存储在堆内存中。**在堆内存中开辟的每块存储空间都有地址值。**

### 三、方法区

存储可以运行的class文件，当一个类要开始运行的时候，它都会把这个类的字节码文件，也就是class文件，加载到方法区当中，临时存储。

### 五、本地方法栈

JVM在使用操作系统功能的时候使用，暂时和我们开发没有太大关系。

### 六、寄存器

给CPU使用的，暂时和我们开发也没有太大关系。

## 二、最简单的代码的内存

![image-20250611152018892](img/image-20250611152018892.png)

## 三、数组的内存图

![image-20250611152344815](img/image-20250611152344815.png)

一、两个数组指向同一个空间的内存图

![image-20250611175028915](img/image-20250611175028915.png)



# 八、方法

## 一、什么是方法

方法是程序中最小的执行单元

### 一、在实际开发中，什么时候用到方法

重复的代码，具有独立功能的代码，可以抽取到方法中。

### 二、在实际开发中，方法有什么好处

可以提高代码的复用性

可以提高代码的可维护性

## 二、方法的格式

### 一、方法的定义

![image-20250612092550694](img/image-20250612092550694.png)

### 二、方法的调用

1、**看到方法进入方法，执行完毕，回到调用处。**

2、方法调用时，参数的个数与类型必须与方法定义中的形参一一对应，否则程序将报错。

### 三、形参与实参

![image-20250612101904183](img/image-20250612101904183.png)

![image-20250612101933054](img/image-20250612101933054.png)

### 五、方法的返回值

方法的返回值其实就是方法运行的最终结果。

如果在调用处要根据方法的结果来编写另一段代码逻辑，**那么为了在调用处拿到方法产生的结果**，就需要定义一个带有返回值的方法。

## 三、方法的注意事项

1、方法不调用就不执行

2、方法与方法之间是平级关系，不能互相嵌套定义。

![image-20250612105224163](img/image-20250612105224163.png)

3、方法的返回值类型为void，表示该方法没有返回值，没有返回值的方法可以省略return语句不写。**如果要编写return，后面不能有具体的数据。**

## 五、return关键字

![image-20250612111107116](img/image-20250612111107116.png)

## 六、方法的重载

1、**在同一个类中**，定义了多个**同名的方法**，这些同名的方法**具有同种的功能。**

2、这些同名的方法，**具有不同的参数类型，或不同的参数个数，或不同的参数顺序**，这些同名的方法，就构成了重载关系。

3、方法的重载与返回值无关。

5、**java虚拟机会根据参数的不同来区分同名的方法。**

6、参数的顺序不同可以构成重载关系，**但是我们以后开发中几乎不会用到这样的重载。**

## 七、方法的内存

### 一、方法调用的基本内存原理

### 二、方法传递基本数据类型的内存原理

传递基本数据类型时，传递的是真实的数据，形参的改变，不影响实际参数的改变。

### 三、方法传递引用数据类型的内存原理

传递引用数据类型时，传递的是地址值，形参的改变，影响实际参数的值。

### IDEA自动抽取方法的快捷键：

ctrl + alt + m

### 变量名批量修改：

shift + f6

### ctrl + alt + t

# 九、面向对象

## 一、面向对象介绍

我们在代码中想要完成一件事情的时候，我们是拿对应的东西去做这件事情。

![image-20250618151838986](img/image-20250618151838986.png)

## 二、面向对象的重点学习什么

1、学习如何获取已有对象并使用

2、学习如何自己设计对象并使用

## 三、设计对象并使用

### 一、类和对象

#### 一、类（设计图）

是对象共同特征的描述。

##### 一、如何定义类

![image-20250618153550785](img/image-20250618153550785.png)

类只是代指一类事物，并不是指一个具体的事物，所以它当中的**属性**是**只定义不给值的**。

#### 二、对象

是真实存在的具体东西。是能拿来帮我们解决问题的东西。

##### 拿到对象后能做什么

能通过**对象.成员变量**的方式给成员变量赋值，或拿到成员变量中的值。能通过**对象.成员方法**调用成员方法，让它帮我们做事情。

### 二、类的几个补充注意事项

用来描述**一类事物的类**，我们称之为**JavaBean类**，在这种类中我们是不写main方法的。

在学习面向对象之前，我们写的那种有main方法的类叫做**测试类**，在这种类中我们**可以创建JavaBean类的对象**并进行**赋值**、**调用**。

1、类名首字母建议大写，做到见名知意。

2、一个java文件中可以定义多个class类，但只能有一个且必须有被public修饰的类，而且public修饰的类名必须成为代码文件名。

**但实际开发中还是建议一个文件中只定义一个class类。**

3、成员变量的完整定义格式是：**修饰符 数据类型 变量名称 = 初始化值**    **但是我们一般不指定初始化值，因为类代指一类事物，不是一个具体的事物。我们通常会选择在创建对象之后为对象赋具体的值。**

![image-20250618193426616](img/image-20250618193426616.png)

## 五、封装

### 一、面向对象三大特征

封装、继承、多态

### 二、封装

1、封装就是告诉我们，如何正确设计对象的属性和方法

2、**封装本质**：对象代表什么，就得封装对应的数据（属性）（比如有一个对象代表圆，那么它就得封装圆的半径），并提供数据对应的行为（比如利用半径画圆）。

3、封装思想的另一个应用：可以把一些零散的数据封装成一个对象，以后传递参数的时候只需要传递这个整体就可以了，不需要管这些零散的数据。

### 三、private关键字

- 是一个权限修饰符
- 可以**修饰成员**（成员变量和成员方法）
- 被private修饰的**成员**只能在**本类中**才能访问、赋值。
- **同一个类的不同实例之间，可以互相访问对方的private属性。**

**用private关键字的目的**：保证数据的安全性。比如可以在成员变量对应的set方法中对要给成员变量赋值的数据进行一个校验，确保要赋值的数据的合法性。如果不加private关键字，而是选择在每次创建具体对象后，赋值时进行校验，那如果有800个对象岂不是太累？

![image-20250618204714613](img/image-20250618204714613.png)

## 六、this关键字

### 一、成员变量与局部变量

成员变量：定义在方法外，类内的变量

局部变量：定义在方法内的变量

**就近原则**：当成员变量和局部变量重名时，用它们共同的名字调用时谁离的近调用的就是谁。

如果局部变量离的近，但是就是想调用成员变量，那么就可以在变量名前加上this关键字。

### 二、this关键字的作用

区分成员变量和局部变量

### 三、成员变量与局部变量的区别

![image-20250619120131590](img/image-20250619120131590.png)

## 七、构造方法

### 一、构造方法概述

构造方法也叫做构造器、构造函数。

**作用**：在**创建对象**的时候，由**虚拟机自动调用**，给成员变量进行**初始化赋值**的。作用就是在创建对象的时候给成员变量进行初始化的。

### 二、构造方法的格式

![image-20250618212458481](img/image-20250618212458481.png)

### 三、补充注意事项：

1、如果我们在类中没有定义任何构造方法，那么java虚拟机会自动帮我们写一个空参的构造方法。

2、如果定义了构造方法，系统将不会再为我们提供默认的无参构造方法了。

![image-20250619085704031](img/image-20250619085704031.png)

### 五、构造方法有几种，各自的作用是什么

无参构造方法：在创建对象，**成员变量的数据均采用默认值**。

有参数的构造方法：在创建对象的时候，同时还可以为对象的成员变量赋值。

## 八、对象内存图

### 一、一个对象的内存图

创建一个对象时，内存中要有**七个动作**。

![image-20250619105207039](img/image-20250619105207039.png)

s.study()方法执行完后出栈。

![image-20250619105404896](img/image-20250619105404896.png)

main方法执行完毕，出栈。

![image-20250619105530964](img/image-20250619105530964.png)

main方法出栈了，main方法中的局部变量s也会消失。那么也就没有任何变量再指向Student对象了。所以Student对象就会变成垃圾，被清理掉。

![image-20250619110038039](img/image-20250619110038039.png)

### 二、两个对象的内存图

![image-20250619110932902](img/image-20250619110932902.png)

回答：不需要了，因为在第一次创建对象的时候对象的class文件就已经加载到方法区了，所以在创建第二个对象的时候，就不需要再加载对象的class文件了，直接用就可以了。

![image-20250619112108577](img/image-20250619112108577.png)

### 三、两个引用指向同一个对象

![image-20250619112813053](img/image-20250619112813053.png)

## 九、this的内存原理

this的本质：代表所在方法调用者的地址值。

## 十、面向对象综合训练

### 一、文字版格斗游戏

**Role.java**

```java
package com.it.ls.oop;

import java.util.Random;

public class Role {
    private String name;
    private int blood;
    public Role() {

    }
    public Role(String name, int blood) {
        this.name = name;
        this.blood = blood;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getBlood() {
        return blood;
    }

    public void setBlood(int blood) {
        this.blood = blood;
    }
    //定义一个攻击的方法
    public void attach(Role role) {
        Random r = new Random();
        int hent = r.nextInt(20) + 1;
        int remain = role.getBlood() - hent;
        remain = remain < 0 ? 0 : remain;
        role.setBlood(remain);
        System.out.println(name + "打了" + role.name + "一下，造成了" + hent + "点伤害，" + role.name + "剩余血量" + remain);
    }
}
```



**问：**在这段代码中name属性被private修饰符修饰，那么在Role类中的attach方法中，采用role.name的方式可以访问到role对象中的name属性吗？

答：

1. **`role.name` 是什么？**

   `role` 是 `attach(Role role)` 方法的参数，也就是**另一个 Role 对象**，它可能是从外部传进来的。

   `name` 是 `Role` 类中的私有（private）属性。

2. **`private` 到底怎么限制访问？**

​	`private` 关键字限制了**外部类**无法通过 `role.name` 直接访问 `name` 属性。

​	但是，在 `Role` 类的**内部方法**中（比如 `attach` 方法），**不管你是 this.name 还是 role.name，只要是 Role 类型的对象，都可	以直接访问**。

3. **为什么类的内部可以访问其他同类对象的 private 属性？**

​	这是 Java 语法的一个“特权”设计——**同一个类的不同实例之间，可以互相访问对方的 private 属性**。

**总结：**

​	`role` 虽然是外部传进来的参数，但**它是 Role 类型的对象**。

​	在 `Role` 类的内部，**可以通过 `role.name` 访问任何 Role 类对象的 private 属性 `name`**，无论是 `this.name` 还是参数   		`role.name`。

​	但**类外部**不可以用 `role.name`。

**一句话理解：**

​	在 Role 类**内部**，可以用 `role.name` 访问参数 `role` 的 private 属性，因为它和当前类是同一个类。

```java
package com.it.ls.oop;

public class GameTest {
    public static void main(String[] args) {
        Role r1 = new Role("乔峰", 100);
        Role r2 = new Role("鸠摩智", 100);
        while (true) {
            r1.attach(r2);
            if (r2.getBlood() == 0){
                System.out.println(r1.getName() + "K.O" + r2.getName());
                break;
            }
            r2.attach(r1);
            if (r1.getBlood() == 0){
                System.out.println(r2.getName() + "K.O" + r1.getName());
                break;
            }
        }
    }
}
```



# 十、字符串

## 一、API&字符串

### 一、API

![image-20250621211008648](img/image-20250621211008648.png)

二、API和API帮助文档

![image-20250621211147626](img/image-20250621211147626.png)

## 二、String

### 一、String概述

java.lang包是java中的核心包，在使用的时候是不需要导包的。

![image-20250621213528253](img/image-20250621213528253.png)

### 二、String的注意点

字符串的内容是不会发生改变的，**它的对象在创建后不能被更改**。

![image-20250621213844827](img/image-20250621213844827.png)

### 三、创建String对象的两种方式

![image-20250621214203422](img/image-20250621214203422.png)

### 五、String在内存中的机制

#### 直接赋值：

通过**直接赋值的方式**创建的字符串存储在StringTable(字符串常量池)中。StringTable在堆内存中。

![image-20250622205539431](img/image-20250622205539431.png)

当使用双引号直接赋值时，系统会检查该字符串在串池中是否存在。如果**不存在**则**创建新的**，如果**存在**则**复用**

#### 通过new关键字创建

![image-20250622101716144](img/image-20250622101716144.png)

### 六、字符串的比较

#### 一、==号比的到底是什么

如果比较的是基本数据类型，那么比较的就是数据值，如果比较的是引用数据类型，**比的就是地址值**。

#### 二、字符串比较

![image-20250622111335595](img/image-20250622111335595.png)

**键盘录入的字符串在底层是new出来的。**

#### 五、遍历字符串

![image-20250622115240035](img/image-20250622115240035.png)

#### 六、字符串截取

![image-20250622180000517](img/image-20250622180000517.png)

#### 七、字符串替换

![image-20250622182639759](img/image-20250622182639759.png)

## 三、StringBuilder

### 一、SrtingBuilder概述

StringBuilder可以看作是一个**容器**，**来帮助我们操作字符串的工具**，创建之后里面的**内容是可变的**。

**作用**：提高字符串的操作效率。

![image-20250622194444881](img/image-20250622194444881.png)

### 二、StringBuilder构造方法

![image-20250622194636186](img/image-20250622194636186.png)

### 三、StringBuilder常用方法

![image-20250622194831214](img/image-20250622194831214.png)

### 五、打印SpringBuilder对象

因为StringBuilder类是java帮我们写好的，**java在底层对他做了一些特殊的处理**，**所以打印对象不是地址值而是属性值**。

### 六、链式编程

当我们调用一个方法的时候，不需要用变量接收它的结果，可以继续调用它的结果可以.调用的方法。

### 七、使用StringBuilder的场景

1、字符串的拼接

采用传统的字符串拼接方法的运行速度和内存消耗都是非常大的。**采用StringBuilder拼接字符串是高效的**。

2、字符串的反转

## 五、StringJoiner

### 一、StringJoiner概述

**可以方便高效的拼接字符串**。

![image-20250622204227935](img/image-20250622204227935.png)

### 二、StringJoiner的构造方法

![image-20250622204819348](img/image-20250622204819348.png)

### 三、StringJoiner的成员方法

![image-20250622204913383](img/image-20250622204913383.png)

## 六、字符串原理

### 扩展底层原理1：字符串存储的内存原理

![image-20250622205946288](img/image-20250622205946288.png)

### 扩展底层原理2：==号比较的到底是什么

![image-20250622210124600](img/image-20250622210124600.png)

### 扩展底层原理3：字符串拼接的底层原理

#### 1、等号的右边没有变量	

![image-20250622211153370](img/image-20250622211153370.png)

#### 2、等号的右边有变量参与

在JDK8以前，等号右边有变量参与的字符串拼接底层采用的是StringBuilder，但是采用这种方式一个加号会在堆内存中创建两个对象，一个是StringBuilder对象一个是字符串对象。因为StringBuilder中的toString方法的底层也是通过new一个String对象实现的StringBuilder转字符串。所以这样的方法太消耗资源且效率很慢。

![image-20250623203547476](img/image-20250623203547476.png)

JDK8及以后，稍微做了一下改进，在有变量参与的字符串拼接前，JDK会先做一个预估，预估一下拼接后的字符串长度，然后根据这个长度创建一个字符串数组，把每个要拼接的字符串放到数组中去，然后再转换为String对象。但是如果向下面所示的，有好几次拼接，那么也是会存在创建多个数组对象的问题。

![image-20250623205406940](img/image-20250623205406940.png)

### 扩展底层原理4：StringBuilder提高效率原理图

因为StringBuilder是一个内容可变的容器，所以采用StringBuilder拼接字符串的效率是高的，因为**只需要创建一个StringBuilder对象**，然后每次拼接都通过append()方法将要拼接的字符串添加到StringBuilder对象中即可。**所以如果有多字符变量拼接就用StringBuilder或这StringJoiner。**

![image-20250623210951899](img/image-20250623210951899.png)

### 扩展底层原理5：StringBuilder源码分析

![image-20250623212805527](img/image-20250623212805527.png)

### 字符串原理小结：

![image-20250623214457268](img/image-20250623214457268.png)

### 常见面试问题：

![image-20250623210433211](img/image-20250623210433211.png)

![image-20250623210620172](img/image-20250623210620172.png)

### 练习题：调整字符串的内容并比较

```java
package com.it.ls.test;

import com.sun.nio.sctp.AbstractNotificationHandler;

public class Test2 {
    public static void main(String[] args) {
        String s1 = "abcde";
        String s2 = "ABC";
        boolean result = compare(s1, s2);
        System.out.println(result);
    }
    public static String rotate(String str) {
        //套路
        //以后我们如果看到要修改字符串里面的内容
        //可以有两个办法：
        //1.用subString进行截取
        //2、可以把字符串先变成一个字符数组，然后调整字符数组里面的数据，最后再把字符数组变成字符串。

        //1.用subString进行截取
        /*String first = str.substring(0, 1);
        String last = str.substring(1);
        String newStr = last + first;
        return newStr;*/
        //2、可以把字符串先变成一个字符数组，然后调整字符数组里面的数据，最后再把字符数组变成字符串。
        char[] chars = str.toCharArray();
        char first = chars[0];
        for (int i = 1; i < chars.length; i++) {
            chars[i - 1] = chars[i];
        }
        chars[chars.length - 1] = first;
        return new String(chars);
    }
    public static boolean compare(String s1, String s2) {
        for (int i = 0; i < s1.length(); i++) {
            s1 = rotate(s1);
            if (s1.equals(s2)) {
                return true;
            }
        }
        return false;
    }
}
```

# 十一、集合

## 一、为什么要有集合

因为**集合的长度是可变的**，它的**长度一开始是0**，它**可以自动扩容**，不需要我们管，我们只需要向里面添加元素就可以了，这一点比数组好用。

## 二、集合存储数据类型的特点

集合中可以存储引用数据类型的数据，**但是不可以直接存储基本数据类型的数据**，如果想要存储基本数据类型的数据就需要把基本数据类型的数据变为其对应的包装类。

## 三、集合的体系结构

![image-20250817191904138](img/image-20250817191904138.png)

### 一、单列集合

下面图片中红色的是接口，蓝色的是实现类。

![image-20250817192210910](img/image-20250817192210910.png)

#### 一、Collection

Collection是单列集合的祖宗接口，**它的功能是全部单列集合都可以继承使用的**。

![image-20250817192443069](img/image-20250817192443069.png)

![image-20250817192801522](img/image-20250817192801522.png)

![image-20250817192918890](img/image-20250817192918890.png)

因为set系列集合没有索引。

4、判断元素是否包含

细节：底层是依赖equals方法进行判断是否存在的。

所以，**如果集合中存储的是自定义对象，也想通过contains方法来判断是否包含，那么在javabean类中，一定要重写equals方法。**

#### 二、Collection的通用遍历方式

##### 一、迭代器遍历

1、迭代器是**不依赖索引的**，所以如果遍历到超了集合本身长度的地方不会报索引越界异常，会报NoSuchElementException异常。

2、迭代器在java中的类是Iterator，**迭代器是集合专用的遍历方式**。

**在Collection集合中获取迭代器**：

![image-20250817195120678](img/image-20250817195120678.png)

**Interator中的常用方法**：

![image-20250817195329171](img/image-20250817195329171.png)

![image-20250817200749220](img/image-20250817200749220.png)

**细节注意点：**

1、当迭代器遍历结束后，指针此时指向了最后一个元素的后面，如果此时再调用next()方法，会报错NoSuchElementException

2、迭代器遍历完毕，指针不会复位。要想再遍历一遍请重新再创建一个迭代器。

3、每次循环中只能用一次next（）方法。next()方法和hasNext（）方法要结合着成对使用。

5、迭代器遍历时不能用**集合的方法**进行增加或删除元素。（**为什么**）如果实在要删除，可以用迭代器提供的remove方法删除，如果要增加，暂时没有方法。如下面的代码所示，虽然next()方法的作用是获取当前位置的元素，并将迭代器对象移向下一个位置。但是用迭代器提供的删除方法，即使已经执行过next()方法了，删除的还是next()返回的当前的元素，不是下一个位置的元素。**因为**，我们可以看下面的迭代器源码讲解那里，在那里的next()方法的源码里，有一个lastRet变量，它里面存储了上一次操作的索引，所以删除时删除的是lastRet变量里存储的值对应的索引位置上的变量。

```java
package com.it.ls.mylist;

import java.util.ArrayList;
import java.util.Iterator;

public class MyListDemo2 {
    public static void main(String[] args) {
        ArrayList<String> arrayList = new ArrayList<>();
        arrayList.add("aaa");
        arrayList.add("bbb");
        arrayList.add("ccc");

        Iterator<String> iterator = arrayList.iterator();
        while (iterator.hasNext()) {
            String s = iterator.next();
            if (s == "aaa"){
                iterator.remove();
            }
        }
        System.out.println(arrayList);
    }
}
```





##### 二、增强for遍历

![image-20250817205147716](img/image-20250817205147716.png)

![image-20250817210313057](img/image-20250817210313057.png)

##### 三、Lambda表达式遍历

![image-20250817205627945](img/image-20250817205627945.png)

![image-20250819165000389](img/image-20250819165000389.png)

#### 三、List系列集合

##### 一、List系列集合的特点

![image-20250817212322783](img/image-20250817212322783.png)

##### 二、List集合的特有方法

![image-20250817212420228](img/image-20250817212420228.png)

**List系列集合中有两个remove方法：**

采用直接删除元素的方法来删除元素时，如果要删除的这个元素在集合中是重复的，那么执行remove方法会删除重复元素中**位置最靠前**的那个元素。

![image-20250819151452054](img/image-20250819151452054.png)



##### 三、List集合的遍历方式

###### 1、迭代器

![image-20250819165235980](img/image-20250819165235980.png)

###### 2、增强for

![image-20250819165338906](img/image-20250819165338906.png)

###### 3、lambda表达式

**匿名内部类方式：**

![image-20250819165457055](img/image-20250819165457055.png)

**lambda表达式方式：**
![image-20250819165539127](img/image-20250819165539127.png)

###### 5、普通for循环

![image-20250819170842624](img/image-20250819170842624.png)

###### 6、列表迭代器

列表迭代器不止有添加元素的方法，也有和迭代器一样的删除元素的方法。

![image-20250819170830191](img/image-20250819170830191.png)

###### 7、五种遍历方式对比

![image-20250819171102169](img/image-20250819171102169.png)

##### 五、ArrayList

###### 泛型：

限定集合中存储的数据的类型。

![image-20250624212606406](img/image-20250624212606406.png)

###### 基本数据类型对应的包装类

![image-20250625095112305](img/image-20250625095112305.png)

###### ArrayList的成员方法

![image-20250625161231154](img/image-20250625161231154.png)

ArrayList集合有一个特点：就是add方法永远都返回true，也就是它永远都可以将元素添加成功。

**添加整数并进行遍历**

![image-20250625095235525](img/image-20250625095235525.png)

###### ArrayList集合的底层原理

![image-20250819144334374](img/image-20250819144334374.png)

**当用空参构造创建集合后，开始添加第一个元素的底层原理：**

![image-20250819145312297](img/image-20250819145312297.png)



**存满时，扩容1.5倍和1.5倍放不下，以实际为准时的底层原理**：

右移一位相当于除以2。

DEFAULTCAPACITY_EMPTY_ELEMENTDATA代表空数组。

![image-20250819152042528](img/image-20250819152042528.png)

##### 六、LinkedList集合

**底层数据结构是双向列表**，查询慢，增删快，但是要是操作的是首尾元素，速度也是极快的。

LinkedList本身多了很多操作首尾元素的特有API

###### 一、LinkedList的特有方法

![image-20250819160225078](img/image-20250819160225078.png)

###### 二、LinkedList集合的底层原理

last是尾节点，是Node类型的。first是头节点，是Node类型的。

![image-20250819161606690](img/image-20250819161606690.png)

###### 三、迭代器的底层原理

next()方法中return (E) elementData[lastRet = i];这句代码详解：

- 赋值表达式本身也有返回值，它返回的是所赋的值（即 `i` 的值）。
- 执行完后，`lastRet` 的值就是 `i` 的值

![image-20250819175914112](img/image-20250819175914112.png)

#### 五、Set系列集合

![image-20250820181125431](img/image-20250820181125431.png)

Set**接口**中的方法几乎与Collection的API一致。

##### 一、HashSet底层原理

HashSet集合底层采用**哈希表**来存储数据。

**哈希表**是一种对于**增删改查**数据性能都很好的数据结构。

哈希表组成：

![image-20250820181819496](img/image-20250820181819496.png)

###### 1、哈希值

![image-20250820182153750](img/image-20250820182153750.png)

###### 2、对象的哈希值特点

![image-20250820182223737](img/image-20250820182223737.png)

![image-20250820184248121](img/image-20250820184248121.png)

![image-20250820184314138](img/image-20250820184314138.png)

**应存入的位置**：int index = (数组长度 - 1) & 哈希值;

加载因子：就是HashSet的扩容时机，当数组里面存了16 * 0.75 = 12 个元素的时候，此时数组就会扩容到**原先的两倍**。

###### 3、HashSet集合的去重机制

HashSet集合就是利用HashCode方法和equals方法来去重的。

所以如果HashSet集合中存储的是自定义对象，那么**必须在自定义对象的类中重写hashCode和equals方法**。

##### 二、LinkedHashSet的底层原理

**有序**、不重复、无索引

![image-20250820185131505](img/image-20250820185131505.png)

以后如果仅仅需要数据去重的话，默认使用HashSet，如果需要去重且存取有序的话，使用LinkedHashSet。为什么默认使用HashSet呢？因为LinkedHashSet底层比HashSet又多了一个双向列表，是不是占用的资源也更多啊。

##### 三、TreeSet的特点

- 不重复、无索引、**可排序**。
- 默认是按元素从小到大的顺序排列的。
- TreeSet集合底层是基于**红黑树的数据结构实现排序的**，**增删改查性能都较好**。红黑树的底层就是红黑树。

###### 1、TreeSet集合的排序规则

**对于数值类型和字符字符串类型**：

![image-20250820194113223](img/image-20250820194113223.png)

**对于自定义对象：**

方式一：**默认排序/自然排序**：JavaBean类实现Comparable接口指定比较规则。

![image-20250820194436656](img/image-20250820194436656.png)

方式二：**比较器排序**：创建TreeSet集合时，传递Comparator指定规则。

**使用原则**：默认使用方式一，如果方式一不能满足当前需求就使用方式二。

**如果方式一和方式二同时存在，那么虚拟机会听方式二的**。就比如下图，字符串底层源码中用方式一的方式定义了排序规则了，但是我们下面用方式二又定义了一个新的排序规则，那么虚拟机还是以我们定义的方式二为准的。

![image-20250821084624250](img/image-20250821084624250.png)

#### 六、总结

![image-20250821110917381](img/image-20250821110917381.png)

### 二、数据结构

#### 一、数据结构概述

计算机存储，组织数据的方式。**不同的业务场景要选择不同的数据结构。**

![image-20250819081350335](img/image-20250819081350335.png)

#### 二、常见的数据结构

![image-20250819081455264](img/image-20250819081455264.png)

#### 三、数组

**查询速度快**，元素在内存中是连续存储的，在查找时通过地址值和索引来进行定位，查询任意数据耗时相同。**查询速度快的原因**：数组（Array）这种数据结构之所以**查询速度快**，主要原因是**数组中的元素在内存中是连续存储的，每个元素的地址都可以通过索引直接计算出来**。**公式**：元素地址=数组地址+元素大小*索引。数组的**查找时间复杂度是 O(1)**，也叫“常数时间查询”。

删除效率低：要将原始数据删除，再将后面每个数据前移。

添加效率低：先将添加位置后的每个元素后移，再添加元素。

#### 五、链表

单向链表中的节点是独立的对象，在内存中是不连续存储的，每个节点包含它所存储的数据值和下一个节点的地址值。

单向链表**查询速度慢**，因为无论查找哪个元素都要从头开始查找。平均时间复杂度是O(n)。

双向链表在查询第N个元素时**效率会有所提升**。在查询前会先判断第N个元素离头近还是离尾近，离头近就从头开始查，离尾近就从尾开始查。

**链表增删相对快**。

#### 六、树

![image-20250820113147632](img/image-20250820113147632.png)

二叉树中**任意节点**的度<=2

##### 一、二叉搜索树

![image-20250820130415670](img/image-20250820130415670.png)

###### 1、添加节点的规则：

小的存左边，大的存右边，一样的不存。

###### 2、查找节点：

和添加节点一样的

###### 3、二叉树的遍历方式:

**注意**：这些遍历方式所有二叉树都可以用

（1）前序遍历

![image-20250820132725142](img/image-20250820132725142.png)

（2）中序遍历

**最为常见也是最重要的**

![image-20250820132917271](img/image-20250820132917271.png)

（3）后序遍历

![image-20250820133103071](img/image-20250820133103071.png)

（4）层序遍历

![image-20250820133142400](img/image-20250820133142400.png)

###### 5、二叉搜索树的弊端

如下图所示，如果想要查找13，就得一个一个的遍历整个树，查找效率和列表一样了，**很低**。**一棵树想要提高查询效率，左右的高度要差不多才可以。**

![image-20250820133859417](img/image-20250820133859417.png)



##### 二、平衡二叉树

在二叉搜素树的基础上又加了一条规则：**任意节点**左右**子树**高度差不超过1

###### 1、旋转规则

![image-20250820140538509](img/image-20250820140538509.png)

（1）左旋

比较简单的一种情况：

![image-20250820141647618](img/image-20250820141647618.png)

![image-20250820141551809](img/image-20250820141551809.png)

比较难的一种情况：

![image-20250820141808550](img/image-20250820141808550.png)

![image-20250820141934421](img/image-20250820141934421.png)

（2）右旋

比较简单的情况：

![image-20250820144442808](img/image-20250820144442808.png)

比较复杂的情况：

![image-20250820144656261](img/image-20250820144656261.png)

![image-20250820144808283](img/image-20250820144808283.png)

###### 2、平衡二叉树需要旋转的四种情况

![image-20250820150107009](img/image-20250820150107009.png)

###### 3、平衡二叉树优缺点

高度平衡，**查找非常快**，但是**添加节点效率不高**，因为旋转。

##### 三、红黑树

- 红黑树是一种自平衡的二叉查找树，是计算机科学中用到的一种数据结构。
- 1972年出现，当时被称为平衡二叉B树。后来1978年被修改为如今的“红黑树”。
- 它是一种特殊的**二叉查找树**，红黑树的每一个节点上都有存储位来表示节点的颜色。
- **每一个节点可以是红或者黑**，红黑树**不是高度平衡的**，它的平衡是通过**红黑规则**来实现的。

###### 1、红黑规则

![image-20250820171309452](img/image-20250820171309452.png)

###### 2、添加节点

添加节点时默认节点是**红色的**，**这样做添加效率高**。

![image-20250820173749956](img/image-20250820173749956.png)

**红黑树增删改查性能都会比较好。**

### 三、泛型深入

**泛型**：是JDK5中引入的特性，可以在**编译阶段**约束操作数据的数据类型，并进行检查。

**泛型的格式**：<数据类型>

**注意**：**泛型只能支持引用数据类型。**

#### 一、泛型的好处

没有泛型的话，集合中什么类型的元素都能存，那么我们在遍历获取集合中数据的时候，因为集合中存储的元素没有统一的类型，所以都会上升为Object类型，那因为多态的弊端，我们无法使用取出来的数据的特有行为。强转的话也不行，到底该强转成哪个类型？会报类型转换异常的。

![image-20250819183100352](img/image-20250819183100352.png)

#### 二、扩展知识点

Java中的泛型是**伪泛型**。在编译的时候，也就是代码是java文件的时候是存在泛型的，当运行的时候，也就是当代码是class文件的时候，泛型就不存在了。这在java里有一个专业术语，叫做**泛型擦除**。当数据进入集合之后集合还是把所有数据都当作是Object类型的，只不过当将数据从集合中往外获取的时候，在集合的底层将这些Object类型的数据再按照泛型进行强转。

![image-20250819184017029](img/image-20250819184017029.png)



#### 三、泛型类

使用场景：当一个类中，**某个变量的数据类型不确定时**，就可以定义带有泛型的类。创建该类对象时E就确定类型。创建对象时E得写，**不写的话就是默认的Object类型。**

MyArrayList.java

```java
package com.it.ls.mygenerics;

import java.util.Arrays;

public class MyArrayList <E>{
    Object[] obj = new Object[10];
    int size;
    public boolean add(E e){
        obj[size] = e;
        size++;
        return true;
    }
    public E get(int index){
        return (E) obj[index];
    }

    @Override
    public String toString() {
        return Arrays.toString(obj);
    }
}
```



GenericsDemo2.java

```java
package com.it.ls.mygenerics;

public class GenericsDemo2 {
    public static void main(String[] args) {
        MyArrayList<String> list = new MyArrayList<>();
        list.add("AAA");
        list.add("BBB");
        list.add("CCC");
        System.out.println(list);

        MyArrayList<Integer> list2 = new MyArrayList<>();
        list2.add(1);
        list2.add(2);
        list2.add(3);

        System.out.println(list2);
    }
}
```



#### 五、泛型方法

![image-20250819192601889](img/image-20250819192601889.png)

![image-20250819211526796](img/image-20250819211526796.png)

当调用方法的时候类型就被确定了。

#### 六、泛型接口

![image-20250819212901409](img/image-20250819212901409.png)

1、实现类给出具体类型

MyArrayList2.java

```Java
package com.it.ls.mygenerics;

import java.util.*;

public class MyArrayList2 implements List<String> {
    @Override
    public int size() {
        return 0;
    }

    @Override
    public boolean isEmpty() {
        return false;
    }

    @Override
    public boolean contains(Object o) {
        return false;
    }

    @Override
    public Iterator<String> iterator() {
        return null;
    }

    @Override
    public Object[] toArray() {
        return new Object[0];
    }

    @Override
    public <T> T[] toArray(T[] a) {
        return null;
    }

    @Override
    public boolean add(String s) {
        return false;
    }

    @Override
    public boolean remove(Object o) {
        return false;
    }

    @Override
    public boolean containsAll(Collection<?> c) {
        return false;
    }

    @Override
    public boolean addAll(Collection<? extends String> c) {
        return false;
    }

    @Override
    public boolean addAll(int index, Collection<? extends String> c) {
        return false;
    }

    @Override
    public boolean removeAll(Collection<?> c) {
        return false;
    }

    @Override
    public boolean retainAll(Collection<?> c) {
        return false;
    }

    @Override
    public void clear() {

    }

    @Override
    public String get(int index) {
        return "";
    }

    @Override
    public String set(int index, String element) {
        return "";
    }

    @Override
    public void add(int index, String element) {

    }

    @Override
    public String remove(int index) {
        return "";
    }

    @Override
    public int indexOf(Object o) {
        return 0;
    }

    @Override
    public int lastIndexOf(Object o) {
        return 0;
    }

    @Override
    public ListIterator<String> listIterator() {
        return null;
    }

    @Override
    public ListIterator<String> listIterator(int index) {
        return null;
    }

    @Override
    public List<String> subList(int fromIndex, int toIndex) {
        return List.of();
    }


}
```



GenericsDemo3.java

```java
package com.it.ls.mygenerics;

import java.util.Arrays;

public class GenericsDemo3 {
    public static void main(String[] args) {
        MyArrayList2 myArrayList2 = new MyArrayList2();
        myArrayList2.add("a");
        myArrayList2.add("b");
        myArrayList2.add("c");

        for (int i = 0; i < myArrayList2.size(); i++) {
            System.out.println(myArrayList2.get(i));
        }
    }
}
```



2、实现类延续泛型，创建对象时再确定

MyArrayLis3.java

```java
package com.it.ls.mygenerics;

import java.util.Collection;
import java.util.Iterator;
import java.util.List;
import java.util.ListIterator;

public class MyArrayList3<E> implements List<E> {
    @Override
    public int size() {
        return 0;
    }

    @Override
    public boolean isEmpty() {
        return false;
    }

    @Override
    public boolean contains(Object o) {
        return false;
    }

    @Override
    public Iterator<E> iterator() {
        return null;
    }

    @Override
    public Object[] toArray() {
        return new Object[0];
    }

    @Override
    public <T> T[] toArray(T[] a) {
        return null;
    }

    @Override
    public boolean add(E e) {
        return false;
    }

    @Override
    public boolean remove(Object o) {
        return false;
    }

    @Override
    public boolean containsAll(Collection<?> c) {
        return false;
    }

    @Override
    public boolean addAll(Collection<? extends E> c) {
        return false;
    }

    @Override
    public boolean addAll(int index, Collection<? extends E> c) {
        return false;
    }

    @Override
    public boolean removeAll(Collection<?> c) {
        return false;
    }

    @Override
    public boolean retainAll(Collection<?> c) {
        return false;
    }

    @Override
    public void clear() {

    }

    @Override
    public E get(int index) {
        return null;
    }

    @Override
    public E set(int index, E element) {
        return null;
    }

    @Override
    public void add(int index, E element) {

    }

    @Override
    public E remove(int index) {
        return null;
    }

    @Override
    public int indexOf(Object o) {
        return 0;
    }

    @Override
    public int lastIndexOf(Object o) {
        return 0;
    }

    @Override
    public ListIterator<E> listIterator() {
        return null;
    }

    @Override
    public ListIterator<E> listIterator(int index) {
        return null;
    }

    @Override
    public List<E> subList(int fromIndex, int toIndex) {
        return List.of();
    }
}
```



GenericsDemo3.java

```java
package com.it.ls.mygenerics;

import java.util.Arrays;

public class GenericsDemo3 {
    public static void main(String[] args) {
        MyArrayList3<String> list = new MyArrayList3<>();
        list.add("A");
        list.add("B");
        list.add("C");
    }
}
```



#### 七、泛型的继承和通配符

##### 1、泛型的继承

泛型不具备继承性，但是数据具备继承性

**泛型不具备继承性：**

![image-20250820084223539](img/image-20250820084223539.png)

数据具备继承性：

![image-20250820084524548](img/image-20250820084524548.png)

**利用泛型方法有一个小弊端，就是它可以接受任何类型的参数。**

![image-20250820084932020](img/image-20250820084932020.png)

我们希望，本方法虽然是一个泛型方法，不确定形参的类型，但是以后我希望只能传递Ye Fu Zi。

此时我们就可以使用泛型的通配符

##### 2、泛型的通配符

![image-20250820085543207](img/image-20250820085543207.png)

注意：`public static void method(ArrayList<?> list){}`和`public static<E> void method(ArrayList<E> list){}`是一样的。

应用场景：

![image-20250820101846338](img/image-20250820101846338.png)

### 五、双列集合

#### 一、双列集合的特点

1、双列集合一次需要存**一对数据**，分别为**键和值**。

2、键**不能重复**，值**可以重复**

3、键和值是**一一对应**的，每一个键只能找到自己对应的值。

4、键+值这个整体我们称之为**“键值对”**或者**“键值对对象”**，在Java中叫做**"Entry对象"**

![image-20250825212305535](img/image-20250825212305535.png)

#### 二、Map集合的常见API

![image-20250826212858189](img/image-20250826212858189.png)

![image-20250826213709123](img/image-20250826213709123.png)

#### 三、Map的遍历方式

1、按键找值

2、键值对

3、Lambda表达式

##### 一、按键找值

下面通过map.keySet()创建的Set集合是一个**HashMap&KeySet类型的对象**，HashMap&KeytSet类型的对象是HashMap中的一个**内部类**，专门用于表示键集合的类。这个 `KeySet` **不是一个独立的、全新的集合对象**，它只是底层 `HashMap` 的一个**动态视图**。这意味着**你并没有创建一个新的Set来存储所有的键。**你对 `KeySet` 的操作会**直接作用到底层的 `Map`** 上。例如，如果你调用 `keys.remove("尹志平")`，那么 `("尹志平", "小龙女")` **这个键值对会立刻从 `map` 中被删除**。由于它只是一个视图，本身并不存储数据，所以**不允许直接添加元素**。如果你调用 `keys.add("新的键")`，将会抛出 `UnsupportedOperationException`。

```java
package com.it.ls.mymap;

import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class MapDemo1 {
    public static void main(String[] args) {
        //Map集合的第一种遍历方式

        //创建Map集合对象
        Map<String, String> map = new HashMap<>();

        //田间元素
        map.put("尹志平", "小龙女");
        map.put("郭靖", "穆念慈");
        map.put("欧阳克", "黄蓉");

        //通过键找值
        //获取所有的键，把这些键放到一个单列集合中
        Set<String> keys = map.keySet();
        //遍历单列集合得到每一个键
        for (String key : keys) {
            //利用map集合中的键获取每一个值 get
            String value = map.get(key);
            System.out.println(key + ":" + value);
        }

    }
}
```



##### 二、键值对遍历

```java
package com.it.ls.mymap;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;
import java.util.function.Consumer;

public class MapDemo3 {
    public static void main(String[] args) {
        //创建集合对象
        Map<String, String> map = new HashMap<String, String>();

        map.put("标枪选手", "马超");
        map.put("人物挂件", "明世隐藏");
        map.put("御龙骑士", "尹志平");

        //Map集合的第二种遍历方式
        //通过键值对对象进行遍历
        //通过entrySet（）方法获取所有键值对对象，返回一个Set集合
        Set<Map.Entry<String, String>> entries = map.entrySet();
        //用增强for的方式遍历entries集合得到里面的键值对对象
        for (Map.Entry<String, String> entry : entries) {
            //调用get方法获取键和值
            String key = entry.getKey();
            String value = entry.getValue();
            System.out.println(key + "=" + value);
        }

        //用迭代器的方式遍历entries集合得到里面的键值对对象
        Iterator<Map.Entry<String, String>> iterator = entries.iterator();
        while (iterator.hasNext()) {
            Map.Entry<String, String> entry = iterator.next();
            String key = entry.getKey();
            String value = entry.getValue();
            System.out.println(key + "=" + value);
        }

        //用lambda表达式的方式遍历entries集合得到里面的键值对对象
        entries.forEach(new Consumer<Map.Entry<String, String>>() {

            @Override
            public void accept(Map.Entry<String, String> stringStringEntry) {
                String key = stringStringEntry.getKey();
                String value = stringStringEntry.getValue();
                System.out.println(key + "=" + value);
            }
        });
    }
}
```



##### 三、Lambda表达式遍历方式

```java
package com.it.ls.mymap;

import java.util.HashMap;
import java.util.Map;
import java.util.function.BiConsumer;

public class MapDemo4 {
    public static void main(String[] args) {
        //Map集合的第三种遍历方式
        Map<String, String> map = new HashMap<String, String>();

        map.put("鲁迅", "这句话是我说的");
        map.put("曹操", "不可能绝对不可能");
        map.put("刘备", "接着奏乐接着舞");
        map.put("柯镇恶", "看我眼色形式");

        //利用lambda表达式进行遍历
        //底层
        //forEach其实就是利用第二种方式进行遍历，依次得到每一个键值对，将键和值分别传递给accept函数
        map.forEach((String key, String value)->{
                System.out.println(key + ":" + value);
            }
        );
    }
}
```



#### 五、HashMap的特点

(1)HashMap是Map里面的一个实现类。

(2)没有额外需要学习的方法，直接使用Map里面的方法就可以了。

(3)特点都是由键决定的：无序、不重复、无索引

(4)HashMap和HashSet底层原理是**一模一样的**。都是哈希表结构。

![image-20250828084456411](img/image-20250828084456411.png)

##### 一、HashMap集合练习(存储自定义对象)

HashMap的键位置如果存储的是自定义对象，需要重写hashCode和equals方法。

Student.java

```java
package com.it.ls.mymap;

import java.util.Objects;

public class Student {
    private String name;
    private int age;

    public Student(){

    }
    public Student(String name, int age){
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return age == student.age && Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}
```



HashMapDemo1

```java
package com.it.ls.mymap;

import java.util.HashMap;
import java.util.Set;

public class HashMapDemo1 {
    public static void main(String[] args) {
        //同姓名同年龄被认为是同一个对象

        HashMap<Student, String> hashMap = new HashMap<>();
        //创建三个学生对象
        Student s1 = new Student("zhangsan", 23);
        Student s2 = new Student("lisi", 24);
        Student s3 = new Student("wangwu", 25);
        Student s4 = new Student("wangwu", 25);

        //向集合中添加元素
        hashMap.put(s1, "江苏");
        hashMap.put(s2, "浙江");
        hashMap.put(s3, "福建");
        hashMap.put(s4, "山东");

        //遍历
        Set<Student> students = hashMap.keySet();
        for (Student student : students) {
            String value = hashMap.get(student);
            System.out.println(student + " : " + value);
        }
    }
}
```



##### 二、HashMap集合练习（利用Map集合进行统计）

提到**统计**，我们第一个想到的就是计数器，但是计数器思想有一个弊端，那就是如果需要统计的内容很多，那就需要创建很多个计数器，况且还有一种情况，如果不知道统计的内容有几个，那就完蛋了。所以遇到这种情况的时候，我们可以利用map集合进行统计。

用Map集合进行统计有两种方法，一种是利用HashMap集合进行统计，一种是利用TreeMap集合进行统计，那么什么时候该用什么呢？

HashMap：**当只需要统计，不需要对统计结果进行排序的时候。**

TreeMap：**当需要对统计结果进行排序的时候。**

```java
package com.it.ls.mymap;

import java.util.HashMap;
import java.util.Map;
import java.util.Random;
import java.util.Set;

public class HashMapDemo2 {
    public static void main(String[] args) {
        String[] arr = {"A", "B", "C", "D"};
        HashMap<String, Integer> hashMap = new HashMap<>();
        Random rand = new Random();
        for (int i = 0; i < 80; i++) {
            int x = rand.nextInt(arr.length);
            if(hashMap.containsKey(arr[x])) {
                hashMap.put(arr[x], hashMap.get(arr[x]) + 1);
            }else {
                hashMap.put(arr[x], 1);
            }
        }

        System.out.println(hashMap);

        int max = 0;
        Set<String> keySet = hashMap.keySet();
        for (String key : keySet) {
            if(max < hashMap.get(key)) {
                max = hashMap.get(key);
            }
        }
        System.out.println(max);

        Set<Map.Entry<String, Integer>> entries = hashMap.entrySet();
        for (Map.Entry<String, Integer> entry : entries) {
            if(max == entry.getValue()) {
                System.out.println(entry.getKey());
            }
        }
    }
}
```



##### 三、HashMap源码超详细解析

###### 1、首次添加元素

![image-20250901161848235](img/image-20250901161848235.png)

![image-20250901162201432](img/image-20250901162201432.png)

![image-20250901162229417](img/image-20250901162229417.png)

![image-20250901162324853](img/image-20250901162324853.png)

![image-20250901162411437](img/image-20250901162411437.png)

![image-20250901162957954](img/image-20250901162957954.png)



![image-20250901163103291](img/image-20250901163103291.png)

![image-20250901162544962](img/image-20250901162544962.png)

![image-20250901162656037](img/image-20250901162656037.png)



###### 2、数组位置不为null,键不重复，挂在下面形成列表或红黑树

![image-20250901164534818](img/image-20250901164534818.png)



![image-20250901164846082](img/image-20250901164846082.png)



![image-20250901165104777](img/image-20250901165104777.png)

###### 3、数组位置不为null，键重复，需要元素覆盖

![image-20250901170029570](img/image-20250901170029570.png)

**我们之前所说的元素的覆盖其实是不准确的，从下面的源码可以看出来，其实不是元素的覆盖，而是键值对中值的覆盖。**

![image-20250901170845289](img/image-20250901170845289.png)

#### 六、LinkedHashMap集合

**由键决定**：**有序**、不重复、无索引

这里的有序指的是保证存储和取出的元素顺序一致。

原理：和LinkedHashSet一样，底层还是哈希表，只不过是每个键值对元素又额外多了一个双向列表机制记录存储顺序。

#### 七、TreeMap集合

TreeMap和TreeSet一样，底层都是红黑树结构的。

**由键决定特性**：无序、不重复、**可排序**

可排序：**对键进行排序**

注意：默认按照键的从小到大顺序排序，也可以自己规定键的排序规则。

##### 一、代码书写两种排序规则

**实现Comparable接口，指定比较规则。**

Integer、String这些在底层都实现了Comparable接口了。

![image-20250901114807321](img/image-20250901114807321.png)

**创建集合时传递Comparator比较器对象，指定比较规则。**

```java
package com.it.ls.TreeMap;

import java.util.Comparator;
import java.util.TreeMap;

public class TreeMapDemo1 {
    public static void main(String[] args) {
        TreeMap<Integer, String> treeMap = new TreeMap<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                //o1表示当前要添加的元素
                //o2表示已经在红黑树中存在的元素
                return o2 - o1;
            }
        });
        treeMap.put(1, "粤利粤");
        treeMap.put(2, "康帅傅");
        treeMap.put(3, "九个核桃");
        treeMap.put(4, "雷碧");
        treeMap.put(5, "可恰可乐");
        System.out.println(treeMap);
    }
}
```



Integer和Double这些默认都是按照升序排序的。

String按照字母在ASCII码表中对象的数字升序排序。

##### 二、TreeMap练习(键位置添加自定义对象)

因为TreeMap集合底层是要排序的，所以如果键位置是自定义对象的话一定**要实现Comparable接口**。

Student.java

```java
package com.it.ls.TreeMap;

public class Student implements Comparable<Student>{
    private String name;
    private int age;

    public Student(){}
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public int compareTo(Student o) {
        int i = this.getAge() - o.getAge();
        i = i == 0 ? this.getName().compareTo(o.getName()) : i;
        return i;
    }
}
```



TreeMapDemo2.java

```java
package com.it.ls.TreeMap;

import java.util.TreeMap;

public class TreeMapDemo2 {
    public static void main(String[] args) {
        TreeMap<Student, String> treeMap = new TreeMap<>();
        Student s1 = new Student("zhangsan", 23);
        Student s2 = new Student("lisi", 24);
        Student s3 = new Student("wangwu", 25);

        treeMap.put(s1, "江苏");
        treeMap.put(s2, "天津");
        treeMap.put(s3, "北京");
        System.out.println(treeMap);
    }
}
```



##### 三、TreeMap练习(利用TreeMap进行统计)

```java
package com.it.ls.TreeMap;

import java.util.Comparator;
import java.util.Map;
import java.util.Set;
import java.util.TreeMap;

public class TreeMapDemo3 {
    public static void main(String[] args) {
        String str = "aababcabcdabcde";
        TreeMap<Character, Integer> treeMap = new TreeMap<>();
        for (int i = 0; i < str.length(); i++) {
            if (treeMap.containsKey(str.charAt(i))) {
                int value = treeMap.get(str.charAt(i));
                value += 1;
                treeMap.put(str.charAt(i), value);
            }else {
                treeMap.put(str.charAt(i), 1);
            }
        }

        Set<Map.Entry<Character, Integer>> entries = treeMap.entrySet();
        StringBuilder stringBuilder = new StringBuilder();
        for (Map.Entry<Character, Integer> entry : entries) {
            Character key = entry.getKey();
            Integer value = entry.getValue();
            stringBuilder.append(key).append("(").append(value).append(")").append(" ");
        }
        System.out.println(stringBuilder.toString());
    }
}
```



##### 五、总结

![image-20250901142555839](img/image-20250901142555839.png)



##### 六、TreeMap集合源码超详细解析

###### 1、阅读源码前需要知道的知识

TreeMap集合里面的元素是Entry对象，Entry对象的属性有下面这些，我们说红黑树的节点默认是红色的，可是下面为什么是黑色的？别急！其实就是默认是红色的，等一会儿我们会看到TreeMap在调用put（）方法添加元素的时候会进行调整，调整成默认是红色的。

![image-20250901175150454](img/image-20250901175150454.png)

###### 2、添加元素

覆不覆盖值和HashMap是反过来的，为什么是反过来的？因为它们的判断逻辑是不一样的。 

![image-20250901175335887](img/image-20250901175335887.png)

当添加首个元素的时候，根节点是null。

![image-20250901181304822](img/image-20250901181304822.png)

![image-20250901181406155](img/image-20250901181406155.png)

当添加第二个元素的时候。

![image-20250901184707791](img/image-20250901184707791.png)



![image-20250901182115324](img/image-20250901182115324.png)

在代码中如果我们用的是无参的构造方法创建的TreeMap对象，那走的就是else里面的代码，我们下面以else里面的代码为例。

![image-20250901184840138](img/image-20250901184840138.png)

![image-20250901191452077](img/image-20250901191452077.png)

addEntry()方法会对添加进来的节点按照红黑树的规则进行调整

![image-20250901191906444](img/image-20250901191906444.png)



![image-20250901192000215](img/image-20250901192000215.png)

#### 八、面试易问问题

![image-20250901193651766](img/image-20250901193651766.png)



![image-20250901193709462](img/image-20250901193709462.png)

#### 九、可变参数

方法**形参的个数**是可以变化的。

**格式**：数据类型...名字

**底层**：可变参数底层就是一个**数组**，只不过不需要我们自己创建了，java底层会帮我们创建好。

![image-20250901194331170](img/image-20250901194331170.png)

可变参数的小细节：（1）在方法的形参中只能有一个可变参数。（2）如果方法的形参中既有可变参数又有其他参数，那么要把可变参数写到最后面。

上面的所有细节都是因为可变参数是一个大胖子，有多少实参它就吃多少实参，如果有两个可变参数，那所有的实参都会被第一个可变参数吃掉。如果可变参数写到前面，那么其他参数对应的实参也会被可变参数吃掉。

### 六、Collections

- java.util.Collections是集合工具类。
- 不是集合，而是用来操作集合的工具类。

#### 一、Collections常用的API

![image-20250902183917651](img/image-20250902183917651.png)

### 七、不可变集合详解

#### 一、不可变集合的应用场景

![image-20250907205000328](img/image-20250907205000328.png)

**不可变集合，别人只能查询集合中的数据，不能添加、删除、修改。**

#### 二、创建不可变集合的书写格式

![image-20250907205142518](img/image-20250907205142518.png)

1、当我们要获取一个不可变的Set集合时，**里面的参数一定要保证唯一性**，否则会报错。

![image-20250907210121624](img/image-20250907210121624.png)

2、创建map的不可变集合，JVM会把第一个和第二个参数认为是一个键值对，以此类推。

注意：（1）键是不可重复的。（2）Map里面的这个of方法参数是有上限的，最多只能传递20个参数，10个键值对。（3）如果我们要传递超过10个键值对对象，在Map接口中还有一个方法。

![image-20250907210327075](img/image-20250907210327075.png)

```java
package com.it.ls.immutable;

import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.Set;

public class immutableDemo1 {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("张三", "南京");
        map.put("李四", "北京");
        map.put("王五", "上海");
        map.put("赵六", "北京");
        map.put("孙七", "深圳");
        map.put("周八", "杭州");
        map.put("吴九", "宁波");
        map.put("郑十", "苏州");
        map.put("刘一", "无锡");
        map.put("陈二", "嘉兴");
        map.put("aaa", "111");

        //2、利用上面的数据来创建一个不可变集合
        //获取到所有的键值对对象
        Set<Map.Entry<String, String>> entries = map.entrySet();
        //因为可变参数底层就是一个数组，所以把Set集合变为数组。
        //toArray()方法在底层会比较Set集合的长度和数组的长度的大小。
        //如果集合的长度>数组的长度，说明数据在数组中放不下，此时会根据实际数据的个数，重新创建数组。
        //如果集合的长度<=数组的长度，说明数据在数组中放的下，此时不会创建新的数组而是直接用。
        Map.Entry[] array = entries.toArray(new Map.Entry[0]);
        Map map1 = Map.ofEntries(array);

        //JDK10之后出现了一个新方法
        Map<String, String> stringStringMap = Map.copyOf(map);
    }
}
```



# 十二、面向对象进阶

## 一、static关键字

staric表示静态，是java中的一个关键字，可以用来修饰成员变量，成员方法。	

### 一、被static修饰的成员变量，叫做静态变量

#### 1、特点：

被该类所有对象**共享**，在内存中只有一份，谁要用谁去拿。

**不属于对象，属于类。**

**随着类的加载而加载，优先于对象存在。**因为只有执行了new关键字，在内存当中才有对象。

**什么样的属性需要被static修饰：**需要被共享的属性。

#### 2、调用方式

类名调用（推荐）

对象名调用

### 二、static内存图

类的字节码文件一加载到方法区中时，静态区也就随之出现了，**是优先于对象出现在内存里面的。**只有执行了new关键字，在内存当中才有对象。静态区中存储着该类所有的静态变量。

只要是用静态static修饰的，都是随着类的加载而加载，所以是优先于对象而出现的。

![image-20250626150704672](img/image-20250626150704672.png)

![image-20250626153021287](img/image-20250626153021287.png)

### 三、被static修饰的成员方法，叫做静态方法

#### 1、特点：

多用在测试类和工具类中，javabean类中很少用。

#### 2、调用方式：

如果在本类中调用直接写方法名调用，如果调用别的类的静态方法推荐用类名调用，当然也可以用对象名调用。

### 五、工具类

![image-20250626160323580](img/image-20250626160323580.png)

### 六、static的注意事项

#### 一、静态方法中没有this关键字

1、this：表示当前方法调用者的地址值

2、在类的非静态成员方法的形参中其实隐藏着一个this变量，**这个变量的类型是这个成员方法所属的类的类型**。当调用这个方法时，**虚拟机会将调用该方法的对象的地址值赋值给这个this变量**。

如下图所示，通过s1.show1()调用show1()方法，虚拟就会把s1的地址值赋值给show1()方法形参中的this变量。通过s2.show1()调用show1()方法，虚拟就会把s2的地址值赋值给show1()方法形参中的this变量。

![image-20250626202207647](img/image-20250626202207647.png)

如下图所示，其实我们在调用成员变量的时候，它们的前面有一个**隐含的this**。在show1()中调用show2()我们是可以直接在show1()中写一个show2()来调用的，但其实它也有一个**隐含的this**关键字的。

![image-20250626202721704](img/image-20250626202721704.png)

在静态方法中就没有this关键字。

为什么虚拟机要这样设计呢？在非静态的成员方法中设置this关键字，而在静态方法中不设置this关键字？那是因为非静态的东西一般都是和对象相关的，所以需要设置this关键字来表示调用它们的那个对象的地址值。而静态的东西一般都是共享的，是和类相关的，不是和具体的对象相关的。所以不需要设置this关键字。

#### 二、静态方法中只能访问静态的东西

因为非静态的东西都是和对象有关的，所以在本类中调用本类的非静态的东西其实前面都隐藏着一个this.。代表着当前调用对象的地址值。但是静态方法中没有this，所以它不能调用非静态变量以及非静态方法。

![image-20250626203508606](img/image-20250626203508606.png)

![image-20250626203523922](img/image-20250626203523922.png)

![image-20250626203653715](img/image-20250626203653715.png)

#### 三、非静态方法中可以访问所有

因为静态变量和静态方法都有两种调用方式，一种是通过类名调用，一种是通过对象名调用。

![image-20250626204104138](img/image-20250626204104138.png)

#### 五、总结

![image-20250627092639158](img/image-20250627092639158.png)

### 七、static注意事项的内存图解释

#### 一、静态方法里不可以访问非静态的成员变量和非静态的成员方法

如下图静态方法method()是通过类名Student调用的，所以虚拟机就会到堆内存中的Student的静态区中去找name和teacherName这两个变量，由于name是非静态的成员变量，所以它在方法区中，方法区中的字节码文件中有类的所有非静态的成员变量和所有的成员方法。所以在堆内存的静态区中是找不到的。而teacherName是静态变量，它在静态区中，所以是可以找到的。**所以静态方法中不能访问非静态的成员变量。**

![image-20250627085042724](img/image-20250627085042724.png)

**静态方法中也不能调用非静态的成员方法**，如下图，show()是非静态的，所以它需要具体的对象去调用。假设method()中可以调用show()，但method()是通过类Student调用的，所以就没有具体的对象可以去调用method()中的show()。

![image-20250627092021784](img/image-20250627092021784.png)

#### 二、非静态可以访问所有

下图中show()是通过s1调用的，通过s1是可以找到非静态的成员变量和静态变量的。

![image-20250626213043146](img/image-20250626213043146.png)

不管是静态方法还是非静态方法都是存储在方法区中的，s1对象它在调方法的时候就会去找到方法区，所以它在方法区中肯定可以找到静态的method()方法。show()是非静态的方法，是通过s1调用的，所以非静态可以访问所有。

![image-20250626213853538](img/image-20250626213853538.png)

### 八、静态方法、变量和非静态方法、变量的区别

静态方法、变量**属于类**，可以在**没有实例**的情况下调用；非静态方法**属于实例**，**必须通过实例调用**。

### 九、重新认识main方法

#### 一、详解mian方法

![image-20250627110852299](img/image-20250627110852299.png)

#### 二、main方法中调用非静态的东西

main方法是静态方法，因此它**不能直接调用**非静态的东西，静态的东西属于类，而非静态的东西属于类的实例，为了在main方法中调用非静态的东西，**可以通过实例化对象在main方法中调用非静态的东西。**

## 二、继承

### 一、继承

![image-20250627112016238](img/image-20250627112016238.png)

继承是面向对象三大特征之一，可以让类和类之间产生父子关系。

### 二、继承的好处

- 可以把多个子类中**重复的代码**抽取到父类中，子类可以直接使用，减少代码冗余，提高代码的复用性。
- 子类可以在父类的基础上增加其他的功能，使子类更加强大。（所谓长江后浪推前浪一浪更比一浪强）

### 三、什么时候用继承

当类与类之间，存在相同的内容，并满足子类是父类的一种，就可以考虑使用继承来优化代码。

### 五、继承后子类的特点

- 子类可以**直接调用**父类的**非私有**属性和行为。
- 子类**可以**在父类的基础上**新增**其他行为，子类更强大。

### 五、继承的特点

每个类都**直接**或**间接**继承于Object类，当我们写一个类时，如果它没有继承任何类，那么**虚拟机就会自动给这个类加上一个默认的继承关系，使其继承于Obiect类。**如果我们写一个类时继承了别的类，那么就没事儿了。

![image-20250627115238797](img/image-20250627115238797.png)

在继承体系最上面的类都是默认的直接继承于Obiect类的，继承体系下面的类都是间接的继承于Obiect类的。

![image-20250627144001367](img/image-20250627144001367.png)

**在继承体系中，子类是可以使用自己直接父类里的内容，也可以使用自己间接父类里的内容。**

子类只能**调用**父类中非私有的成员。（注意：**调用和继承不是一个概念**）

### 六、子类到底能继承父类中的哪些内容

**构造方法**不管是私有的还是非私有的都不能被子类继承下来。**成员变量**不管是私有的还是非私有的都可以被继承下来，只不过是私有的子类不能直接使用而已。**成员方法**非私有的能被继承下来，私有的不能被继承下来。

![image-20250627154225006](img/image-20250627154225006.png)

#### 一、私有成员变量是否能被继承

##### 成员变量继承内存图

在一个类执行之前，会先将该类的字节码文件加载到方法区中**临时存储**，在执行main方法中的第一行代码之前，因为要用到Zi这个类了，所以会先把Zi这个类的字节码文件加载到方法区，当加载的时候发现Zi类有一个爸爸，所以也会将Zi类的爸爸，Fu类的字节码文件也加载到方法区中。但是Fu类的默认父类是Obiect类，所以其实也会将Obiect类的字节码文件加载到方法区中的。

![image-20250627162405773](img/image-20250627162405773.png)

执行new Zi()时会在堆内存中开辟一块空间，**将这块空间划分为两部分**，一部分存放Zi类的成员变量，另一部分存放从Fu类继承来的成员变量。然后为它们赋上默认的初始值。

![image-20250627163300901](img/image-20250627163300901.png)

在执行z.name="钢门吹雪"时虚拟机会**先到**堆内存的001空间的右边也就是**子类**的成员变量中**找**name这个变量，如果没找到就到左边从**父类**继承过来的成员变量中**找**。在执行z.game="王者农药"和z.age=23的时候同上。

![image-20250627162202741](img/image-20250627162202741.png)

私有的成员变量是可以被继承的，如下图所示，但是它不能被直接调用。

![image-20250627170230506](img/image-20250627170230506.png)

#### 二、成员方法是否可以被继承

**虚方法**：非private修饰的、非static修饰的、非final修饰的才是虚方法。

只有**父类中的虚方法**才能被子类继承

##### 成员方法继承内存图

当执行z.ziShow()和z.fuShow1()这两句代码的时候，虚拟机会直接到Zi的虚方法表中去找有没有这两个方法，如果有就把它直接从虚方法表中加载到栈内存中去执行。当执行到z.fuShow2()时，同样的虚拟机会直接到Zi的虚方法表中去找有没有fuShow2()方法，结果发现没有，那虚拟机就会到Zi.class文件中的成员方法中去找这个方法，结果还是没有，那么它就会到它的父类的字节码文件中去找这个方法，找到了，但是这个方法是private修饰的私有方法，所以它调用不了。

![image-20250701203310603](img/image-20250701203310603.png)

### 七、继承中成员变量的访问特点

**万整版就近原则**：谁离我近我就访问谁。

#### 案例一

如下图：第一条输出语句直接打印name，所以它就会一级一级往上找，谁离它近就用谁。第二条输出语句它打印了this,name用了this关键字，所以它不会一级一级往上找，它会直接到本类的成员位置找。第三条输出语句，它打印了super.name用来super关键字，所以它也不会一级一级往上找，它会直接到父类的成员位置找。**super表示父类的意思**。**注意：在子类中一条语句中只能有一个super，有多个会报错。**

![image-20250703113205967](img/image-20250703113205967.png)

![image-20250703113224408](img/image-20250703113224408.png)

#### 案例二：

打印喝茶有三种写法，第二种写法this.hobby会先到子类的成员变量种去找hobby，如果没有再到父类的成员变量中去找，这是它的寻找过程。

![image-20250703115720384](img/image-20250703115720384.png)



![image-20250703115649663](img/image-20250703115649663.png)

#### 总结：

![image-20250703120152318](img/image-20250703120152318.png)

### 八、方法重写

#### 1、方法重写

将父类的方法在子类中重写一遍，**当父类的方法不能满足子类现在的需求时需要进行方法重写**。

#### 2、书写格式

**在继承体系中**，子类中出现了和父类中一模一样的方法声明

#### 3、@Override重写注解

1、@Override是放在重写后的方法上面，校验子类重写时语法是否正确。

2、加上注解后如果有红色波浪线，表示语法错误。

3、建议重写方法都加@Override注解，代码安全、优雅。

#### 5、方法重写的本质

方法重写的本质就是，子类覆盖了**从父类继承下来**的**虚方法表中的方法**。

![image-20250707183839400](img/image-20250707183839400.png)

#### 6、方法重写注意事项和要求

1、重写方法的**名称**、**形参列表**必须和父类中的一致。

2、子类重写父类方法时，访问权限子类必须**大于等于**父类（暂时了解：空着不写<protected<public）

3、子类重写父类方法时，返回值类型必须**小于等于**父类。

4、建议：**重写的方法尽量和父类保持一致**

5、**只有被添加到虚方法表中的方法才能被重写。**

### 九、继承中构造方法的访问特点

- 父类中的构造方法不会被子类继承，是通过super调用的。为什么不可以被子类继承呢？你想：假设可以被子类继承，子类中构造方法的名字和类名是不是就不一样了？
- 子类中**所有的构造方法默认**先访问**父类**中的**无参构造**，再执行自己。

#### **为什么**

- 子类在初始化的时候，有可能会使用到父类中的数据，如果父类没有完成初始化，子类将无法使用父类的数据。
- **所以子类在初始化之前，一定要先调用父类的构造方法，先完成父类数据空间的初始化。**

#### 怎么调用父类的构造方法？

子类构造方法的**第一行语句默认**都是：**super()**，**不写也存在，且必须在第一行**。

**如果想调用父类的有参构造，必须手动写super进行调用**，手动调用了父类的有参构造或者无参构造那么就不会默认调用父类的无参构造了。

#### 示例代码：

1、下述代码体现了，子类的所有构造方法中，第一行语句默认都是super()。

Person.java

```java
package com.it.ls.oppextendsdemo8;

public class Person {
    String name;
    int age;
    public Person(){
        System.out.println("父类的无参构造");
    }
    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }
}
```



Student.java

```java
package com.it.ls.oppextendsdemo8;

public class Student extends Person {
    public Student() {
        //子类中所有的构造方法，默认先访问父类的无参构造方法，再执行自己。
        System.out.println("子类的无参构造");
    }
    public Student(String name, int age) {
        
    }
}
```



Test.java

```java
package com.it.ls.oppextendsdemo8;

public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        /*Student s1 = new Student("zhangsan", 23);
        System.out.println(s1.name + " " + s1.age);*/
    }
}
```



运行结果：

```
父类的无参构造
子类的无参构造
```

下述代码同样也能说明，**子类可以继承并调用父类中非私有的成员变量**，并且在子类中可以通过this关键字去调用从父类中继承来的非私有成员变量，并且在其他类中也可以通过s1.name（s1为子类对象）的方式调用从父类继承来的非私有成员变量。

Student.java

```java
package com.it.ls.oppextendsdemo8;

public class Student extends Person {
    public Student() {
        //子类中所有的构造方法，默认先访问父类的无参构造方法，再执行自己。
        System.out.println("子类的无参构造");
    }
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```



```java
package com.it.ls.oppextendsdemo8;

public class Test {
    public static void main(String[] args) {
        //Student s = new Student();
        Student s1 = new Student("zhangsan", 23);
        System.out.println(s1.name + " " + s1.age);
    }
}
```



运行结果：

```
父类的无参构造
zhangsan 23
```



下述代码说明，子类**虽然可以继承父类中私有的成员变量，但是不能调用。**

Person.java

![image-20250708193834226](img/image-20250708193834226.png)

Student.java

![image-20250708193854756](img/image-20250708193854756.png)

Test.java

![image-20250708193926313](img/image-20250708193926313.png)

下述代码说明，当手动的调用了父类中的构造方法时，那么就不会默认调用父类的无参构造了。 

Person.java

```java
package com.it.ls.oppextendsdemo8;

public class Person {
    String name;
    int age;
    public Person(){
        System.out.println("父类的无参构造");
    }
    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }
}
```



Student.java

```java
package com.it.ls.oppextendsdemo8;

public class Student extends Person {
    public Student() {
        //子类中所有的构造方法，默认先访问父类的无参构造方法，再执行自己。
        System.out.println("子类的无参构造");
    }
    public Student(String name, int age) {
        super(name, age);
    }
}
```



Test.java

```java
package com.it.ls.oppextendsdemo8;

public class Test {
    public static void main(String[] args) {
        //Student s = new Student();
        Student s1 = new Student("zhangsan", 23);
        System.out.println(s1.name + " " + s1.age);
    }
}
```



运行结果：

```
zhangsan 23
```



### 十、this、super使用总结

#### 一、this

它其实**就是一个局部变量**，在底层对于虚拟机来说它就是一个局部变量，它表示当前方法调用者的地址值。

#### 二、super

代表父类存储空间

![image-20250709092854029](img/image-20250709092854029.png)

this(...)访问本类的构造方法。常用于，调用本类的无参构造创建对象时，**想要给某些成员变量一个默认值**。如下面的代码。this(...)也必须写在第一行。当在一个构造方法中使用了this(...)时，虚拟机就不会再添加默认的super()了，因为this(...)表示调用本类的其他构造，其他构造方法中有默认的super()。**问题：**其他方法中可以用this(...)吗？还是只有构造方法中能用this(...)？

![image-20250709093236176](img/image-20250709093236176.png)

![image-20250709093250262](img/image-20250709093250262.png)

### 带有继承结构的标准javaBean类：

1、带有继承结构的标准javaBean类的全参构造方法中要包括父类+子类的所有成员变量。

2、标准javaBean类具备的点。

Employee.java

```java
package com.it.ls.oopextenddemo10;

public class Employee {
    private String id;
    private String name;
    private int salary;

    public Employee(){

    }
    public Employee(String id, String name, int salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public int getSalary() {
        return salary;
    }

    public void setSalary(int salary) {
        this.salary = salary;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void work(){
        System.out.println("员工在工作");
    }
    public void eat(){
        System.out.println("吃米饭");
    }
}
```



Manager.java

```java
package com.it.ls.oopextenddemo10;

public class Manager extends Employee{
    private double award;

    public  Manager(){

    }
    //全参的构造方法，父类+子类所有的成员变量都要有
    public Manager(String id, String name, int salary, double award) {
        super(id, name, salary);
        this.award = award;
    }

    public double getAward() {
        return award;
    }

    public void setAward(double award) {
        this.award = award;
    }

    @Override
    public void work() {
        System.out.println("管理其他人");
    }
}
```



Cooker.java

```java
package com.it.ls.oopextenddemo10;

public class Cooker extends Employee{
    public Cooker() {}
    public Cooker(String id, String name, int salary) {
        super(id, name, salary);
    }

    @Override
    public void work() {
        System.out.println("炒菜");
    }
}
```



Test.java

```java
package com.it.ls.oopextenddemo10;

public class Test {
    public static void main(String[] args) {
        Manager manager = new Manager("heima001", "zhangsan", 15000, 8000);
        System.out.println(manager.getId() + " " + manager.getName() + " " + manager.getSalary() + " " + manager.getAward());
        manager.work();
        manager.eat();

        Cooker cooker = new Cooker();
        cooker.setId("heima001");
        cooker.setName("lisi");
        cooker.setSalary(8000);
        System.out.println(cooker.getId() + " " + cooker.getName() + " " + cooker.getSalary());
        cooker.work();
        cooker.eat();
    }
}
```



运行结果：

```
heima001 zhangsan 15000 8000.0
管理其他人
吃米饭
heima001 lisi 8000
炒菜
吃米饭
```



## 三、多态

### 一、多态的应用场景

比如学生管理系统或者教务管理系统，这些系统需要注册才能使用，那么需要注册使用系统的有学生、老师、管理员等，那么注册方法的形参到底应该是什么类型的呢？学生？老师？管理员？还是应该为每个对象都写一个注册方法？都不是！我们只需要写一个注册方法就可以，然后把形参的类型设置为所有需要当作参数传递进来的对象的父类即可。

![image-20250709105732987](img/image-20250709105732987.png)

### 二、认识多态

#### 一、什么是多态

**多态就是同类型对象表现出来的不同形态。**下图的前提条件：Student类继承于Person类。下图中的student对象可以有两种形态，一种学生形态，一种人的形态。

![image-20250709111219268](img/image-20250709111219268.png)

#### 二、多态的表现形式

![image-20250709111502192](img/image-20250709111502192.png)

#### 三、多态的前提

- 有**继承/实现**关系
- 有父类引用指向子类对象
- 有方法重写（方法重写是必要前题吗？我验证好像不是，如果在子类中没有重写父类的方法，那在多态的时候调用的就是父类的方法。）

#### 五、多态的好处

使用父类型作为参数，可以接收所有子类对象，体现了多态的扩展性与便利。

### 三、多态中调用成员的特点

![image-20250709145357133](img/image-20250709145357133.png)

#### 多态调用成员的内存图解

**多态调用成员变量：**编译看左边，运行也看左边。编译时先看父类中是否有该成员变量，如果没有就直接报错了，标红，编译都通过不了。因为a毕竟是Animal类型的。运行时也看左边，比如下面那条打印语句，打印的就是“动物”。也可以调用父类的私有成员变量（我自己验证过）。

![image-20250709142356306](img/image-20250709142356306.png)

![image-20250709142446257](img/image-20250709142446257.png)

多态调用成员方法：编译看左边，运行看右边。编译看左边同上调用成员变量。运行看右边。**调用这种虚方法表中的方法时**，就是运行看右边，调用的是子类虚方法表中的方法。**如果调用的是父类的虚方法表外的方法**，就运行也看左边（这个我也自己验证过）验证见下方代码。

![image-20250709143207517](img/image-20250709143207517.png)



```java
class Parent {
    public static void hello() {
        System.out.println("Parent.hello");
    }
}

class Child extends Parent {
    public static void hello() {
        System.out.println("Child.hello");
    }
}

public class Demo {
    public static void main(String[] args) {
        Parent p = new Child();

        Parent.hello(); // Parent.hello
        Child.hello();  // Child.hello

        p.hello(); // ⚠️ 仍然是 Parent.hello（看“引用类型”）
    }
}
```



### 五、多态的优势

1、在多态形式下，右边对象可以实现解耦合，便于扩展和维护。

比如有一天，我不想让学生工作了，我想让老师去工作，只需要把右边红色部分换成老师对象即可，后面的代码不需要修改。

![image-20250709144705784](img/image-20250709144705784.png)

2、**定义方法的时候，使用父类型作为形参，可以接收所有子类对象，体现多态的扩展性和便利。**

### 六、多态的弊端

![image-20250709152147826](img/image-20250709152147826.png)

补充：转换的时候不能瞎转，如果转成其他类型，就会报错。所以可以在转换前先做一个判断。

![image-20250709160713518](img/image-20250709160713518.png)

JDK14新特性：把判断和强转写在一行

![image-20250709160934436](img/image-20250709160934436.png)

### 七、总结

![image-20250709161332515](img/image-20250709161332515.png)

### 八、综合练习

Animal.java

```java
package com.it.ls.polymorphismdemo5;

public class Animal {
    private int age;
    private String color;

    public Animal(){

    }
    public Animal(int age, String color) {
        this.age = age;
        this.color = color;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    public void eat(String something) {
        System.out.println("动物在吃" + something);
    }
}
```



Dog.java

```java
package com.it.ls.polymorphismdemo5;

public class Dog extends Animal {
    public Dog() {}
    public Dog(int age, String color) {
        super(age, color);
    }

    @Override
    public void eat(String something) {
        System.out.println(getAge() + "岁的"+getColor()+"颜色的狗两只前腿死死的抱住" + something + "猛吃");
    }
    public void lookHome(){
        System.out.println("狗在看家");
    }
}
```





Cat.java

```java
package com.it.ls.polymorphismdemo5;

public class Cat extends Animal {
    public Cat(){

    }
    public Cat(int name, String color){
        super(name, color);
    }

    public void eat(String something){
        System.out.println(getAge() + "岁的"+ getColor() + "颜色的猫眯着眼睛侧着头吃" + something);
    }
    public  void catchMouse(){
        System.out.println("猫逮老鼠");
    }
}
```



Person.java

```java
package com.it.ls.polymorphismdemo5;

public class Person {
    private String name;
    private int age;

    public Person(){

    }
    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void keepPet(Animal animal, String something){
        if (animal instanceof Dog d){
            System.out.println("年龄为" + age + "岁的" + name + "养了一只" + animal.getColor() + "颜色的" + animal.getAge() + "岁的狗");
            animal.eat(something);
        }else if (animal instanceof Cat c){
            System.out.println("年龄为" + age + "岁的" + name + "养了一只" + animal.getColor() + "颜色的" + animal.getAge() + "岁的猫");
            animal.eat(something);
        }else {
            System.out.println("没有这种动物");
        }


    }
}
```



Test.java

```java
package com.it.ls.polymorphismdemo5;

public class Test {
    public static void main(String[] args) {
        Person person = new Person("老王", 30);
        Dog dog = new Dog(2, "黑");
        Cat cat = new Cat(3, "灰");
        person.keepPet(dog, "骨头");
        person.keepPet(cat, "鱼");
    }
}
```



## 五、包和final

### 一、包

#### 一、什么是包

包就是文件夹，用来管理各种不同功能的java类，方便后期代码维护。

##### 包名的规则：

公司域名反写+包的作用，**需要全部英文小写**，见名知意。

![image-20250709201643708](img/image-20250709201643708.png)

#### 二、使用其他类的规则

![image-20250709203158469](img/image-20250709203158469.png)

### 二、final

![image-20250709205650905](img/image-20250709205650905.png)

当想通过方法定义一种规则，且不希望这个规则被 改变时，就可以把这个方法用final修饰。**前两种用法我们不常用，就是在看一些源码的时候可能会看到，所以了解一下就行了**。

#### 常量

![image-20250709210156383](img/image-20250709210156383.png)

## 六、权限修饰符和代码块

### 一、权限修饰符

权限修饰符：是用来控制一个成员能够被访问（能够通过对象.成员名的方式调用的）的范围。

#### 一、权限修饰符的分类

![image-20250710093215649](img/image-20250710093215649.png)

#### 二、权限修饰符的使用规则

![image-20250710093323893](img/image-20250710093323893.png)

### 二、代码块

#### 一、局部代码块

局部代码块的作用就是为了提前结束变量的生命周期，**因为变量只在它所在的大括号里有效**。这是当时硬件不发达的时候为了节省内存而设计的。**现在已经不用了**。

#### 二、构造代码块

1、写在成员位置的代码块

2、作用：可以把多个构造方法中重复的代码抽取出来

3、执行时机：我们在创建本类对象的时候会先执行构造代码块再执行构造方法

**这种方法现在也不常用了**，因为不够灵活，如果想要将构造方法中重复的代码抽取出来，现在常用的是俩种方法：（1）将重复的代码写到一个构造方法中，在其他构造方法中通过this关键字调用这个构造方法。（2）将重复的代码提取成一个方法，在构造方法中调用这个方法。

![image-20250710101402037](img/image-20250710101402037.png)

#### 三、静态代码块

![image-20250710104547977](img/image-20250710104547977.png)

## 七、抽象类和抽象方法

### 一、抽象方法和抽象类

**抽象方法：**

将共性的行为（方法）抽取到父类之后，由于每一个子类执行的内容是不一样的，**所以在父类中不能确定具体的方法体**，该方法就可以定义为抽象方法。

**抽象方法子类必须强制重写，否则子类会报错。**

**抽象类：**

如果一个类中存在抽象方法，那么这个类就必须声明为抽象类

### 二、抽象类和抽象方法的定义格式

![image-20250710110246394](img/image-20250710110246394.png)

### 三、抽象类和抽象方法的注意事项

1、抽象类**不能实例化**

2、抽象类中不一定有抽象方法，但是有抽象方法的类一定是抽象类。

3、可以有构造方法（**可以有构造方法的目的是，子类可以通过构造方法给父类中私有的局部变量赋值。**）**作用**：当创建子类对象时给属性赋值的。你想，抽象类是不是也是一个父类啊，既然是一个父类它就要把所有子类共有的属性都抽取上来，那么当我们创建子类对象的时候，如何给这些共有的属性进行赋值呢？是不是就是通过父类的构造方法进行赋值啊？是的！

Person.java

```java
package com.it.ls.abstractdemo1;

public abstract class Person {
    private String name;
    private int age;

    public Person(){}
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public abstract void work();
}
```



Student.java

```java
package com.it.ls.abstractdemo1;

public class Student extends Person {
    public Student() {
    }

    public Student(String name, int age) {
        super(name, age);
    }

    @Override
    public void work() {
        System.out.println("学生的工作是学习");
    }
}
```



Test.java

```java
package com.it.ls.abstractdemo1;

public class Test {
    public static void main(String[] args) {
        Student s1 = new Student("张三", 23);
        System.out.println(s1.getName() + " " + s1.getAge());
    }
}
```



5、抽象类的子类

要么重写抽象父类中的所有抽象方法（常用）

要么自己也定义为抽象类

### 五、编写带有抽象类的标准JavaBean类

Animal.java

```java
package com.it.ls.abstractdemo2;

public abstract class Animal {
    private String name;
    private int age;

    public Animal(){

    }
    public Animal(String name, int age){
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public abstract void eat();
    public void drink(){
        System.out.println("喝水");
    }
}
```



Dog.java

```java
package com.it.ls.abstractdemo2;

public class Dog extends Animal {
    public Dog() {
    }

    public Dog(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("狗在吃骨头");
    }
}
```



Frog.java

```java
package com.it.ls.abstractdemo2;

public class Frog extends Animal {

    public Frog() {
    }

    public Frog(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("青蛙在吃虫子");
    }
}
```



Sheep.java

```java
package com.it.ls.abstractdemo2;

public class Sheep extends Animal {
    public Sheep() {
    }

    public Sheep(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("羊在吃草");
    }
}
```



Test.java

```java
package com.it.ls.abstractdemo2;

public class Test {
    public static void main(String[] args) {
        Frog f = new Frog("小绿", 1);
        System.out.println(f.getName() + " " + f.getAge());
        f.eat();
        f.drink();
    }
}
```



## 八、接口

接口就是一种规则。接口不代表一类事物，接口就是一种**规则**，是对**行为**的抽象。

### 一、接口的定义和使用

![image-20250710152431226](img/image-20250710152431226.png)

- 接口的子类（实现类）

​	**要么重写接口中的所有抽象方法**

​	要么是抽象类

![image-20250710153840367](img/image-20250710153840367.png)

### 二、接口中成员的特点

![image-20250710154649687](img/image-20250710154649687.png)

为什么成员变量只能是常量？因为接口代表一种规则，规则是不能改变的。

### 三、接口和类之间的关系

- 类和类的关系

​		**继承关系**，只能单继承，**不能多继承**，但可以多层继承。

- 类和接口的关系

​		实现关系，可以单实现，也**可以多实现**，还可以在继承一个类的时候实现多个接口。实现多个接口必须实现这些接口中所有的抽		象方法。如果实现的不同接口中有重名的抽象方法，只需重写一次就可以了。

- 接口和接口的关系

​		继承关系，可以单继承也**可以多继承**。如果实现类，实现的是最低层的子接口，那么该实现类就需要重写这个继承体系中所有的抽象方法。

### 五、编写带有接口和抽象类的标准JavaBean类

看JavaStudy项目中的interfacedemo5包中的代码。

### 六、JDK8开始接口中新增的方法

**JDK7以前**：接口中只能定义抽象方法

**JDK8的新特性**：接口中可以定义有方法体的方法。（默认、静态）

**JDK9的新特性**：接口中可以定义私有方法。

#### Java为什么要设计在接口中写有方法体的方法

在接口中写有方法体的方法，**是在接口升级时为了兼容性而使用的**。

#### 什么是接口升级

接口升级就是，比如一个团队开发了一个应用1.0版本，上线后一段时间，该团队决定升级这个程序，升级成2.0版本，需要对一些接口进行丰富，加入几个新的方法，此时就可以使用有方法体的方法了，**这样实现类就不需要立马修改了，等以后用到某个规则了，再重写就行了。**

#### 一、新增的默认方法

- 允许在接口中定义**默认方法**，需要使用关键字default修饰。

​	**作用：解决接口升级的问题**

![image-20250713132424390](img/image-20250713132424390.png)

**接口中默认方法的注意事项：**

- **默认方法不是抽象方法**，**所以不强制被重写**。但是如果被重写，**重写的时候去掉defaul关键字**。
- public可以省略，defaul不能省略。因为public是默认就有的。
- 如果实现了多个接口，多个接口中存在相同名字的默认方法，**子类就必须对该方法进行重写**。

#### 二、新增的静态方法

- 允许在接口中定义**静态方法**，需要用static修饰。

![image-20250713133529758](img/image-20250713133529758.png)

**接口中静态方法的注意事项**

**静态方法只能通过接口名调用**，不能通过实现类名或对象名调用。**因为**：接口的 static 方法不会被实现类继承。

public可以省略，static不能省略。因为public是默认就有的。

**静态方法不能重写**，因为，重写指的是子类覆盖了从父类继承下来的虚方法表中的方法，而static修饰的方法压根就不能写到虚方法表中，所以它也就不能被重写。

### 七、JDK9新增的方法--私有方法

默认方法和静态方法中有一些重复的代码，将这些重复的代码提取到私有方法中，此方法中的代码**只为接口本身提供服务**，不需要被外类访问，所以定义为私有方法。

#### 一、接口中私有方法的定义格式

![image-20250713135132996](img/image-20250713135132996.png)

这种私有方法，是为默认方法服务的。

![image-20250713135156384](img/image-20250713135156384.png)

这种私有方法是为静态方法服务的。

### 八、接口的应用

#### 一、接口是行为的规则

把接口理解成各种各样**行为的规则**，想让Java拥有什么样的行为，就实现对应的接口就可以了。

#### 二、接口的多态

当一个方法的形参是一个接口时，那这个方法就可以接收这个接口的所有实现类的对象，就相当于：接口类型 j = new 实现类对象（）;在运行的时候也会遵守，编译看左边，运行看右边的规则。

![image-20250713143453279](img/image-20250713143453279.png)

### 九、适配器设计模式

![image-20250713144441356](img/image-20250713144441356.png)

## 十一、内部类

### 一、什么是内部类

类的五大成员：属性、方法、构造方法、内部类、代码块

![image-20250713152147518](img/image-20250713152147518.png)

### 二、为什么要学习内部类

![image-20250713152414213](img/image-20250713152414213.png)

![image-20250713203212421](img/image-20250713203212421.png)

![image-20250713204637256](img/image-20250713204637256.png)

### 三、内部类的分类

成员内部类、静态内部类、局部内部类、匿名内部类

### 五、成员内部类

#### 一、成员内部类的代码如何书写

![image-20250713160148944](img/image-20250713160148944.png)

#### 二、如何获取成员内部类的对象

方式一：在外部类中编写方法，对外提供内部类的对象。（当内部类被private修饰时）

方式二：

![image-20250713192331066](img/image-20250713192331066.png)

![image-20250713202534502](img/image-20250713202534502.png)

#### 三、成员内部类如何获取外部类的成员变量

![image-20250713213056419](img/image-20250713213056419.png)

##### 内部类的内存图

在内存中，外部类和内部类是两个独立的字节码文件。内部类的对象中除了自己本身的成员变量外，还有一个**隐藏的成员变量this**，它**记录着外部类对象的地址值**。

![image-20250713210648909](img/image-20250713210648909.png)

### 六、静态内部类

静态内部类是一种**特殊**的成员内部类。

如果想要在静态内部类中访问外部类中的非静态的成员，需要创建对象，就像要想在main方法中访问非静态的东西需要先创建对象，通过实例化对象访问。

![image-20250714093021966](img/image-20250714093021966.png)

![image-20250714093158910](img/image-20250714093158910.png)

![image-20250714093313725](img/image-20250714093313725.png)

### 七、局部内部类

1、**将内部类定义在方法里面**就叫做局部内部类，类似于方法里面的局部变量。

2、**外界是无法使用的**，要使用就在方法内部创建对象并使用。

3、该类可以直接访问外部类的成员，也可以访问方法内的局部变量。

### 八、匿名内部类

![image-20250714115655805](img/image-20250714115655805.png)

Animal.java

```java
package com.it.ls.anonymityinnerclassdemo;

public abstract class Animal {
    public abstract void eat();
    public void drink(){
        System.out.println("动物喝水");
    }
}
```



Test.java

```java
package com.it.ls.anonymityinnerclassdemo;

public class Test {
    public static void main(String[] args) {
        method(
            //下面这个整体：
                //整体不是匿名内部类，整体是匿名内部类的对象
                //花括号以及花括号中的内容组成了匿名内部类
                //下面这段代码创建了匿名内部类的对象
                //匿名内部类继承了Animal类。
                // 因为Animal是抽象类，所以匿名内部类中重写了其的抽象方法。
                new Animal(){
                    @Override
                    public void eat() {
                        System.out.println("狗吃骨头");
                    }
                }

        );

    }
    public static void method(Animal animal) {
        //上面main方法中采用匿名内部类的方式传参，匿名内部类是Animal的子类
        //所以就形成了Animal animal = 子类对象 形成了多态
        //所以下面这句代码是编译看左边，运行看右边
        animal.eat();
        animal.drink();
    }
}
```



Swim.java（接口）

```java
package com.it.ls.anonymityinnerclassdemo;

public interface Swim {
    public abstract void swim();
}
```



Test2.java

```java
package com.it.ls.anonymityinnerclassdemo;

public class Test2 {
    public static void main(String[] args) {
        //整体我们可以理解为Swim接口的实现类对象
        //接口多态
        Swim swim = new Swim(){
            @Override
            public void swim() {
                System.out.println("重写之后的游泳方法");
            }
        };
        //编译看左边，运行看右边
        swim.swim();

        new Swim(){
            @Override
            public void swim() {
                System.out.println("重写之后的游泳方法");
            }
        }.swim();
    }
}
```

![image-20250714144720217](img/image-20250714144720217.png)

# 十三、常用API

## 一、Math

- 是一个帮助我们用于数学计算的工具类
- **私有化构造方法，所有的方法都是静态的**

### Math类的常用方法

![image-20250731151406809](img/image-20250731151406809.png)

## 二、System

System也是一个工具类，提供了一些与系统相关的方法

![image-20250731152947330](img/image-20250731152947330.png)

## 三、Runtime

表示当前虚拟机的运行环境。

![image-20250731172342074](img/image-20250731172342074.png)

## 五、Object

Object是java中的顶级父类，所有的类都直接或间接的继承于Object类。

Object类中的方法可以被所有子类访问，所以我们要学习Object类和其中的方法。

### 一、Object的构造方法

![image-20250731174918502](img/image-20250731174918502.png)

### 二、Object的成员方法

#### 一、toString方法

1、**默认情况下**，Object类中的toString方法返回的是**地址值**。

2、`System.out.println()`通过这个语句打印一个对象的时候，默认会调用这个对象的toString方法，把对象变成字符串，然后再打印到控制台上。打印完毕，换行处理。因为**默认情况下**，Object类中的toString方法返回的是**地址值**。 所以**默认情况下**，**打印一个对象打印的就是地址值**。

3、但是一般情况下，地址值对我们是没有意义的，我们想要看到的是对象中的属性值，此时我们需要重写Object类中的toString方法，在重写的方法中，把对象的属性进行拼接即可。

#### 二、equals方法

![image-20250731191923502](img/image-20250731191923502.png)

1、默认情况下，Object类的equals方法比较的是两个对象的**地址值是否相同**。

2、可以重写Object类的equals方法，比较对象内部的属性值。

#### 三、Clone方法

1、**Cloneable**：如果一个接口里面没有抽象方法，表示当前的接口是一个**标记性接口**。一旦实现了Cloneable接口，就表示当前类的对象可以被克隆。如果没有实现，那么当前类的对象不能克隆。

2、Obiect类中的clone方法是用protected修饰符修饰的。所以只能在Object类所在包或其他包的子类中使用。所以我们要想在其他地方使用clone方法，需要在自己定义的类中重写clone方法。

3、细节

​	（1）在javabean类中重写Object类中的clone方法

​	（2）让javabean类实现Cloneable接口

​	（3）创建原对象并调用clone方法即可。

5、对象克隆

![image-20250801215424797](img/image-20250801215424797.png)

6、第三方深克隆工具

**gson**

![image-20250801220024711](img/image-20250801220024711.png)

## 六、Objects

是一个工具类，提供了一些操作对象的方法去完成一些功能。

1、Objects的成员方法

![image-20250802102142557](img/image-20250802102142557.png)

## 七、BigInteger

### 一、BigInteger的构造方法

![](img/image-20250802110703393.png)

1、`public static BigInteger valueOf(long val)`细节

​	![image-20250802112707859](img/image-20250802112707859.png)

2、对象一旦创建，里面的数据不能发生改变。只要进行计算，就会产生一个新的BigInteger对象。除了用max和min方法比较大小的时候不会创建新的对象，因为它就是把两个数中较大的数返回了而已。

![image-20250802113016600](img/image-20250802113016600.png)

### 二、BigInteger中的常见方法

BigInteger是一个对象，那 它就不能直接进行加减乘除、比较大小等操作，这些操作都得用方法去操作。

![image-20250802113306983](img/image-20250802113306983.png)

### 三、BigInteger底层存储方式

将长整数先转换为2进制，然后再将转换后的2进制数每32位分一组。

![image-20250802155421148](img/image-20250802155421148.png)

五、BigInteger的存储上限

![image-20250802155558584](img/image-20250802155558584.png)

## 八、BigDecimal

### 一、计算机中的小数

![image-20250802160034150](img/image-20250802160034150.png)

### 二、BigDecimal的作用

用于小数的精确计算

用来表示很大的小数

### 三、BigDecimal的构造方法

![image-20250802204414714](img/image-20250802204414714.png)

### 五、BigDecimal中的常见方法

![image-20250802210611267](img/image-20250802210611267.png)

### 六、BigDecimal底层存储方式

不管是通过传递字符串表示的小数，还是通过静态方法创建BigDecimal对象，其底层都是通过传递字符串表示的小数的方式new出来的。

![image-20250802211054272](img/image-20250802211054272.png)

数组中存储的是符号的ASCCL码。

![image-20250802211222492](img/image-20250802211222492.png)

## 九、正则表达式

### 一、正则表达式的作用

![image-20250805203832059](img/image-20250805203832059.png)

### 二、正则表达式的内容

![image-20250805205320421](img/image-20250805205320421.png)

![image-20250805204012221](img/image-20250805204012221.png)

### 三、正则表达式基本练习

```java
package com.it.ls.regexdome;

public class RegexDemo4 {
    public static void main(String[] args) {
        String regex1 = "1[3-9]\\d{9}";
        System.out.println("13112365678".matches(regex1));
        System.out.println("13712365667".matches(regex1));
        System.out.println("13965679077".matches(regex1));
        System.out.println("139656790271".matches(regex1));
        System.out.println("-----------------------------------------");

        String regex2 = "0\\d{2,3}-?[1-9]\\d{4,9}";
        System.out.println("020-7376767".matches(regex2));
        System.out.println("02177667".matches(regex2));
        System.out.println("027-67676".matches(regex2));
        System.out.println("0712-3676736".matches(regex2));
        System.out.println("-----------------------------------------");

        String regex3 = "\\w+@[\\w&&[^_]]{2,6}(\\.[a-zA-Z]{2,3}){1,2}";
        //()是分组的意思
        System.out.println("3636363@qq.com".matches(regex3));
        System.out.println("zhangsan@itcast.cnn".matches(regex3));
        System.out.println("dlei0009@163.com".matches(regex3));
        System.out.println("dlei0009@pci.com.cn".matches(regex3));
    }
}
```

### 五、忽略大小写的匹配方式

![image-20250806170104174](img/image-20250806170104174.png)

### 六、正则表达式小结

![image-20250806171046565](img/image-20250806171046565.png)

![image-20250806171110446](img/image-20250806171110446.png)

## 十、JDK7以前时间相关的类

### 一、时间的相关知识点

![image-20250806204059420](img/image-20250806204059420.png)

### 二、Data时间类

![image-20250806204853720](img/image-20250806204853720.png)

![image-20250806205455791](img/image-20250806205455791.png)

### 三、SimpleDateFormat类

#### 一、SimpleDateFormat类的作用

![image-20250806222412986](img/image-20250806222412986.png)

#### 二、SimpleDateFormat类

![image-20250806224421372](img/image-20250806224421372.png)

### 五、Calendar类

#### 一、Calender类概述

Calender代表了系统当前时间的日历对象，可以单独修改、获取时间中的年、月、日

**细节**：Calender是一个抽象类，不能直接创建对象。

#### 二、获取Calender日历对象的方法

该方法获取Calender子类对象

![image-20250807170333993](img/image-20250807170333993.png)

#### 三、Calender常用方法

![image-20250807170417258](img/image-20250807170417258.png)

![image-20250808163742506](img/image-20250808163742506.png)

![image-20250808163816698](img/image-20250808163816698.png)

![image-20250808165528962](img/image-20250808165528962.png)

#### 五、总结

![image-20250808165713682](img/image-20250808165713682.png)

## 十一、JDK8新增的时间相关类

### 一、为什么要学JDK8新增的时间相关类

![image-20250808170519397](img/image-20250808170519397.png)

### 二、JDK8时间类

![image-20250810094340621](img/image-20250810094340621.png)

#### 一、ZoneId时区

![image-20250810094509590](img/image-20250810094509590.png)

![image-20250810094835187](img/image-20250810094835187.png)

#### 二、Instant时间戳

![image-20250810100743387](img/image-20250810100743387.png)



```java
package com.it.ls.jdk8datetime;

import java.time.Instant;
import java.time.ZoneId;
import java.time.ZonedDateTime;

public class InstantDemo {
    public static void main(String[] args) {
        //获取当前时间的Instant对象（标准时间）
        Instant instant = Instant.now();
        System.out.println(instant);

        //根据（秒/毫秒/纳秒）获取Instant对象
        Instant instant1 = Instant.ofEpochMilli(0L);
        System.out.println(instant1);
        Instant instant2 = Instant.ofEpochSecond(1L);
        System.out.println(instant2);
        Instant instant3 = Instant.ofEpochSecond(1L, 1000000000L);
        System.out.println(instant3);

        //指定时区，获取带有时区的时间对象
        Instant instant5 = Instant.now();
        ZonedDateTime zonedDateTime = instant5.atZone(ZoneId.of("Asia/Shanghai"));
        System.out.println(zonedDateTime);

        //isXxx 判断
        Instant instant6 = Instant.ofEpochMilli(0L);
        Instant instant7 = Instant.ofEpochMilli(1000L);
        boolean result = instant6.isBefore(instant7);
        System.out.println(result);
        boolean result1 = instant7.isBefore(instant6);
        System.out.println(result1);

        //减少时间系列的方法
        Instant instant8 = Instant.ofEpochMilli(3000L);
        System.out.println(instant8);
        Instant instant9 = instant8.minusSeconds(1L);
        System.out.println(instant9);
    }
}
```



#### 三、ZoneDataTime带时区的时间

![image-20250811102804397](img/image-20250811102804397.png)



```java
package com.it.ls.jdk8datetime;

import java.time.Instant;
import java.time.ZoneId;
import java.time.ZonedDateTime;

public class ZoneIdDateTimeDemo {
    public static void main(String[] args) {
        //1、获取当前时间对象（带时区）
        ZonedDateTime zonedDateTime = ZonedDateTime.now();
        System.out.println(zonedDateTime);
        //2、获取指定的时间对象（带时区）
        ZonedDateTime zonedDateTime1 = ZonedDateTime.of(2023, 10, 1, 11, 11, 12, 0, ZoneId.of("Asia/Shanghai"));
        System.out.println(zonedDateTime1);

        //3、通过Instant + 时区的方式指定获取时间对象
        Instant instant = Instant.ofEpochMilli(0L);
        ZoneId zoneId = ZoneId.of("Asia/Shanghai");
        ZonedDateTime zonedDateTime2 = ZonedDateTime.ofInstant(instant, zoneId);
        System.out.println(zonedDateTime2);

        //3、withXxx修改时间系列的方法
        ZonedDateTime zonedDateTime3 = zonedDateTime2.withYear(2000);
        System.out.println(zonedDateTime3);

        //5、减少时间
        ZonedDateTime zonedDateTime4 = zonedDateTime3.minusYears(1L);
        System.out.println(zonedDateTime4);

        //4、增加时间
        ZonedDateTime zonedDateTime5 = zonedDateTime4.plusYears(1L);
        System.out.println(zonedDateTime5);

    }
}
```



**细节：**

![image-20250811114118776](img/image-20250811114118776.png)

#### 五、DateTimeFormatter用于时间的格式化解析

![image-20250811114351213](img/image-20250811114351213.png)

```java
package com.it.ls.jdk8datetime;

import java.time.Instant;
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;

public class DateTimeFormatterDemo {
    public static void main(String[] args) {
        ZonedDateTime zdt = ZonedDateTime.now();
        ZonedDateTime zonedDateTime = Instant.now().atZone(ZoneId.of("Asia/Shanghai"));
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss EE a");
        System.out.println(formatter.format(zdt));
    }
}
```



#### 六、LocalDate、LocalTime、LocalDateTime

![image-20250811154457511](img/image-20250811154457511.png)

LocalDateTime还可以转成LocalDate和LocalTime

![image-20250811154654643](img/image-20250811154654643.png)

#### 七、Duration、Period、ChronoUnit

![image-20250811160301606](img/image-20250811160301606.png)

![image-20250811161009147](img/image-20250811161009147.png)

![image-20250811161200180](img/image-20250811161200180.png)

![image-20250811161351878](img/image-20250811161351878.png)

JDK8中有一个判断是不是闰年的方法

![image-20250812100255912](img/image-20250812100255912.png)

## 十二、包装类

### 一、什么是包装类

就是基本数据类型对应的引用数据类型。

### 二、如何理解包装类

![image-20250811165258268](img/image-20250811165258268.png)

### 三、为什么要有包装类

1、在java中万物皆对象，java的多态机制可以让任何对象都可以通过Object类的对象接收，如果没有包装类，那么对于整数这些基本数据类型的使用就会有局限性。

2、java中集合中不能装基本数据类型。

### 五、获取Integer对象的方式

#### 一、JDK5以前

![image-20250811173430045](img/image-20250811173430045.png)

#### 二、面试题

以上这两种获取Integer对象的方法的区别：

通过构造方法的方式，new出来的Integer对象，及时它们代表的数值是一样的，但它们也不是同一个对象，因为每一次new都是创建了一个新的对象。

通过静态方法valueOf()创建的对象，如果对象代表的值的范围在**-128到127之间**，那么两个值相同的Integer对象**是同一个对象**。因为在我们的开发中-128到127之间的数据是**比较常用**的，**为了节约资源**，Integer底层将-128到127之间的每一个数据对应的Integer对象都提前创建好了，存放在一个数组中，用到这些数据的时候valueOf()直接从这个数组中取出数据返回，**不需要再创建新的对象了**。

#### 三、JDK5提出的自动装箱和自动拆箱机制

所谓自动就是不需要你自己去写了java会自动帮你完成

自动装箱：把基本数据类型自动变成其对应的包装类。

自动拆箱：把包装类自动变成其对应的基本数据类型。

在JDK5之后，int和Integer可以看成是一个东西，因为在内部可以自己转换。

![image-20250811181119021](img/image-20250811181119021.png)

JDK5之后获取包装类对象直接赋值就行了。

### 六、Integer成员方法

![image-20250811182217822](img/image-20250811182217822.png)

**细节：**

1、8种包装类中，除了Character外都有对应的parseXxx方法，进行类型转换。

2、键盘录入弊端，当我们在使用nextInt、next、nextDouble的时候，这些方法在遇到空格、回车、制表符的时候就会停止，导致空格、回车、制表符后面的内容无法录入。如果想要接收一整行数据，知道遇到回车才停止，遇到空格、制表符不停止，那么就使用nextLine（）方法。**约定，以后不管想要接收什么类型的数据，都使用nextLine()，后面再使用包装类的parseXxx()这类方法转换就行**。

# 十五、常见算法

## 一、查找算法

### （一）基本查找

从0索引开始挨个往后查找

### （二）二分查找/折半查找

**前提条件**：数组中的数据必须是有序的。

**核心逻辑**：每次排除一半的查找范围

![image-20250812105215990](img/image-20250812105215990.png)

**小结：**

![image-20250812113240134](img/image-20250812113240134.png)



```java
package com.it.ls.search;

public class BinarySearchDemo {
    public static void main(String[] args) {
        int[] arr = {7, 23, 79, 81, 103, 127, 131, 147};
        int index = binarySearch(arr, 150);
        System.out.println(index);

    }
    public static int binarySearch(int[] arr, int target) {
        int min = 0;
        int max = arr.length - 1;
        while (min <= max) {
            int mid = (min + max) / 2;
            if (arr[mid] > target) {
                max = mid - 1;
            }else if (arr[mid] < target) {
                min = mid + 1;
            } else if (arr[mid] == target) {
                return mid;
            }
        }
        return -1;
    }
}
```



**二分查找改进：**

（1）插值查找

![image-20250812113929040](img/image-20250812113929040.png)

（2）斐波那契查找

![image-20250812114120519](img/image-20250812114120519.png)



### （三）分块查找

分块的原则1：前一块中的最大数据，要小于后一块中的所有数据。**（块内无序，块间有序）**

分块的原则2：**块的数量一般等于数字的个数开根号**。比如16个数字一般分为4块左右。

核心思路：**先确定要查找的元素在哪一块，然后在块内挨个查找**。

```java
package com.it.ls.search;

public class BlockSearchDemo {
    public static void main(String[] args) {

        //实现步骤
        //1、创建数组blocks存储每一块的数据
        //2、判断所要找的数据可能在哪一块
        //3、再到数据所在块挨个查找

        int[] arr = {16, 5, 9, 12, 21, 18,
                     32, 23, 37, 26, 45, 34,
                     50, 48, 61, 52, 73, 66};

        //创建三个块的对象
        Block b1 = new Block(21, 0, 5);
        Block b2 = new Block(45, 6, 11);
        Block b3 = new Block(73, 12, 17);

        //定义数组用来管理三个块的对象
        Block[] blocks = {b1, b2, b3};

        //定义一个变量用来记录要查找的数据
        int number = 37;

        //调用方法，传递索引表、数组、要查找的数据
        int index = getIndex(blocks, arr, number);
        System.out.println(index);
    }
    private static int getIndex(Block[] blocks, int[] arr, int number) {
        int indexBlock = findIndexBlock(blocks, number);

        if (indexBlock == -1) {
            return -1;
        }

        int startIndex = blocks[indexBlock].getStartIndex();
        int endIndex = blocks[indexBlock].getEndIndex();
        for (int i = startIndex; i <= endIndex; i++) {
            if (arr[i] == number) {
                return i;
            }
        }
        return -1;
    }
    private static int findIndexBlock(Block[] blocks, int number) {
        for (int i = 0; i < blocks.length; i++) {
            if (number <= blocks[i].getMax()){
                return i;
            }
        }
        return -1;
    }
}

class Block {
    private int max;
    private int startIndex;
    private int endIndex;

    public Block() {
    }
    public Block(int max, int startIndex, int endIndex) {
        this.max = max;
        this.startIndex = startIndex;
        this.endIndex = endIndex;
    }

    public int getMax() {
        return max;
    }

    public void setMax(int max) {
        this.max = max;
    }

    public int getStartIndex() {
        return startIndex;
    }

    public void setStartIndex(int startIndex) {
        this.startIndex = startIndex;
    }

    public int getEndIndex() {
        return endIndex;
    }

    public void setEndIndex(int endIndex) {
        this.endIndex = endIndex;
    }
}
```



扩展的分块查找：

当碰到无规律的数据时，分块的话，要使得分好的每一块的数据的范围没有交集。

![image-20250812160414989](img/image-20250812160414989.png)



```java
package com.it.ls.search;

public class BlockSearchDemo1 {
    public static void main(String[] args) {
        int[] arr = {
                27, 22, 30, 40, 36,
                13, 19, 16, 20,
                7, 10,
                43, 50, 48
        };
        BlockPro blockPro1 = new BlockPro(22, 40, 0, 4);
        BlockPro blockPro2 = new BlockPro(13, 20, 5, 8);
        BlockPro blockPro3 = new BlockPro(7, 10, 9, 10);
        BlockPro blockPro4 = new BlockPro(43, 50, 11, 13);

        BlockPro[] blockProArray = {blockPro1, blockPro2, blockPro3, blockPro4};

        int number = 16;
        int index = getIndex(blockProArray, arr, number);
        System.out.println(index);

    }
    private static int getIndex(BlockPro[] blockProArray, int[] arr, int number) {
        int indexBlock = findIndexBlock(blockProArray, number);
        if (indexBlock == -1) {
            return -1;
        }

        int startIndex = blockProArray[indexBlock].getStartIndex();
        int endIndex = blockProArray[indexBlock].getEndIndex();
        for (int i = startIndex; i <= endIndex; i++) {
            if (arr[i] == number) {
                return i;
            }
        }
        return -1;
    }
    private static int findIndexBlock(BlockPro[] blockProArray, int number) {
        for (int i = 0; i < blockProArray.length; i++) {
            if (number <= blockProArray[i].getMax() && number >= blockProArray[i].getMin()) {
                return i;
            }
        }
        return -1;
    }
}

class BlockPro {
    private int min;
    private int max;
    private int startIndex;
    private int endIndex;

    public BlockPro() {
    }
    public BlockPro(int min, int max, int startIndex, int endIndex) {
        this.min = min;
        this.max = max;
        this.startIndex = startIndex;
        this.endIndex = endIndex;
    }

    public int getMin() {
        return min;
    }

    public void setMin(int min) {
        this.min = min;
    }

    public int getMax() {
        return max;
    }

    public void setMax(int max) {
        this.max = max;
    }

    public int getStartIndex() {
        return startIndex;
    }

    public void setStartIndex(int startIndex) {
        this.startIndex = startIndex;
    }

    public int getEndIndex() {
        return endIndex;
    }

    public void setEndIndex(int endIndex) {
        this.endIndex = endIndex;
    }
}
```



### （四）插值查找

### （五）斐波那契查找

### （六）树表查找

### （七）哈希查找

### （八）二分查找、插值查找、斐波那契查找各自的特点

![image-20250812114350976](img/image-20250812114350976.png)

## 二、排序算法

### （一）冒泡排序

**思想**：相邻的元素两两比较，小的放在前面，大的放在后面。

**记住**：第一轮比较完毕后，最大值已经在最后面了，第二轮可以少循环一次，第二轮比较完毕后次大值已经在倒数第二个位置了。后面以此类推。所以如果数组中有n个数据，那么就执行n-1轮的代码就可以。

![image-20250812170203317](img/image-20250812170203317.png)



```java
package com.it.ls.mysort;

public class BubbleDemo1 {
    public static void main(String[] args) {
        //1、定义数组
        int[] arr = {2, 4, 5, 3, 1};

        //外循环：表示我要执行多少轮。如果有n个数据那么执行n-1轮
        for (int i = 0; i < arr.length - 1; i++) {
            //内循环：每一轮中我如何比较数据，并找到当前的最大值。
            //-1 为了防止索引越界
            //-i：提高效率，每一轮执行的次数应该比上一轮少一次。
            for (int j = 0; j < arr.length - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]);
        }
    }
}
```



### （二）选择排序

**核心思想**：从0索引开始，拿着每一个索引上的元素跟后面的元素依次比较，小的放前面，大的放后面，以此类推。

![image-20250812172637803](img/image-20250812172637803.png)



```java
package com.it.ls.mysort;

public class SelectionDemo {
    public static void main(String[] args) {
        int[] arr = {2, 4, 5, 3, 1};
        //外循环：要执行几轮
        //其中的i表示这一轮中，要拿着哪个索引上的数据与后面的数据进行比较并交换
        for (int i = 0; i < arr.length - 1; i++) {
            //内循环：每一轮拿着i和i后面的数据进行比较交换
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] > arr[j]) {
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }
    }
}
```



### （三）插入排序

**核心思想：**将0索引的元素到N索引的元素看作是有序的，把N+1索引的元素到最后一个看作是无序的。遍历无序的数据，将遍历到的元素插入有序序列中适当的位置，如遇到相同的数据，插在后面。

```java
package com.it.ls.search;

public class InsertDemo {
    public static void main(String[] args) {
        int[] arr = {3, 44, 38, 5, 47, 15, 36, 26, 27, 2, 46, 4, 19, 50, 48};

        //1、找到无序的那一组数组是从哪个索引开始的
        int startIndex = -1;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > arr[i + 1]) {
                startIndex = i + 1;
                break;
            }
        }

        //2、遍历从startIndex开始到最后一个索引的元素，依次得到无序的那一组数据中的每一个数据
        for (int i = startIndex; i < arr.length; i++) {
            //3、将遍历到的数据插入到前面有序的那一组数据中
            int j = i;
            while (j > 0 && arr[j] < arr[j - 1]) {
                int temp = arr[j - 1];
                arr[j - 1] = arr[j];
                arr[j] = temp;
                j --;
            }
        }

        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

    }
}
```



### （四）快速排序

#### **递归算法**：

递归指的是方法中调用方法本身的现象。

**递归的注意点**：递归一定要有出口，否则就会出现内存溢出。

**递归算法的作用：**

1、把**一个复杂的问题**层层转化为一个**与原问题相似**的，**规模较小的问题**来求解。

2、递归策略只需要**少量的程序**，就可以**描述出**解题过程所需要的**多次重复计算**。

**书写递归的两个核心：**

1、**找出口**：什么时候不再调用方法

2、**找规则：**如何把大问题变成规模较小的问题。

**写递归时的小心得：**

方法内部再次调用方法的时候，参数必须要更加靠近出口。

**快速排序：**
![image-20250812192344557](img/image-20250812192344557.png)

**递归排序的时间复杂度**：

**平均情况：**O(n log n)

**最坏情况**：（如数组已排序且每次选最差基准）：O(n²)

在快速排序中，**选好基准值可以提高排序的效率**。如果**数据本来接近有序**，升序或降序，**直接选第一个或最后一个元素做基准值容易导致极度不平衡的分区**。此时可以采取“三数取中法”，这是一种**改进快速排序选基准值（pivot）**的方法，目的是避免最坏情况（如 O(n²)）的发生，提高排序的稳定性和效率。

**三数取中法核心思想**：

在每一轮分区（partition）前，

1. 从当前待排序区间**选三个数**：
   - **第一个元素**
   - **中间位置的元素**
   - **最后一个元素**
2. 比较这三个数的大小，**取它们的中位数作为基准值**（pivot）。

这样可以减少选到极端值（最大或最小值）的概率，从而让划分更平衡。

### （五）希尔排序

### （六）归并排序

### （七）堆排序

### （八）计数排序

### （九）桶排序

### （十）基数排序

### （十一）冒牌排序、插入排序、选择排序、快速排序速度对比

同为排序10万随机数

**插入排序**：2633

**选择排序**：10527

**冒泡排序**：11124

## 三、Arrays

操作数组的工具类

![image-20250817100948781](img/image-20250817100948781.png)

![image-20250817101253021](img/image-20250817101253021.png)

![image-20250817101309834](img/image-20250817101309834.png)

![image-20250817101535154](img/image-20250817101535154.png)

上面Arrays的那几条成员方法的最后一个方法，里面的第二个参数，排序规则，是一个接口，所以我们在调用这个方法的时候，需要传递这个接口的实现类对象作为排序的规则。

但这个实现类，我们只需要使用一次，所以就没有必要单独去写一个类，直接采取匿名内部类的形式就可以了。

这个方法的底层原理：

1、这个方法只能给引用数据类型的数组进行排序，如果是基本数据类型，需要变成其对应的包装类。

2、这个方法底层是利用插入排序+二分查找的方式进行排序的。默认把0索引的数据认为是有序的，1索引到最后一个索引的数据认为是无序的序列。

3、![image-20250817110859858](img/image-20250817110859858.png)

4、如果方法的返回值是**负数**，拿着A继续和前面的数据进行比较。如果方法的返回值是**正数**，则拿着A继续和后面的数据进行比较。如果方法的**返回值是0**，就把A放在插入点元素的后面。

5、compare方法的形式参数：

参数一o1：表示在无序序列中，遍历得到的每一个元素。

参数二o2：有序序列中插入点位置的元素。

![image-20250817112247103](img/image-20250817112247103.png)

# 十六、Lambda表达式

## 一、函数式编程

1、面向对象的思想其实有的时候，也是有一些小小的累赘的，我们在干一件事情之前，必须先有对象，让这个对象去干事情。但是，有的时候，其实不需要非要找到那个干活的对象，有活需要干，有东西干就行了，管它谁干呢，爱谁谁。所以这就用到了函数式编程。

2、函数式编程是一种思想特点。

3、函数式编程特点，忽略面向对象的复杂语法，更关注于方法体中的逻辑，强调做什么，而不是谁做。

5、我们现在要学的Lambda表达式就是函数式编程思想的体现。

## 二、Lambda表达式的标准格式

![image-20250817114841688](img/image-20250817114841688.png)

注意点：

1、Lambda表达式可以用来简化匿名内部类的书写

2、**Lambda表达式只能简化函数式接口的匿名内部类的书**

3、函数式接口：**有且仅有一个抽象类的接口称为函数式接口**，接口上方可以加上@FunctionalInterface注解。

LambdaDemo2

```java
package com.it.ls.lambdademo;

public class LambdaDemo2 {
    public static void main(String[] args) {
        mathed(()->{
            System.out.println("正在游泳~");
        });

    }
    public static void mathed(Swim s){
        s.swim();
    }
}

interface Swim{
    public abstract void swim();
}
```



## 三、总结

![image-20250817120347472](img/image-20250817120347472.png)

五、Lambda表达式的写法

![image-20250817150506650](img/image-20250817150506650.png)

# 正则表达式

就是由一些特定的字符组成，代表的是一个规则。 

String提供了一个匹配正则表达式的方法

public boolean matches(String regex) 判断字符串是否匹配正则表达式，匹配则返回true，不匹配返回false。

正则表达式的书写规则：

```java
public class RegexTest2 {
    public static void main(String[] args) {
        //字符类（只能匹配单个字符）
        System.out.println("a".matches("[abc]"));//true
        System.out.println("e".matches("[abcd]"));//false

        System.out.println("d".matches("[^abc]"));//true
        System.out.println("a".matches("[^abc]")); //false

        System.out.println("b".matches("[a-zA-Z]"));// true
        System.out.println("2".matches("[a-zA-Z]"));// false

        System.out.println("k".matches("[a-z&&[^bc]]"));//true
        System.out.println("b".matches("[a-z&&[^bc]]"));//false

        System.out.println("ab".matches("[a-zA-Z0-9]"));//false 以上带[内容] 的正则表达式都只能匹配单个字符

        //2.预定义字符 （只能匹配单个字符） \d \D \s \S \w \W
        System.out.println("徐".matches(".")); //可以匹配任意字符 true
        System.out.println("徐徐".matches("."));// false 只能匹配单个字符

        //在java中\是有特殊用图的，例如和字母一起组成转义字符，但是转义字符中没有\d \s等，所以需要在\前再加一个\告诉第二个\你就是一个\不要当成转义字符的组成部分。
        System.out.println("1".matches("\\d"));//true \d代表0-9之间的数字
        System.out.println("12".matches("\\d"));//false

        System.out.println(" ".matches("\\s"));//true \s代表一个空白字符
        System.out.println("a".matches("\\s"));// false

        System.out.println("a".matches("\\S"));//true \S代表非空白字符
        System.out.println(" ".matches("\\S"));// false

        System.out.println("a".matches("\\w"));// true \w代表[a-zA-Z0-9]
        System.out.println("_".matches("\\w"));//true
        System.out.println("徐".matches("\\w"));//false

        System.out.println("徐".matches("\\W"));//true \W:[^\w]
        System.out.println("a".matches("\\W"));//false

        //3.数量词：？ * + {n} {n,} {n,m}
        System.out.println("a".matches("\\w?"));//true ?代表出现0次或1次
        System.out.println("".matches("\\w?"));//true
        System.out.println("abc".matches("\\w?"));//false

        System.out.println("abc12".matches("\\w*"));//true *代表至少出现0次
        System.out.println("".matches("\\w*"));//true
        System.out.println("abc12张".matches("\\w*"));//false

        System.out.println("a".matches("\\w+"));//true +代表出现1次
        System.out.println("".matches("\\w+"));//false
        System.out.println("abc12张".matches("\\w+"));//false

        System.out.println("a3c".matches("\\w{3}"));//true {3}代表正好出现3次
        System.out.println("abcd".matches("\\w{3}"));//false
        System.out.println("abcd".matches("\\w{3,}"));//true {3,}代表至少出现三次
        System.out.println("ab".matches("\\w{3,}"));//false
        System.out.println("abcde徐".matches("\\w{3,}"));//false
        System.out.println("abc232d".matches("\\w{3,9}"));//true {3,9}代表出现3-9次

        //4.其他几个常用的符号(?i)忽略大小写
        System.out.println("abc".matches("(?i)abc"));//true (?i)忽略大小写
        System.out.println("ABC".matches("(?i)abc"));//true
        System.out.println("aBc".matches("a((?i)b)c"));//true
        System.out.println("ABc".matches("a((?i)b)c"));//false

        //需求1 要么是三个小写字母 要么是三个数字
        System.out.println("abc".matches("[a-z]{3}|\\d{3}"));// true
        System.out.println("123".matches("[a-z]{3}|\\d{3}"));//true
        System.out.println("aAc".matches("[a-z]{3}|\\d{3}"));//false

        //需求2 必须是”我爱“开头 中间可以是至少一个”编程 最后至少是一个666“
        System.out.println("我爱编程编程666666".matches("我爱(编程)+(666)+"));//true
        System.out.println("我爱编程编程6666666".matches("我爱(编程)+(666)+"));//false
    }
}
```

# 集合

## Map集合

### 1、认识map集合

map集合称为双列集合，格式：{key1=value1, key2=value2, key3=value3, ...}，一次需要存一段数据作为一个元素。

map集合的每个元素{key=value}称为一个键值对/键值对对象/entry对象，Map集合也被叫做键值对集合。

Map集合的所有键是不允许重复的，但是值可以重复，键和值是一一对应的，每一个键只能找到自己对应的值。

### 2、map集合的应用场景

需要存储一一对应的数据时可以考虑map集合。

### 3、map集合体系的特点

**注意：**map集合的所有特点都是由键决定的，值只是一个附属品，值不做要求。

HashMap(由键决定特点)：无序、不能重复、无索引

LinkedHashMap(由键决定特点)：有序、不能重复、无索引。

TreeMap(由键决定特点)：按照大小默认升序排序、不重复、无索引。