## 异常

Java异常层次结构图

![Java 异常类层次结构图](https://oss.javaguide.cn/github/javaguide/java/basis/types-of-exceptions-in-java.png)

### Exception与Error有什么区别

- `Exception`：程序本身可以处理的异常，可以通过`catch`来进行捕获，`Exception`又可以分为Checked Exception（受检查异常，必须处理）和Unchecked Exception（不受检查异常，可以不处理）
- `Error`：`Error`属于程序无法处理的错误，不建议通过`catch`捕获，例如Java 虚拟机运行错误（`Virtual MachineError`）、虚拟机内存不够错误(`OutOfMemoryError`)、类定义错误（`NoClassDefFoundError`）等 。这些异常发生时，Java 虚拟机（JVM）一般会选择线程终止。

### Checked Exception和Unchecked Exception有什么区别

**Checked Exception** 即 受检查异常 ，Java 代码在编译过程中，如果受检查异常没有被 `catch`或者`throws` 关键字处理的话，就没办法通过编译。

除了`RuntimeException`及其子类以外，其他的`Exception`类及其子类都属于受检查异常 。常见的受检查异常有：IO 相关的异常、`ClassNotFoundException`、`SQLException`...。

**Unchecked Exception** 即 **不受检查异常** ，Java 代码在编译过程中 ，我们即使不处理不受检查异常也可以正常通过编译。

`RuntimeException` 及其子类都统称为非受检查异常，常见的有（建议记下来，日常开发中会经常用到）：

- `NullPointerException`(空指针错误)
- `IllegalArgumentException`(参数错误比如方法入参类型错误)
- `NumberFormatException`（字符串转换为数字格式错误，`IllegalArgumentException`的子类）
- `ArrayIndexOutOfBoundsException`（数组越界错误）
- `ClassCastException`（类型转换错误）
- `ArithmeticException`（算术错误）
- `SecurityException` （安全错误比如权限不够）
- `UnsupportedOperationException`(不支持的操作错误比如重复创建同一用户)

### try-catch-finally如何使用

- `try`：用于捕获异常，其后可接零个或多个`catch`块，如果没有`catch`块，必须跟一个`finally`块
- `catch`块：用于处理try捕获的异常
- `finally`：无论是否捕获异常或处理异常，`finally`块中的语句都会被执行，当`try`块或`catch`块中遇到 `return` 语句时，`finally` 语句块将在方法返回之前被执行。

>**不要在 finally 语句块中使用 return!** 当 try 语句和 finally 语句中都有 return 语句时，try 语句块中的 return 语句会被忽略。这是因为 try 语句中的 return 返回值会先被暂存在一个本地变量中，当执行到 finally 语句中的 return 之后，这个本地变量的值就变为了 finally 语句中的 return 返回值。

在以下 2 种特殊情况下，`finally` 块的代码也不会被执行：

1. 程序所在的线程死亡。
2. 关闭 CPU。
3. finally 之前虚拟机被终止运行的话，finally 中的代码就不会被执行。

## 反射

反射被称为框架的灵魂，主要是因为它赋予了我们在运行是分析类以及执行类中的能力。通过反射可以获取任意一个类的所有属性和方法，还可以调用这些方法和属性。

类似于spring，springBoot，MyBatis等框架中都使用了大量的反射机制，这些框架中也**大量使用动态代理，动态代理的实现也依赖于反射。**

注解的实现也实现了反射，可以基于反射类，然后获取到类/属性/方法/方法的参数的注解

### 反射的优点，缺点

优点：让代码更加灵活，为各种框架提供开箱即用的功能提供便利

缺点：让我们在运行是有分析操作的能力，同样也增加安全问题，比如**可以无视泛型参数的安全检查**，另外反射的性能也稍微差一点

### 获取Class对象的四种方法

**1. 知道具体类的情况下可以使用：**

```java
Class alunbarClass = TargetObject.class;
```

但是我们一般是不知道具体类的，基本都是通过遍历包下面的类来获取 Class 对象，通过此方式获取 Class 对象不会进行初始化

**2. 通过 `Class.forName()`传入类的全路径获取：**

```java
Class alunbarClass1 = Class.forName("cn.javaguide.TargetObject");
```

**3. 通过对象实例`instance.getClass()`获取：**

```java
TargetObject o = new TargetObject();
Class alunbarClass2 = o.getClass();
```

**4. 通过类加载器`xxxClassLoader.loadClass()`传入类路径获取:**

```java
ClassLoader.getSystemClassLoader().loadClass("cn.javaguide.TargetObject");
```

## 注解

`Annotation`(注解)是Java5开始引入的新特性，可以看作是一种特殊的注释，主要用于修饰类、方法或者变量，提供某些信息共程序在编译或者运行的时候使用。

注解只有被解析之后才会生效，常见的解析方法有：

- 编译期直接扫描：编译器在编译java代码的时候扫描对应的注解并处理，比如某个方法使用`@Override`注解，编译器在编译的时候就会检测当前的方法是否重写了父类对应的方法
- 运行期间通过反射处理：想框架中自带的注解（`@Value`，`@Commponent`）都是通过反射来进行处理

## SPI是什么，与API有什么区别

SPI就是专门共给服务提供者或者扩展框架功能的开发者使用的一个接口（即使用者提供一个规范，服务提供者/开发者根据这个规范进行开发，虽然实现方法可能不同，但是都是在这个规范下完成了对应的功能）

与API的区别：

上方为API，下方为SPI。

![SPI VS API](https://oss.javaguide.cn/github/javaguide/java/basis/spi-vs-api.png)

- API是实现放提供了接口和实现，调用方通过调用接口拥有实现方给我们提供的能力。接口和实现都是放在实现方的包里面
- SPI是调用方指定接口规则，实现方根据这个规则实现这个接口，从而提供服务

### SPI的优点，缺点

优点：能够提高接口设计的灵活性

缺点：

- 需要遍历加载所有的实现类，不能做到按需加载，**效率较低**
- 当有多个`ServiceLoader`同时`Load`，**会有并发问题**

## 序列化和反序列化

当我们需要持久化Java对象比如将Java对象存在文件中，或者是通过网络传输Java对象，需要用到序列化

**序列化：**将数据结构或者对象转换成可以存储或传输的形式，通常是二进制字节流，也可以是JSON，XML等文本格式

**反序列化：**将在序列化过程中所生成的数据转换为原始数据结构或者对象的过程

**应用场景：**

- 对象在进行网络传输（远程调用RPC）之前需要先序列化，接收到序列化对象之后需要再进行反序列化
- 将对象存储到文件之前需要进行序列化，将对象从文件中读取出来需要进行反序列化
- 将对象存储到数据库（Redis）之前需要用到序列化，将对象从缓存数据库中读取出来需要反序列化
- 将对象存储到内存之前需要进行序列化，从内存中读取出来之后需要进行反序列化

其主要目的是通过网络传输对象或者将对象存储到文件系统、数据库、内存中

### 序列化对应TCP/IP 4层模型中的哪一层？（表示层）

![TCP/IP 四层模型](https://oss.javaguide.cn/github/javaguide/cs-basics/network/tcp-ip-4-model.png)

表示层做的事主要就是对应用层的用户数据进行处理转换为二进制流，反过来就是反序列化

### 常用序列化协议

JDK 自带的序列化方式一般不会用 ，**不支持跨语言调用，序列化效率低并且存在安全问题**。比较常用的序列化协议有 Hessian、Kryo、Protobuf、ProtoStuff，这些都是基于二进制的序列化协议。

像 **JSON 和 XML 这种属于文本类序列化方式。虽然可读性比较好，但是性能较差**，一般不会选择。

### 如果有些字段不想进行序列化

使用`transient`关键词修饰，其作用：阻止实列中哪些用词关键词修饰的变量序列化，当对象被反序列化时，被`transient`修饰的变量值不会被持久化和恢复。

注意：

- 只能修饰变量，不能修饰类和方法
- 被修饰的变量，在反序列化之后会变成默认值
- static变量不属于任何对象，所以无论有没有`transient`关键字修饰，均不会被序列化。

## I/O

IO 即 `Input/Output`，输入和输出。数据输入到计算机内存的过程即输入，反之输出到外部存储（比如数据库，文件，远程主机）的过程即输出。数据传输过程类似于水流，因此称为 IO 流。IO 流在 Java 中分为输入流和输出流，而根据数据的处理方式又分为字节流和字符流。

Java IO 流的 40 多个类都是从如下 4 个抽象类基类中派生出来的。

- `InputStream`/`Reader`: 所有的输入流的基类，前者是字节输入流，后者是字符输入流。
- `OutputStream`/`Writer`: 所有输出流的基类，前者是字节输出流，后者是字符输出流。

### 为什么要分字节流和字符流

**不管是文件读写还是网络发送接收，信息的最小存储单元都是字节，那为什么 I/O 流操作要分为字节流操作和字符流操作呢？**

- 字符流是由 Java 虚拟机将字节转换得到的，这个过程还算是比较耗时；
- 如果我们不知道编码类型的话，使用字节流的过程中很容易出现乱码问题。

### IO设计模式

- 装饰器模式
- 适配器模式
- 工厂模式
- 观察者模式