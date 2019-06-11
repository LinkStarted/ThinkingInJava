[TOC]
[脑图参考](https://blog.csdn.net/titer1/article/details/53872123)

# 第一章 对象导论  

## 1.1 抽象过程  

Java所基于的语言之一的Smalltalk的五个基本特性:

1. 万物皆为对象;
2. 程序是对象的集合，它们通过发送消息来告知彼此所要做的;
3. 每个对象都有自己的由其他对象所构成的存储;
4. 每个对象都拥有其类型;
5. 某一特定类型的所有对象都可以接收同样的消息(*继承*)。

对象的简洁描述： **对象具有状态、行为和标识**；具体说来，就是每一个对象在内存中都有一个唯一的地址。

注:  

- Smalltalk被公认为历史上第二个面向对象的程序设计语言和第一个真正的集成开发环境 (IDE)。
- Simula 67被认为是最早的面向对象程序设计语言，它引入了所有后来面向对象程序设计语言所遵循的基础概念：对象、类、继承。

## 1.2 每个对象都有一个接口  

- 创建抽象数据类型(类)是面向对象程序设计的基本概念之一。  
- 类描述了具有相同特性(数据元素)和行为(功能)的对象集合。  
- 接口确定了对某一特定对象所能发出的*请求*；满足这些请求的代码与隐藏的数据一起构成了*实现*。

## 1.3 每个对象都提供服务  

- 将对象想像为“服务提供者”，程序本身将向用户提供服务，它将通过调用其他对象提供的服务来实现这一目的，开发一个程序的目标就是去创建(或寻找)能够提供理想的服务来解决问题的一系列对象。
- **高内聚** 是软件设计的基本质量要求之一，指一个软件模块是由相关性很强的代码组成，只负责一项任务，也就是常说的单一责任原则。高内聚性的好处是可以提高程序的可靠性。

## 1.4 被隐藏的具体实现  

访问控制存在的原因：  

- 让客户端程序员无法触及他们不应该触及的部分；
- 允许库设计者可以改变类内部的工作方式而不用担心会影响到客户端程序员。  

访问控制符：  

- public ： 元素对任何人都是可用的；
- private ： 除类型创建者和类型的内部方法之外的任何人都不能访问的元素。如果有人试图访问private成员，就会在编译时得到错误信息;
- protected : 与private作用相当，差别仅在于继承的类可以访问protected成员，但是不能访问private成员;
- default ： 包访问权限(默认的访问权限),当没有使用前面提到的任何访问控制符时，它将发挥作用。在这种权限下，类可以访问在同一个包中的其他类的成员，但是在包之外，这些成员如同指定了private一样。

## 1.5 复用具体实现  

最简单地复用某个类的方式就是直接使用该类的一个对象，此外也可以将那个类的一个对象置于某个新的类中，我们称其为“创建一个成员对象”。

使用现有的类合成新的类，所以这种概念被称为**组合**(composition)。组合带来了极大的灵活性。新类的成员对象通常都被声明为private，使得使用新类的客户端程序员不能访问它们。

## 1.6 继承  

- 通过类(关键字class)将数据和功能封装到一起，形成了编程语言的基本单位。
- 继承的概念： 以现有的类为基础，复制它，然后通过添加和修改这个副本来创建新类。
- 继承使用的关键字： extends; `class A extends B {...}`
- 新类不仅包括现有类型的所有成员(尽管private成员被隐藏了起来，并且不可访问)，而且更重要的是它复制了基类的接口。也就是说，所有可以发送给基类对象的消息同时也可以发送给导出类对象。
- 使基类与导出类产生差异的方法：  
    1. 直接在导出类中添加新方法；
    2. 改变现有基类的方法：重写(Overriding)

- 纯粹替代： 继承时，只覆盖基类的方法，而不添加基类中没有的新方法，结果可以用导出类对象完全替代一个基类对象。这样称之为纯粹替代或替代原则。这种情况下基类和导出类之间的关系称为“is-a”(是一个)关系。
- 有时必须在导出类型中添加新的接口元素，这样也就扩展了接口。这个新的类型仍然可以替代基类，但是这种替代并不完美，因为基类无法访问新添加的方法。这种情况我们可以描述为“is-like-a”(像是一个)关系。

## 1.7 伴随多态的可互换对象  

- 前期绑定(静态绑定)： 在程序编译期的绑定；在Java中的方法，只有final，static，private和构造方法是前期绑定。
- [后期绑定](https://www.cnblogs.com/jstarseven/articles/4631586.html)(动态绑定)： 在运行是根据具体对象的类型进行绑定。运行时(动态)绑定针对的范畴只是**对象的方法**。

## 1.8 单根继承结构  

- 所有的类最终都继承自单一的基类： Object类。
- [Object类中常用的方法](https://www.cnblogs.com/zhangyinhua/p/7715486.html)
    1. clone()
    2. toString()
    3. getClass()
    4. finalize()
    5. equals()
    6. hashCode()
    7. wait()
    8. notify()
    9. notifyAll()

## 1.9 容器  

- Java中的容器：
    1. List： 用于存储序列；
    2. Map： 也称为关联数组，用来建立对象之间的关联；
    3. Set： 每种对象类型只持有一个。
- 泛型(参数化类型)： 使用泛型定制一个只接纳和取出某一种对象的容器；

## 1.10 对象的创建和生命期  

- Java完全采用了动态内存分配方式。每当想要创建新对象时，就要使用new关键字来构建此对象的动态实例。
- Java提供了被称为“垃圾回收器”的机制，它可以自动发现对象何时不再被使用，并继而销毁它。

## 1.11 异常处理：处理错误  

- 异常是一种对象，它从出错地点被“抛出”，并被专门设计用来处理特定类型错误的相应的异常处理器“捕获”。
- 异常提供了一种从错误状况进行可靠恢复的途径。

## 1.12 并发编程  

- 并发有一个隐患:共享资源。如果有多个并行任务都要访问同一项资源，那么就会出问题。因此，并发整个过程是: 某个任务锁定某项资源，完成其任务，然后释放资源锁，使其他任务可以使用这项资源。

# 第二章 一切都是对象

## 2.1 用引用操纵对象  

- 一切都被视为对象,但操纵的标识符实际上是对象的一个“引用”(reference)
- 字符串可以用带引号的文本初始化, `String s = "123";`

## 2.2 必须由你创建所有对象

### 2.2.1 存储到什么地方

1. **寄存器**：最快的存储区，位于处理器内部，不能直接控制；
2. **堆栈**： 位于通用RAM(随机访问存储器)中，堆栈指针若向下移动，则分配新的内存，若向上移动，则释放那些内存。这是一种快速有效的分配存储方法，仅次于寄存器；
3. **堆**： 一种通用的内存池(也位于RAM区)，用于存放所有的Java对象。编译器不需要知道存储的数据在堆里存活多长时闹。因此，在堆里分配存储有很大的灵活性。为这种灵活性必须要付出相应的代价：用堆进行存储分配和清理可能比用堆栈进行存储分配需要更多的时间；
4. **常量存储**： 常量值通常直接存放在程序代码内部，它们永远不会被改变。
5. **非RAM存储**： 如果数据完全存活于程序之外，那么它可以不受程序的任何控制，在程序没有运行时也可以存在。其中两个基本的例子是*流对象*和*持久化对象*。
    - 流对象： 对象转化成字节流，通常被发送给另一台机器。
    - 持久化对象： 对象被存放于磁盘上，因此，即使程序终止，它们仍可以保持自己的状态。这种存储方式的技巧在于：把对象转化成可以存放在其他媒介上的事物，在需要时，可恢复成常规的、基于RAM的对象。

### 2.2.2 特例： 基本类型

| 基本类型 | 大小| 最小值 | 最大值 | 包装器类型 | 默认值 |
| --- | --- | --- | --- | --- | --- |
| boolean | - | - | - | Boolean | false |
| char | 16 bits | Unicode 0 | Unicode 2^16 -1 | Character | '\u0000'(null) |
| byte | 8 bits | -128 | 127 | Byte | (byte)0 |
| short | 16 bits | -2^15 | 2^15-1 | Short | (short)0 |
| int | 32 bits | -2^31 | 2^31-1 | Integer | 0 |
| long | 64 bits | -2^63 | -2^63-1 | Long | 0L |
| float | 32 bits | IEEE754 | IEEE754 | Float | 0.0f |
| double | 64 bits | IEEE754 | IEEE754 | Double | 0.0d |
| void | - | - | - | - |

- boolean类型所占存储空间的大小没有明确指定，仅定义为能够取字面值true或false。
- 基本类型具有的包装器类，使得可以在堆中创建一个非基本对象，用来表示对应的基本类型。([自动装箱和自动拆箱](https://www.cnblogs.com/wang-yaz/p/8516151.html))
- 自动类型转换表： `byte-->short-->int-->long-->float-->double`;    `char-->int`

## 2.3 永远不需要销毁对象  

### 2.3.1 作用域

尽管以下代码在C和C＋＋中是合法的，但是在Java中却不能这样书写：

```java
{
    int x = 12;
    {
        int x= 96;
    }
}
```

编译器将会报告变量x已经定义过。所以，在C和C++里将一个较大作用域的变量“隐藏”起来的做法，在Java里是不允许的。因为Java设计者认为这样做会导致程序混乱。

### 2.3.2 对象的作用域  

由new创建的对象，只要你需要，就会一直保留下去。

Java有一个*垃圾回收器*，用来监视用new创建的所有对象，并辨别那些不会再被引用的对象。随后，释放这些对象的内存空间，以便供其他新的对象使用。也就是说，你根本不必担心内存回收的问题。你只需要创建对象， 一且不再需要，它们就会自行消失。

## 2.4 创建新的数据类型：类

- 类中可以设置两种元素：  
  1. 字段
  2. 方法

- 当 *基本数据* 类型作为 *类的成员* 时没有进行初始化, Java会赋予一个默认值(见上基本类型表格)。默认初始化不适用于非类的成员变量。

## 2.5 方法，参数和返回值  

方法的基本组成部分包括：**名称、参数、返回值和方法体**。下面是它最基本的形式：

```java
ReturnType methodName( /* Argument list */ ){
    /* Method body*/
}
```

**返回类型**描述的是在调用方法之后从方法返回的值。  
**参数列表**给出了要传给方法的信息的类型和名称。  
*方法名和参数列表*(它们合起来被称为“方法签名”)**唯一地标识出某个方法**。

Java中的方法只能作为类的一部分来创建。方法只有通过对象才能被调用(static方法是针对类调用的，并不依赖于对象的存在 ),且这个对象必须能执行这个方法调用。

### 2.5.1 参数列表  

- 参数传递为值传递，只不过对于对象参数，值的内容是对象的引用。
- return关键字表示：
  
    1. 代表“已经做完，离开此方法”；
    2. 如果此方法产生了一个值，这个值要放在return语句后面。
    3. 若返回类型是void , return关键字的作用只是用来退出方法。
    4. 如果返回类型不是void，那么无论在何处返回，编译器都会强制返回一个正确类型的返回值。

## 2.6 构建一个Java程序

### 2.6.1 名字可见性  

- 使用包名区分相同的类名；
- 包名一般用反转域名表示(com.baidu.utility)。

### 2.6.2 运用其他构建  

- import关键字指示编译器导入一个包，也就是一个类库。
  
```java
import java.util.ArrayList;
import java.util.*;
```

### 2.6.3 static关键字  

- 适用static的情况：
    1. 只想为某特定域分配单一存储空间，而不去考虑究竟要创建多少对象，甚至根本就不创建任何对象；
    2. 希望某个方法不与包含它的类的任何对象关联在一起。也就是说，即使没有创建对象，也能够调用这个法。

- 只须将static关键字放在定义之前，就可以将字段或方法设定为static。

    ```java
    class StaticTest {
        static int i = 47;
        static void xx(){StaticTest.i++;}
    }
    ```

- 引问static变量：  
    1. 通过对象来定位

        ```java
        StaticTest st = new StaticTest();
        st.i++;
        st.xx();
        ```

    2. 通过类名引用

        ```java
        StaticTest.i++;
        StaticTest.xx();
        ```

## 2.7 你的第一个Java程序  

- 编译java文件：`javac HelloWorld.java`
- 运行： `java HellWorld`

## 2.8 注释和嵌入式文档  

注释：

```java
1. /*多行注释*/
2. //单行注释
```

### 2.8.1 注释文档

- 所有javadoc命令都只能在`/**`注释中出现，和通常一样，注释结束于`*/`;
- 使用javadoc的方式主要有两种：嵌入HTML，或使用“文档标签”。
- javadoc只能为**public**(公共)和**protected**(受保护)成员进行文档注释。**private**(私有)和**包内可访问成员**的注释会被忽略掉，所以输出结果中看不到它们(不过可以用`-private`进行标记，以便把private成员的注释也包括在内)

### 2.8.2 －些标签示例

1. @see:引用其他类： `@see classname`
2. {@link package.class#member label}: 与@see相似，只是它用于行内
3. {@docRoot}：该标签产生到文档根目录的相对路径，用于文档树页面的显式超链接。
4. {@inheritDic}：该标签从当前这个类的最直接的基类中继承相关文档到当前的文档注释中。
5. @version： `@version version-information`,其中`version-information`可以是任何你认为适合包含在版本说明中的重要信息。
6. @author: `@author author-information`
7. @since: 该标签允许你指定程序代码最早使用的版本
8. @param: `@param parameter-name description`;其中,parameter-name是方法的参数列表中的标识符， description是可延续数行的文本，终止于新的文档标签出现之前。可以使用任意多个这种标签，大约每个参数都有一个这样的标签。
9. @return: `@return description`,其中，“description”用来描述返回值的含义，可以延续数行。
10. @throws: `@fully-qualified-class-name description`,其中fully-qualified-class-name给出一个异常类的无歧义的名字，而该异常类在别处定义。description(同样可以延续数行)告诉你为什么此特殊类型的异常会在方法调用中出现。
11. @Deprecated: 标签用于指出一些旧特性已由改进的新特性所取代，建议用户不要再使用这些旧特性，
因为在不久的将来它们很可能会被删除。

## 2.9 编码风格

代码风格是这样规定的(**驼峰风格**):  

- 类名的首字母要大写，如果类名由几个单词构成，那么把它们并在－起，其中每个内部单词的首字母都采用大写形式。
- 几乎其他所有内容--方法、字段(成员变量)以及对象引用名称等，公认的风格与类的风格一样，只是标识符的第一个字母采用小写

[练习题](https://blog.csdn.net/waterydd/article/details/70237399)

# 第三章 操作符

## 3.1 更简单的打印语句  

- `System.out.println("")`
- 包的静态导入: `import static package.class.*`

## 3.2 使用Java操作符  

- 操作符接受一个或多个参数，并生成一个新值。
- 几乎所有的操作符都只能操作“基本类型”。例外的操作符是“=”、“==”和“!=”，这些操作符能操作所有的对象。除此以外,String类支持“＋”和“+=”。

## 3.3 优先级  

- 一般而言，单目运算符优先级较高，赋值运算符优先级较低。算术运算符优先级较高，关系和逻辑运算符优先级较低。多数运算符具有左结合性，单目运算符、三目运算符、赋值运算符具有右结合性。
- Java 语言中运算符的优先级共分为 14 级，其中 1 级最高，14 级最低。在同一个表达式中运算符优先级高的先执行。

[运算符优先级表](http://c.biancheng.net/view/794.html)

| 优先级 | 运算符 | 结合性 |
| --- | --- | --- |
| 1 | `()`、`[]` | 从左向右 |
| 2 | `!`、`+`、`-`、`~`、`++`、`--` | 从右向左 |
| 3 | `*`、`/`、`%` | 从左向右 |
| 4 | `+`、`-` | 从左向右 |
| 5 | `<<`、`>>`、`>>>` | 从左向右 |
| 6 | `<`、`<=`、`>`、`>=`、`instanceof` | 从左向右 |
| 7 | `==`、`!=` | 从左向右 |
| 8 | `&` | 从左向右 |
| 9 | `^` | 从左向右 |
| 10 | `|` | 从左向右 |
| 11 | `&&` | 从左向右 |
| 12 | `||` | 从左向右 |
| 13 | `?:` | 从右向左 |
| 14 | `=`、`+=`、`-=`、`*=`、`/=`、`&=`、`|=`、`^=`、`~=`、`<<=`、 `>>=`、`>>>=` | 从右向左 |

例： `--y || ++x && ++z;`

这个表达式中包含了算术运算符和逻辑运算符。根据表中列出的优先级，可以确定它的执行顺序如下：
① 先计算 y 的自减运算符，即 --y。
② 再计算 x 的自增运算符，即 ++x。
③ 接着计算 z 的自增运算符，即 ++z。
④ 由于逻辑与比逻辑或的优先级高，这里将 ② 和 ③ 的结果进行逻辑与运算，即 ++x && ++z。
⑤ 最后将 ④ 的结果与 ① 进行逻辑或运算，即 --y||++x&&++z。

## 3.4 赋值  

- 赋值使用操作符“=”。它的意思是“取右边的值(即右值)，把它复制给左边(即左值)”。右值可以是任何常数、变量或者表达式(只要它能生成一个值就行)。但左值必须是一个明确的已命名的变量。也就是说，必须有一个物理空间可以存储等号右边的值。但是不能把任何东西赋给一个常数，常数不能作为左值〔比如不能说(4=a)。
- 对一个对象进行操作时，我们真正操作的是对对象的引用。所以倘若“将一个对象赋值给另一个对象”，实际是将“引用”从一个地方复制到另一个地方。
- [别名问题](https://blog.csdn.net/zane06/article/details/79705768)

## 3.5 算术操作符  

- Java的基本算术操作符: `+`，`-`，`*`，`/`，`%`
- 一元减号用于转变数据的符号，而一元加号只是为了与一元减号相对应，但是它唯一的作用仅仅是将较小类型的操作数**提升为int**。

## 3.6 自动递增和递减  

- 对于前缀递增和前缀递减(如++a 或--a)，会先执行运算，再生成值；
- 对于后缀递增和后缀递减(如a++或a--)，会先生成值，再执行运算。

## 3.7 关系操作符  

- 关系操作符包括：`<`, `>`，`<=`, `>=`, `==`, `!=`
- =和!=适用于所有基本数据类型；其他的不适用于boolean类型；
- == 和equeals()的[区别](https://blog.csdn.net/qishubiao/article/details/78503263)；

## 3.8 逻辑操作符  

- 逻辑操作符包括： `&&`， `||`， `!`
- "与"、"或"、""操作只可应用于布尔值。不可将一个非布尔值当作布尔值在逻辑表达式中使用。(`0&&1`是不合法的)
- 短路现象： 一旦能够明确无误地确定整个表达式的值，就不再计算表达式余下部分了。

## 3.9 直接常量  

- 直接常量后面的后缀字符标志了它的类型。若为大写(或小写)的L，代表long；大写(或小写)字母F，代表float；大写(或小写)字母D，则代表double。
- 十六进制数适用于所有整数数据类型，以前缀0x(或0X)，后面跟随0-9或小写(或大写)的a-f来表示。
- 八进制数由前缀0以及后续的0~7的数字来表示。
- 在使用十六进制和儿进制记数法时，以二进制形式显示结果将非常有用。通过使用Integer和Long类的静态方法toBinaryString()可以很容易地实现这一点。请注意，如果将比较小的类型传递给Integer.toBinaryString()方法，则该类型将自动被转换为int。
- 指数记数法(e):`1.39e^-43`代表`1.39 x 10^-43`
- 编译器通常会将指数作为双精度数(double)处理，所以假如没有这个尾随的f，就会收到一条出错提示，告诉我们必须使用类型转换将double转换成float.`float f4 = 1e-43f`

## 3.10 按位操作符  

- 按位操作符包括：`&`, `|`, `^`, `~`,他们可以与等号连用，除了按位非；

## 3.11 移位操作符  

- 移位操作符包括： `<<`, `>>`, `>>>`

## 3.12 三元操作符  

- 三元操作符表达式采取下述形式：`boolean-exp ? true-vlaue : false-value`

## 3.13 字符串操作符 + 和 +=  

- 如果表达式以一个字符串起头，那么后续所有操作数都必须是字符串型(请记住，编译器会把双引号内的字符序列自动转成字符串)

## 3.14 使用操作符时常犯的错误  

- =和==

## 3.15 类型转换操作符  

- 窄化转换(显式类型转换)`(short)123`，扩展转换则不必显式地进行类型转换
- 截尾和舍入： 浮点类型转换整型，会去掉小数点后的值，如果想将结果舍入，则使用`Math.round()`方法。
- **提升**： 只要类型比int小(即char 、byte或者short)，那么在运算之前，这些值会自动转换成int。这样一来，最终生成的结果就是int类型。如果想把结果赋值给较小的类型，就必须使用类型转换。
- 自动类型转换表： `byte-->short-->int-->long-->float-->double`,`char-->int`
- 通常，表达式中出现的最大的数据类型决定了表达式最终结果的数据类型。如果将一个float值与一个double值相乘，结果就是double。

## 3.16 Java没有"sizeof"  

- 在C和C＋＋中，需要使用`sizeof()`的最大原因是为了“移植”。不同的数据类型在不同的机器上可能有不同的大小，所以在进行一些与存储空间有关的运算肘，程序员必须获悉那些类型具体有多大。Java不需要`sizeof()`操作符来满足这方面的需要，因为所有数据类型在所有机器中的大小都是相同的。

# 第四章 控制执行流程  

## 4.1 true和false  

- 所有条件语句都利用条件表达式的真或假来决定执行路径。注意Java不允许我们将一个数字做为布尔值使用

## 4.2 if-else

## 4.3 迭代

- while：

```java
while(boolean-expression){
    statement
}
```

- do-while:

```java
do{
    statement
}while(boolean-expressoin)
```

- while和do-while唯一的区别就是do-while中的语句至少会执行一次，即便表达式第一次就被计算为false。而在while循环结构中，如果条件第一次就为false ，那么其中的语句根本不会执行。
- for
  
```java
for(initialization; boolean-expression;step){
    statement
}
```

- Java里**唯一**用到逗号操作符的地方就是for循环的控制表达式。在**控制表达式的初始化**和**步进控制**部分，可以使用一系列由逗号分隔的语句，而且那些语句均会独立执行。

## 4.4 Foreach语法  

- foreach语法，表示不必创建int变量去对由访问项构成的序列进行计数,foreach将自动产生每一项。

```java
foreach(元素类型type  元素变量value : 遍历对象obj){
    引用value的java语句;
}
```

- foreach 适用于数组和容器

## 4.5 return  

- return关键词有两方面的用途： 一方面指定一个方法返回什么值(假设它没有Void返回值)，另一方面它会导致当前的方法退出，并返回那个值。

## 4.6 break和continue  

- `break`用于强行退出循环，不执行循环中剩余的语句
- `continue`则停止执行当前的迭代，然后退回循环起始处，开始下一次迭代。

## 4.7 臭名昭著的“goto”  

- Java没有goto， `goto`是保留关键字
- 退出嵌套循环，使用label标签

**4种退出嵌套循环的方法**：

1. 标号label：在外面的循环语句前定义一个标号，然后再里层循环体代码中使用带有标号的break语句，标号用于跳出多层嵌套循环，你可以用标号label标出你想退出哪一个语句。规定标号label必需放在循环之前(意味着循环必需紧跟着标号)。Java虽然保留了goto关键词，却不允许使用 (goto为保留字)。需要注意的是Label和下面的循环语句间不能有其他代码。标号同时适用于break和continue。

```java
public class OutLoopWithLabel{  
    public static void main(String args[]) {  
        ok: // 设定跳出当前循环的一个标号 注意ok后面是冒号：  
        for (int i = 0; i < 10; i++) {  
            for (int j = 0; j <= 10; j++) {  
                System.out.println("i=" + i + ",j=" + j);  
                if (j == 5)  
                    break ok; // 设定跳出当前循环的一个标号  
            }  
        }  
    }  
}  
```

2. boolean，break组合：通过Boolean型条件变量和break的组合，由内层循环在跳出(break)前改变条件变量，外层循环检测条件变量改变时终止外层循环。

```java
public class OutLoopWithBooleanBreak {  
    public static void main(String args[]) {  
        int arr[][] = { { 1, 2, 3 }, { 4, 5, 6, 7 }, { 9 } };  
        boolean found = false;  
        System.out.println("arr.length " + arr.length);  
        for (int i = 0; i < arr.length && !found; i++) {  
            for (int j = 0; j < arr[i].length; j++) {  
                System.out.println("i=" + i + ",j=" + j);  
                if (arr[i][j] == 5) {  
                    found = true; // 修改了第一个循环中的参数found  
                    break; // 跳出循环  
                }  
            }  
        }  
    }  
}
```

3. return：在内层循环直接跳出整个方法。
4. throw Exception：在内层循环直接抛出异常

```java
public class OutLoopWithException {  
    public static void main(String[] args) throws Exception {  
        for (int i = 0; i < 10; i++) {  
            for (int j = 0; j < 10; j++) {  
                if (i * j > 60) {  
                    throw new Exception("exception");  
                }  
                System.out.println(i + " * " + j + " = " + (i * j));  
            }  
        }  
    }  
}  
```

## 4.8 switch  

```java
switch(integral-selector){
    case integral-value1 : statement; break;
    case integral-value2 : statement; break;
    case integral-value3 : statement; break;
    default ： statement;
}
```

- Integral-selector(整数选择因子)是一个能够产生**整数值的表达式**，switch能将这个表达式的结果与每个integral-value(整数值)相比较。若发现相符的，就执行对应的语句(单一语句或多条语句，其中并不需要括号)。若没有发现相符的，就执行default(默认)语句。
- 每个case均以一个break结尾，这样可使执行流程跳转至switch主体的末尾。break是可选的，若省略break，会继续执行后面的case语句，直到遇到一个break为止。
- switch语句是实现多将选择(也就是说从一系列执行路径中挑选一个)的一种干净利落的方法。但它要求使用一个选择因子，并且必须是int或char那样的整数值。
- 在jdk 7 之前，switch 只能支持 byte、short、char、int 这几个基本数据类型和其对应的封装类型。switch后面的括号里面只能放int类型的值，但由于byte，short，char类型，它们会自动转换为int类型(精精度小的向大的转化)，所以它们也支持。注意，对于精度比int大的类型，比如long、float，doulble，不会自动转换为int，如果想使用，就必须强转为int，如(int)float;jdk1.7后，整形，枚举类型，boolean，字符串都可以。
- 为什么jdk1.7后又可以用string类型作为switch参数呢？
其实，jdk1.7并没有新的指令来处理switch string，而是通过调用switch中string.hashCode,将string转换为int从而进行判断。

# 第五章 初始化与清理  

## 5.1 用构造器确保初始化

- 创建对象时，如果其类具有构造器，Java就会在用户有能力操作对象之前自动调用相应的构造器，从而保证了初始化的进行。
- 构造器采用与类相同的名称

## 5.2 方法重载  

- 区分重载的方法： 每个重载的方法都必须有一个独一无二的参数类型列表。甚至参数顺序的不同也足以区分两个方法。
- 涉及基本类型的重载：

  - 如果传入的数据类型(实际参数类型)小于方法中声明的形式参数类型，实际数据类型就会被提升。char型略有不同，如果无法找到恰好接受char参数的方法，就会把char直接提升至int型。
  - 如果传入的实际参数较大，就得通过类型转换来执行窄化转换。如果不这样做，编译器就会报错。

- 根据方法的返回值来区分重载方怯是行不通的。例：

    ```java
    int f(){}
    void f(){}

    int x = f(); // 明确了返回值类型就可以编译器就可以确定调用的是哪一个方法
    f()；// 如果不关心返回值，就无法确定调用的方法是哪一个

    ```

## 5.3 默认构造器  

- 默认构造器(又名“无参”构造器)是没有形式参数的，它的作用是创建一个 “默认对象”。如果你写的类中没有构造器，则编译器会自动帮你创建一个默认构造器。

## 5.4 this关键字  

- `this`关键字只能在方法内部使用，在方法内部获得当前对象的引用；
- `this`的三种用法：
  - `this`调用本类中的属性，也就是类中的成员变量；
  - `this`调用本类中的其他方法；
  - `this`调用本类中的其他构造方法，调用时要放在构造方法的首行;且不能有第二个`this`；

- `static`方法就是没有`this`的方法；
- 在`static`方法内部不能调用非静态方法，反过来倒是可以。(通过传递一个对象的引用到静态方法中可以调用非静态方法。[例](https://www.cnblogs.com/phil_jing/p/5153754.html)
- 可以在没有创建任何对象的前提下，仅仅通过类本身来调用static方法,是static方法的主要用途。

## 5.5 清理：终结处理和垃圾回收  

- Java里的对象却并非总是被垃圾回收:  

  - 对象可能不被拉圾回收。
  - 垃圾回收并不等于"析构"。
  - **垃圾回收只与内存有关**。

- 如果Java虚拟机(JVM)并未面临内存耗尽的情形，它是不会浪费时间去执行垃圾回收以恢复内存的。
- 不要过多地使用`finalize()`: 垃圾清理不能指望`finalize()`，必须有其他的清理方法。
- `System.gc()`: 只是提醒虚拟机，程序员希望你在这回收一下对象，但回不回收还是虚拟机来决定，也就是说程序员对回不回收没有绝对的控制权。
- 即时(Just-In-Time, JIT)编译器的技术,这种技术可以把程序全部或部分翻译成本地机器码(这本来是Java虚拟机的工作)，程序运行速度因此得以提升。
- HotSpot使用类似**惰性评估**的方法(即时编译器只在必要的时候才编译代码。这样，从不会被执行的代码也许就压根不会被JIT所编译),代码每次被执行的时候都会做一些优化，所以执行的次数越多，它的速度就越快。

### 5.5.1 垃圾回收器如何工作

**引用记数**是一种简单但速度很慢的垃圾回收技术。每个对象都含有一个引用记数器，当有引用连接至对象时，引用计数加1。当引用离开作用域或被置为null时，引用计数减1。垃圾回收器会在含有全部对象的列表上遍历，当发现某个对象的引用计数为0时，就释放其占用的空间。这种方法有个缺陷，如果对象之间存在循环引用，可能会出现“对象应该被回收，但引用计数却不为零”的情况。引用记数常用来说明垃圾收集的工作方式，但似乎从未被应用于任何一种Java虚拟机实现中。  

一些更快的模式中，垃圾回收器并非基于引用记数技术。它们依据的思想是：对任何“活”的对象，一定能最终追溯到其存活在堆栈或静态存储区之中的引用。在这种方式下，Java虚拟机将采用一种**自适应的垃圾回收**技术。有一种做法名为**停止-复制**(stop-and-copy)。先暂停程序的运行,然后将所有存活的对象从当前堆复制到另一个堆，没有被复制的全部都是垃圾。当对象被复制到新堆时，它们是一个挨着一个的，所以新堆保持紧凑排列，然后就可以按前述方法简单、直接地分配新空间了。当把对象从一处搬到另一处时，所有指向它的那些引用都必须修正。导致这种做法效率比较低的2个原因：

- 首先，得有两个堆，然后得在这两个分离的堆之问来回捣腾，从而得维护比实际需要多一倍的空间。
- 第二个问题在于复制。程序进入稳定状态之后，可能只会产生少量垃圾，甚至没有垃圾。尽管如此，复制式回收器仍然会将所有内存自一处复制到另一处，这很浪费。

为了避免这种情形，一些Java虚拟机会进行检查：要是没有新垃圾产生，就会转换到另一种工作模式(即“自适应”)。这种模式称为**标记-清扫**(mark-and-sweep)。“标记一清扫”所依据的思路同样是从堆校和静态存储区出发，遍历所有的引用，进而找出所有存活的对象。每当它找到一个存活对象，就会给对象设一个标记，这个过程中不会回收任何对象。只有全部标记工作完成的时候，清理动作才会开始。在清理过程中，没有标记的对象将被释放，不会发生任何复制动作。所以剩下的堆空间是不连续的，垃圾回收器要是希望得到连续空间的话，就得重新整理剩下的对象。  

## 5.6 成员初始化  

- 类的每个基本类型数据成员保证都会有一个初始值
- 在类里定义一个对象引用时，如果不将其初始化，此引用就会获得一个特殊值null。

### 5.6.1 指定初始化

1. 在定义类成员变量的地方为其赋值:

```java
public class InitialValues2 {
    boolean bool = true;
    char ch = 'x';
    byte b = 47;
    short s = 0xff;
    int i = 999;
    long lng = 1:
    float t = 3.14f;
    double d= 3.14159;
}
```

2. 可以通过调用某个方法来提供初值：

```java
public class Hethodinit{
    int i= f();
    int f(){return 11;}
}
```

3. 这个方法也可以带有参数，但这些参数必须是已经被初始化了的。

```java
public class Hethodinit2{
    int i= f();
    int j = g(i);
    int f() {return 11;}
    int g(int n) {return n * 10; }
}

```

## 5.7 构造器初始化  

- 无法阻止自动初始化的进行，它将在构造器被调用之前发生

### 5.7.1 初始化顺序  

在类的内部，变量定义的先后顺序决定了初始化的顺序。即使变量定义散布于方法定义之间，它们仍旧会在任何方法(包括构造器)被调用之前得到初始化。

```java
class Window {
    Window(int maker){print("Window(" + maker + ")");}
}

class House{
    Window w1 = new Window(1);
    House(){
        print("House()");
        w3 = new Window(33);
    }
    Window w2 = new Window(2);
    void f(){
        print("f()");
    }
    Window w3 = new Window(3);
}

public class OrderOfInitialization{
    public static void main(String[] args){
        House h = new House();
        h.f();
    }
}

/*Output:
Window(1)
Window(2)
Window(3)
House()
Window(33)
*/
```

### 5.7.2 静态数据的初始化

```java
class Bowl(){
    Bowl(int marker){
        print("Bowl(" + marker + ")");
    }
    void f1(int marker){
        print("f1(" + marker + ")");
    }
}

class Table{
    static Bowl bowl1 = new Bowl(1);
    Table(){
        print("Table()");
        bowl2.f1(1);
    }
    void f2(int marker){
        print("f2(" + marker + ")");
    }
    static Bowl bowl2 = new Bowl(2);
}

class Cupboard{
    Bowl bowl3 = new Bowl(3);
    static Bowl bow4 = new Bowl(4);
    Cupboard(){
        print("Cupboard()");
        bowl4.f1(2);
    }
    void f3(int marker){
        print("f3("+ marker + ")");
    }
    static Bowl bowl5 = new Bowl(5);
}

public class StaticInitailization{
    public static void main(String[] args){
        print("Creating new Cupboard() in main");
        new Cupboard();
        print("Creating new Cupboard() in main");
        new Cupboard();
        table.f2(1);
        cupboard.f3(1);
    }
    static Table table = new Table();
    static Cupboard cupboard = new Cupboard();
}

/*Output:
Bowl(1)
Bowl(2)
Table()
f1(1)
Bowl(4)
Bowl(5)
Bowl(3)
Cupboard()
f1(2)
Creating new Cupboard() in main
Bowl(3)
Cupboard()
f1(2)
Creating new Cupboard() in main
Bowl(3)
Cupboard()
f1(2)
f2(1)
f3(1)
*/
```

由输出可见，静态初始化只有在必要时刻才会进行。如果不创建Table对象，也不引用Table.bl或Table.b2，那么静态的Bowl bl和b2永远都不会被创建。只有在第一个Table对象被创建(或者第一次访问静态数据)的时候，它们才会被初始化。此后，静态对象不会再次被初始化。  
初始化的顺序是先静态对象(如果它们尚未因前面的对象创建过程而被初始化)，而后是“非静态”对象。要执行main()(静态方法)，必须加载**Staticlnitialization类**，然后其静态域**table和cupboard被初始化**，这将导致它们对应的类也被加载，并且由于它们也都包含静态的Bowl对象，因此Bowl随后也被加载。  

- 总结一下对象的创建过程，假设有个名为Dog的类：

  1. 即使没有显式地使用static关键字，**构造器实际上也是静态方法**。因此，当首次创建类型为Dog的对象时(构造器可以看成静态方法)，或者Dog类的静态方法/静态域首次被访问时，Java解释器必须查找类路径，以定位Dog.class文件。
  2. 然后载入Dog.class(后面会学到，这将创建一个Class对象)，有关静态初始所有动作都会执行。因此，静态初始化只在Class对象首次加载的时候进行一次。
  3. 当用`new Dog()`创建对象的时候，首先将在堆上为Dog对象分配足够的存储空间。
  4. 这块存储空间会被清零，这就自动地将Dog对象中的所有基本类型数据都设置成了默值(对数字来说就是0，对布尔型和字符型也相同)，而引用则被设置成了null。
  5. 执行所有出现于字段定义处的初始化动作。
  6. 执行构造器。

### 5.7.3 显示的静态初始化

```java
class Cup{
    Cup(int marker){
        print("Cup(" + marker + ")");
    }
    void f(int marker){
        print("f(" + maker + ")");
    }
}

class Cups{
    static Cup cup1;
    static Cup cup2;
    static {
        cup1 = new Cup(1);
        cup2 = new Cup(2);
    }
    Cups(){
        print("Cups()");
    }
}

public class ExplicitStatic{
    public stataic void main(String[] args){
        print("Inside main()");
        Cups.cup1.f(99); //(1)
    }
    // static Cups cups1 = new Cups(); // (2)
    // static Cups cups2 = new Cups(); // (2)
}

/*Output:
Inside main()
Cup(1)
Cup(2)
f(99)
*/
```

- 静态初始化动作只进行一次。

### 5.7.4 非静态实例初始化

```java
class Mug{
    Mug(int marker){
        print("Mug(" + marker + ")");
    }
    void f(int marker){
        print("f(" + marker + ")");
    }
}
pubic class Mugs{
    Mug mug1;
    Mug mug2;
    {
        mug1 = new Mug(1);
        mug2 = new Mug(2);
        print("mug1 & mug2 initialized");
    }
    Mugs(){
        print("Mugs()");
    }
    Mugs(int i){
        print("Mugs(int)");
    }
    public static void main(String[] args){
        print("Inside main()");
        new Mugs();
        print("new Mugs completed");
        new Mugs(1);
        print("new Mugs(1) completed");
    }
}

/*Output:
Inside main()
Mug(1)
Mug(2)
mug1 & mug2 initialized
Mugs()
new Mugs completed
Mug(1)
Mug(2)
mug1 & mug2 initialized
Mugs(int)
new Mugs(1) completed
*/
```

- 它也使得你可以保证无论调用了哪个显式构造器，某些操作都会发生。从输出中可以看到实例初始化子句是在两个构造器之前执行的。

### 5.7.5 成员初始化顺序

1. 静态变量
2. 静态初始化块
3. 成员变量
4. 非静态初始化块
5. 构造器

[参考](https://blog.csdn.net/youanyyou/article/details/78990293)

## 5.8 数组初始化

- 数组只是相同类型的、用一个标识符名称封装到一起的一个对象序列或基本类型数据序列。数组是通过方括号下标操作符门来定义和使用的。`int[] a`或者`int a[]` 来定义一个数组。
- 编译器不允许指定数组的大小。即`int[2] a;`是不允许的。
- 数组元素中的基本数据类型值会自动初始化成空值{对于数字和字符，就是0，对于布尔型，是false)。
- 初始化的3种方式：
  
  ```java
  int[] a1 = {1,2,3,4,5,};//结尾的逗号是可选的，
  int[] a = new int[]{1,2,3,4,5}//这种初始化方式与上面的等价

  int[] a2;
  a2 = new int[20];

  int[] a3 = new int[10];
  ```

### 5.8.1 可变参数列表

```java
class A{}

public class VarArgs{
    static void printArray(Object[] args){
    //static void printArray(Object... args){  // 在Java SE5中的新特性使用...来代表可变参数
        for(Object obj : args){
            System.out.print(obj + " ");
            System.out.println();
        }
    }
    public static void main(string[] args){
        printArray(new Object[]{
            new Integer(47),new Float(3.14),new Double(1.11)
        });
        printArray(new Object[]{"one","two","three"});
        printArray(new Object[]{new A(), new A(), new A()});
    }
}

//Output
47 3.14 1.11
one two three
A@1a46e30 A@3e25a5 A@19821f
```

- 由于所有的类都直接或间接继承子Object类，所以可以创建以Object数组为参数的方法来实现可变参数列表。
- 除了Object类型，使用`...`也可以来表示可变参数列表。
- 使用`...`的可变参数列表的重载与普通方法不同：无法仅通过改变可变参数的类型来重载方法。

## 5.9 枚举类型

- 关键字： `enum`  
- 定义枚举类型：
  
  ```java
  public enum Spiciness{
      NOT, MILD, MEDIUM, HOT, FLAMING //由于枚举类型的实例是常量，因此按照命名惯例它们都用大写字母表示(如果在一个名字中有多个单词，用下划线将它 们隔开)。
  }
  ```

- 使用枚举类型：

    ```java
    public class SimpleEnum{
        public static void main(String[] args){
            Spiciness howHot = Spiciness.NOT; //为了使用enum，需要创建一个该类型的引用，并将其赋值给某个实例:
            System.out.println(howHot);
        }
    }
    ```

- 一些有用的特性： 

  - `toString()`: 可以很方便地显示某个enum实例的名字
  - `ordinal()`: 用来表示某个特定enum常量的声明顺序
  - `static values()`: 用来按照enum常量的声明顺序，产生由这些常量值构成的数组。
  
  ```java
  public class EnumOrder{
      public static void main(String[] args ){
          for(Spiciness s: Spiciness.valus()){
              System.out.println(s + ". ordinal " + s.ordinal());
          }
      }
  }

  //Output
  NOT. ordinal 0
  MILD. ordinal 1
  MEDIUM. ordinal 2
  HOT. ordinal 3
  FLAMING. ordinal 4
  ```

- 尽管enum看起来像是一种新的数据类型，但是这个关键字只是为enum生成对应的类时，产生了某些编译器行为，因此在很大程度上，你可以将enum当作其他任何类来处理。事实上，enum确实是类，并且具有自己的方法。
- enum有一个特别实用的特性，即它可以在switch语句内使用:

    ```java
    public class Burrito{
        Spiciness degree;

        public Burrito(Spiciness degree){
            this.degree = degree;
        }
        public void describe(){
            System.out.print("This burrito is "):
            switch(degree){
                case NOT: System.out.println("not spicy at all.");break;
                case MILD:
                case MEDIUM: System.out.println("a little hot");break;
                case HOT:
                case FLAMING:
                default: System.out.println("maybe too hot");break;
            }
        }
        public static void main(String[] args){
            Burrito
                plain = new Burrito(Spiciness.NOT),
                greenChile = new Burrito(Sp1ciness.MEDIUH),
                jalapeno = new Burrito(Spiciness.HOT);
            plain.describe();
            greenChile.describe();
            jalapeno.describe();
        }
    }
    ```

# 第六章 访问权限控制

## 6.1 包：库单元

- 当编写一个java源代码文件时，此文件通常被成为**编译单元**。在编译单元内则可以有一个public类，该类的名称必须与文件的名称相同(包括大小写，但不包括文件的后缀名.java)。每个编译单元只能有一个public类，否则编译器就不会接受。如果在该编译单元中还有额外的类的话，那么在包之外的世界无法看到这些类，这是因为它们不是public类，而且它们主要用来为主public类提供支持。

### 6.1.1 代码组织

- 当编译一个.java文件时，在扣va文件中的每个类都会有一个输出文件，而该输出文件的名称与.java文件中每个类的各称相同，只是多了一个后缀.class。
- 如果希望这些构件(每一个都有它们自己的独立的.java和.class文牛)从属于同一个群组，就可以使用关键字`package`。
- **如果使用package语句，它必须是文件中除注释意外的第一句程序代码**。
- `package`和`import`关键字允许你做的，是将单一的全局名字空间分隔开，使得无论多少人使用Internet以及java开始编写类，都不会出现名称冲突问题。

### 6.1.2 创建独一无二的包名

- 按照惯例，package名称的第一部分是类的创建者的反顺序的Internet域名。如果你遵照惯例，Internet域名应是独一无二的，因此你的package名称也将是独一无二的，也就不会出现名称冲突的问题了。
- Java解释器的运行过程如下:首先，找出环境变量CLASSPATH，CLASSPATH包含一个或多个目录，用作查找.class文件的根目录。从根目录开始，解释器获取包的名称并将每个句点替换成反斜杠，以从CLASSPATH根中产生一个路径。得到的路径会以CLASSPATH中的各个不同项相连接，解释器就在这些目录中查找与你所要创建的类名相关的.class文件。

### 6.1.3 定制工具库

- 创建自己的工具库来减少或消除重复的程序代码。

### 6.1.4 用import改变行为

- 条件编译还有其他一些有价值的用途。调试就是一个常见的用途。调试功能在开发过程中是开启的，而在发布的产品中是禁用的。可以通过修改被导入的package的方法来实现这一目的，修改的方法将是你程序中用到的代码从调试版改为发布版。

### 6.1.5 对使用包的忠告

- 务必记住，无论何时创建包，都已经在给定包的名称的时候就隐含的指定了目录结构，这个包必须位于其名称所指定的目录中，而且该目录必须是以CLASSPATH开始的目录中可以查询到的。

## 6.2 Java访问控制修饰符

- public,protected和private这几个Java访问权限修饰词在使用时，是置于类中每个成员的定义之前的一无论它是一个域还是一个方法。每个访问权限修饰词仅控制它所修饰的特定定义的访问权。
- 如果不提供任何访问权限修饰词，则意味着它是“包访问权限”。因此，无论如何，所有事物都具有某种形式的访问权限控制

### 6.2.1 包访问权限

- 默认访问权限没有任何关键字，但通常是指包访问权限(有时也表示成为friendly)。这就意味着当前的包中的所有其他类对那个成员都有访问权限，但对于这个包之外的所有类，这个成员却是private。
- 取得对某成员的访问权的唯一途径是：
  
  - 使该成员成为public。于是，无论是谁，无论在哪里，都可以访问该成员。
  - 通过不加访问权限修饰词并将其他类放置于同一个包内的方式给成员赋予包访问权。于是包内的其他类也就可以访问该成员了。
  - 继承而来的类既可以访问public成员也可以访问protected成员(但访问private成员却不行)。只有在两个类都处于同一个包内时，它才可以访问包访问权限的成员。
  - 提供访问器(accessor)和变异器(mutator)方法(也称作get/set方法)，以读取和改变数值。

### 6.2.2 public: 接口访问权限

- 使用关键字public ，就意味着public之后紧跟着的成员声明自己对每个人都是可用的

### 6.2.3 private：你无法访问

- 关键字private的意思是，除了包含该成员的类之外，其他任何类都无法访问这个成员。
- private终有其用武之地的示例：可能想控制如何创建对象，并阻止别人直接访问某个特定的构造器（或全部构造器）

### 6.2.4 protected: 继承访问权限

- 相同包内的其他类可以访问protected元素。

## 6.3 接口和实现

- 出于两个很重要的原因，访问权限控制将权限的边界划在了数据类型的内部。
  - 第一个原因是要设定客户端程序员可以使用和不可以使用的界限。
  - 第二个原因，即将接口和具体实现进行分离
- 为了清楚起见，会采用一种将public成员置于开头，后面跟着protected、包访问权限和private成员的创建类的形式

## 6.4 类的访问权限

- 每个编译单元（文件）都只能有一个public类。这表示，每个编译单元都有单一的公共接口，用public类来表现。
- public类的名称必须完全与含有该编译单元的文件名相匹配，包括大小写。
- 虽然不是很常用，但编译单元内完全不带public类也是可能的。在这种情况下，可以随意对文件命名。
- 类既不可以是private的（这样会使得除该类之外，其他任何类都不可以访问它），也不可以是protected的。
- 对于**类的访问权限**，仅有两个选择：包访问权限或public。如果不希望其他任何人对该类拥有访问权限，可以把所有的构造器都指定为private，从而阻止任何人创建该类的对象，但是有一个例外，就是你在该类的static成员内部可以创建。
- 一个内部类可以是private或是protect的

代码示例

```java
class Soup1{
    private Soup1(){}
    public static Soup1 makeSoup(){
        return new Soup1();
    }
}

class Soup2{
    private Soup2(){}
    private static Soup2 ps1 = new Soup2();
    public static Soup2 access(){
        return ps1;
    }
    public void f(){}
}

public class Lunch{
    void testPrivate(){
        //can't do this! Private constructor:
        // Soup1 soup = new Soup1();
    }
    void testStatic(){
        Soup1 soup = Soup1.makeSoup();
    }
    void testSingleton(){
        Soup2.access().f();
    }
}
```

- Soup2用到了所谓的设计模式。这种特定的模式被称为singleton（**单例**），这是因为你始终只能创建它的一个对象。Soup2类的对象是作为Soup2的一个static private成员而创建的，所以有且仅有一个，而且除非是通过public方法access()， 否则是无法访问到它的。
- 如果没能为类访问权限指定一个访问修饰符， 它就会默认得到包访问权限。这就意味着该类的对象可以由包内任何其他类来创建，但在包外则是不行的。（一定要记住，相同目录下的所有不具有明确package声明的文件，都被视作是该目录下默认包的一部分然而，如果该类的某个static成员是public的话，则客户端程序员仍旧可以调用该static成员，尽管他们并不能生成该类的对象。

# 第七章 复用类

## 7.1 组合语法

## 7.2 继承语法

## 7.3 代理

## 7.4 结合使用组合和继承

## 7.5 在组合与继承之间选择

## 7.6 protected关键字

## 7.7 向上转型

## 7.8 final关键字

## 7.9 初始化及类的加载

