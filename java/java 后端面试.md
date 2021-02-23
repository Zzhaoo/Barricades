# JAVA

## 软件开发原则

https://blog.csdn.net/qq_29676623/article/details/85530078

## 数据结构

#### 集合框架

![image-20210123112555324](/Users/a1466055840/Library/Application Support/typora-user-images/image-20210123112555324.png)

1. Collection类继承了Interable接口
2. Collection类的三个子类：List，Set，Queue
3. Vector是**线程安全**，支持**同步操作**的，而ArrayList不是
4. ArrayList和LinkedList最大的区别是链表实现和数组实现
5. Set是无序的
6. Stack是Vector的子类，支持empty(), peek(), pop(), push()方法
7. 优先队列的实现一般用堆的具体实现，且要传入类实现Comparable接口或者传入compare方法做诶参数
8. Queue的一个实现是LinkedList，方法包括add(), poll(), peek()

## JAVA基础

1. JDK和JRE有什么区别？

   JDK：Java Develpoer Kit，JRE：Java Runtime Environment，JRE包含了JVM和java最基础的类库如I/O、net等，而JDK则是用于给java开发者开发java程序的包，包括JRE和java编译器javac、调试器等

   <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200710192353421.png" alt="image-20200710192353421" style="zoom:50%;" />

2. ==和equals的区别？

   ==：

   对于基本类型来说：==是比较值是否一样，对于引用类型来说，是比较引用的地址是否一样

   equals：

   本质上就是==，但是String和Integer类等重写了该方法，变成了值比较

3. java基本类型和引用类型：

   基本类型：字符类型 char，布尔类型 boolean以及数值类型 byte、short、int、long、float、double

   引用类型：类，接口，数组，enum等

   

4. 两个对象的hashCode()相等，则equals()也一定为true？

   **hashCode()原理**：

   每次new Object()，JVM就会根据这个对象的hashcode值将Object放到hash列表的一个key中作为值，如果几个对象的hashcode一样，就会在那里形成一个单链表，所以可以出现hashCode相同但是实际上不同的情况

   

   **Object 的equals()方法**：

   ```java
   public boolean equals (Object o) {
   return this == o;
   }
   ```

   所以这句话是错的

5. final关键字的作用？

   final修饰的类：不能被继承

   final修饰的方法：不能被重写

   final修饰的变量：就是常量，必须当时就初始化，而且不能再被修改，存放在常量区

6. static关键字？

   static方法（类方法）：可通过类名调用，不可通过实例调用，只能访问static成员变量

   static变量（类变量）：只能通过类名访问，不能通过实例访问，可以被所有内部方法使用

7. 声明、定义、初始化、赋值、引用的区别？

   ```java
   int a; /*声明*/
   int b = 1;/*定义：初始化*/
   b = 3;/*赋值*/
   String s;/*声明了一个引用形变量s*/
   String s = null;/*定义：初始化引用形变量s*/
   String s = "123";/*定义：初始化引用形变量s，在String常量池中创建了“123”，然后将其指针存放到在栈中的s里*/
   String s = new String("123");/*定义：初始化引用形变量s，首先在堆中腾空间创建一个String对象，然后在String常量池中创建“123”，然后String对象指向“123”的地址，s之乡String对象的地址*/
   ```

   <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200710200641967.png" alt="image-20200710200641967" style="zoom:50%;" />

8. Math.round(-1.5)是多少？

   round的本质：离哪个整数近就是谁，如果是0.5，就向右取，所以应该是-1

   floor的本质：选择小于等于这个数的整数，类型为double

9. java操作字符有哪些？

    

10. args[]是什么？

   java TestClass a b c，这是一个正常的java命令，TestClass是类名，而a b c是参数，而args[]内存的也正是这些参数

11. java类初始化顺序？

    1. 初始化父类静态代码块，且只初始化一次

    2. 初始化子类静态代码块，且只初始化一次

    3. 初始化父类构造代码块

    4. 初始化父类构造方法

    5. 初始化子类构造代码块

    6. 初始化子类构造方法

       **特别的是，1. 子类调父类static方法/变量。2. 通过数组调用。3. 调用常量 这三个不会触发子类初始化**

12. 抽象类和抽象方法：

    * 抽象类不一定包含抽象方法

    * 抽象类的存在是为了继承，抽象类本身无法被实例化

    * 包含抽象方法一定是抽象类

    * 抽象方法长啥样？

      ```java
      public abstract int getNum();
      ```

    * 抽象类和普通类一模一样，除了类名前面是abstract class而不是class

    * 子类必须实现父类的抽象方法，除非子类也是抽象类

13. Java获取长度？

    * String: a.length();
    * Array: a.length;
    * List: a.size();

14. java四种引用类型？

    1. 强引用：一个对象赋给一个引用就是强引用，Object obj = new Object()
    2. 软引用：SoftReference类实现，不会轻易回收，内存不够时才会回收，一般用于缓存技术
    3. 弱引用：WeakReference类实现，只要GC启动就会回收
    4. 虚引用：用来在对象被回收时收到系统通知

15. java关键字？保留字？

16. 一些命令

    * jps：所有java进程
    * jstack：java栈情况
    * jmp：打印内存映射，制作堆文件
    * jstat：性能监控工具
    * jhat：内存分析工具
    * jconsole：很一般的控制台
    * jvisualvm：很强大的控制台

17. jsp内置对象？

    在JSP中一共预先定义了对象，分别为request、response、session、application、out、pageContext、config、page和exception

18. 实例变量，局部变量，类变量，final变量

    |           |                                  |                              |                     |                              |
    | --------- | -------------------------------- | ---------------------------- | ------------------- | ---------------------------- |
    | 实例变量  | 类的内部，方法外部               | 对象私有，对象没了自己就没了 | 可以通过set方法改动 | 有默认值                     |
    | 局部变量  | 方法内部                         | 随着方法块的结束消失         | 可以改动            | 无默认值，为初始化则无法使用 |
    | 类变量    | 类的内部，方法外部，static关键字 | 所有类共用一个               | 可以改动            | 有默认值                     |
    | final变量 | final关键词修饰                  |                              | 不可以改动          | final变量必须在声明时初始化  |

19. java三大注解？

    1. @Override：表示覆盖父类方法
    2. @Deprecated：表示不希望别人以后使用这个类，方法，变量
    3. @Suppresswarnings：抑制编译器警告

20. flush()函数？

    flush()函数用于强制输出缓冲区的字符字节流，所以所有的stream类都有flush()函数

21. 数值强制转化？

    小变大不用强制转化，大变小要强制转化，float和double比long要大

22. 权限？

    public > protected（包外子类也可以访问） > 包内 > private 

23. clone方法？

    java的clone方法是直接访问内存区域中的对象完成的，不会经过构造方法，类似于c++拷贝构造函数不调用构造函数一样

24. 系统只会在你没写构造函数的时候给你提供无参的构造函数

25. 子类可以继承父类的所有数据域和方法，但是父类的private方法子类无法调用（但是被继承了），父类的静态方法和静态属性无法被子类**重写**

26. java以Object为对象传入时，传的是**地址**，传入基本类型时，传的是**值**

## 容器

1. 最常见的考点：Collection类

   <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200727105402004.png" alt="image-20200727105402004" style="zoom:50%;" />

   * hashMap：线程不安全，继承自AbstractMap，hashMap的键可以为空，不直接使用对象的hashCode方法，遍历可以使用Iterator
   * CurrentHashMap：线程安全的hashMap，具体实现方法是把hashMap分成很多小的hashMap，对每个小的hashMap设置锁，实现线程安全
   * hashTable：线程安全（整表加锁），继承自Dictionary，键不可以为空，直接使用对象的hashCode，可以使用iterator遍历
   * ArrayList：线程不安全，基于动态数组（先申请10个，如果不够，就申请当前长度的1.5倍，然后copy过去），支持随机读写，但是插入和删除很困难
   * LinkedList：线程不安全，使用链表链接，所以内存浪费主要体现在存指针上，不支持随机读写，插入和删除很快
   * Vector：线程安全的
   * StringBuffer：线程安全的
   * Properties：线程安全的，实现Map接口

## 多线程

线程是CPU调度的最小单元

<img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200727111740992.png" alt="image-20200727111740992" style="zoom:50%;" />



#### 如何实现多线程

1. 继承Thread类，重写run()接口，调用.start()方法启动，.sleep()方法休眠，.setName()方法改名，记住调用run()方法不会报错，但不算是进程，只算是普通函数

   ```java
   public class CreateThreadDemo1 extends Thread {
   
       public CreateThreadDemo1() {
           // 设置当前线程的名字
           this.setName("MyThread");
       }
   
       @Override
       public void run() {
           // 每隔1s中输出一次当前线程的名字
           while (true) {
               // 输出线程的名字，与主线程名称相区分
               printThreadInfo();
               try {
                   // 线程休眠一秒
                   Thread.sleep(1000);
               } catch (Exception e) {
                   throw new RuntimeException(e);
               }
           }
       }
     
   }
   ```

   

2. 实现runable接口，将类传给new Thread()，再调用Thread类的方法操作

   runable接口只有一个方法：

   ```java
   package java.lang;
   @FunctionalInterface
   public interface Runnable {
       public abstract void run();
   }
   ```

   具体操作：

   ```java
   public class CreateThreadDemo4_Task implements Runnable {
   
       @Override
       public void run() {
   		// 每隔1s中输出一次当前线程的名字
           while (true) {
               // 输出线程的名字，与主线程名称相区分
               printThreadInfo();
               try {
                   // 线程休眠一秒
                   Thread.sleep(1000);
               } catch (Exception e) {
                   throw new RuntimeException(e);
               }
           }
       }
         private static void printThreadInfo() {
           System.out.println("当前运行的线程名为： " + Thread.currentThread().getName());
       }
     
     
     public static void main(String[] args) throws Exception {
           // 实例化线程任务类
           CreateThreadDemo4_Task task = new CreateThreadDemo4_Task();
   
           // 创建线程对象,并将线程任务类作为构造方法参数传入
           new Thread(task).start();
   
           // 主线程的任务，为了演示多个线程一起执行
           while (true) {
               printThreadInfo();
               Thread.sleep(1000);
           }
   }
   ```

   

3. 方法内新建Thread类，实现方法内的多线程

   ```java
   public static void main(String[] args) {
           // 基于子类的方式
           new Thread() {
               @Override
               public void run() {
                   while (true) {
                       printThreadInfo();
                   }
               }
           }.start();
   
           // 基于接口的实现
           new Thread(new Runnable() {
               @Override
               public void run() {
                   while (true) {
                       printThreadInfo();
                   }
               }
           }).start();
   			// 同时实现会采用基于子类的方式，因为本身基于接口的方法可以实现是因为Thread run()方法的调用，但你重写了run()之后也就不会调用了
   ```

   

4. 计时器Timer类

   ```java
   public static void main(String[] args){
   
           // 创建定时器
           Timer timer = new Timer();
   
           // 提交计划任务
           timer.schedule(new TimerTask() {
               @Override
               public void run() {
                   System.out.println("定时任务执行了...");
               }
           },format.parse("2020-10-11 22:00:00"), 1000);
       }//指定时间，指定间隔时间重复运行
   }
   ```

5. 线程池，作用是利用了缓存技术，线程资源是宝贵的，将线程储存在线程池中

#### 线程安全

当一个线程对一个变量同时要读和写时，就需要用到锁

![img](https://img-blog.csdnimg.cn/20181122101753671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F4aWFvYm9nZQ==,size_16,color_FFFFFF,t_70)

## 反射

## 对象拷贝

## JAVA Web 模块

JSP

#### Spring Boot自动配置

Spring Boot的启动类注解：@SpringBootApplicztion封装了@EnableAutoConfiguration注解，该注解的作用就是使得自动配置生效

@EnableAutoConfiguration封装了@Import，导入了AutoConfigurationImportSelector类，该类的selectImports()会扫描整个项目内有**META-INF/spring.factories**的jar包

spring.factories内是一组一组的key-value对，value为XxxxAutoConfiguration的类名

这些XxxxAutoConfiguration文件都是有@Configuration注解的，也就是说都是配置类，用于导入bean，而且用@Conditional指定配置生效条件，达到生效条件才会被实例化，否则只是注册，用@EnableConfigurationPropertier(属性bean)指定全局属性。**所以我们现在只要在application.yml中做少量的属性配置就行了，因为大多数的属性配置都已经被spring boot写好，组装成bean了，可以自动配置**

属性bean指用@ConfigurationProperties(配置文件)注解的类

#### Spring Boot的Servlet

Spring Boot的Servlet已经不用我们自己继承Servlet和Filter类，以及用ServletIntize类启动（Servlet3.0），更不用xml指定。而是在Spring-Boot-start-parent和spring-boot-start-web中帮我们实现好了（为了使得war包和jar包都可以正常启动servlet）



Request会到tomcat容器中，tomcat容器会选择合适的servlet来处理request，servlet咨询handle（存放了url——controller对应表），选择合适的controller处理，并将返回的model和view组装成完整的html返回

#### IOC

@SpringBootApplication = @ComponentScanner + @Configuration + @EnableAutoConfiguration

@ComponentScanner用于扫描当前项目下的所有bean

@Configuration用于表明该类是配置类，包含@Bean，可以向Spring IOC容器注册bean

@EnableAutoConfiguration用于自动配置

#### 依赖注入

三种注入位置，单例模式

#### AOP

Advice：干什么，什么时候

PointCut：什么地方

## 异常模块

![image-20200727170509487](/Users/a1466055840/Library/Application Support/typora-user-images/image-20200727170509487.png)

**运行时异常**： 都是RuntimeException类及其子类异常，如NullPointerException(空指针异常)、IndexOutOfBoundsException(下标越界异常)等，这些异常是不检查异常，程序中可以选择捕获处理，也可以不处理。这些异常一般是由程序逻辑错误引起的，程序应该从逻辑角度尽可能避免这类异常的发生。

> 运行时异常的特点是Java编译器不会检查它，也就是说，当程序中可能出现这类异常，即使没有用try-catch语句捕获它，也没有用throws子句声明抛出它，也会编译通过。 

**非运行时异常 （编译异常）**： 是RuntimeException以外的异常，类型上都属于Exception类及其子类。从程序语法角度讲是必须进行处理的异常，如果不处理，程序就不能编译通过。如IOException、SQLException等以及用户自定义的Exception异常，一般情况下不自定义检查异常。



1. finally与try/catch中的return冲突怎么办？

   finally中的语句一定会被执行，**如果finally中有return，则进行覆盖。否则会将try中的return的值临时储存，finally结束后再返回**

2. 虚拟机栈可能报的异常？

   * StackOverflowError：栈帧数大于允许的栈深度
   * OutOfMemory：栈空间可以动态拓展，但是无法申请到足够内存时会报该异常

## 网络模块

1. cookie位于头部中，可用request.getCookies和request.getHeader获取

![image-20200727172129536](/Users/a1466055840/Library/Application Support/typora-user-images/image-20200727172129536.png)

## 设计模块

------

# 框架

## Spring

### * Spring MVC

### * Spring Boot

### * Spring Cloud

## Hibernate

## Mybatis

## 中间件

### * RabbitMQ

### * Kafka

###  * Zookeeper

## 数据

### Mysql



### Redis

------

# JVM

#### JVM内存管理（JMM）

![10006199-a4108d8fb7810a71](https://upload-images.jianshu.io/upload_images/10006199-a4108d8fb7810a71.jpeg)

1. 程序计数器：线程私有，一个寄存器，指示当前线程运行到了哪一行

2. 虚拟机栈：线程私有，每个方法都会创建一个**栈帧**，**栈帧**里有当前方法的返回地址、局部变量表（局部变量表内的数据类型：基本数据类型和引用类型。且每个方法局部变量表的大小在编译时已经确定）、操作数、动态链接

3. 本地方法栈：和虚拟机栈一样，但是是给本地C/C++等native方法用的

4. JAVA堆：对象实例

5. 方法区：

   | Class               |                                                              |
   | ------------------- | ------------------------------------------------------------ |
   | 类型信息            | 包括完整名称，父类名称，实现的接口列表，修饰符               |
   | 类型常量池          | 包括字面值（编译期间确定的值，如final变量）和符号引用        |
   | 字段信息            | 声明的顺序，修饰符，类型，名字                               |
   | 方法信息            | 声明的顺序，修饰符，返回值类型，名字，参数列表，异常表，方法字节码，操作数栈和局部变量表大小 |
   | 类变量              | static变量                                                   |
   | 指向类加载器的引用  | 用于加载类                                                   |
   | 指向Class实例的引用 | 一个实例的引用列表                                           |
   | 方法表              | 有点类似虚函数表，存放对实例方法的直接引用，JVM可以从这里直接调实例方法 |

   





1. 字符串常量池

   JVM为了减少字符串的重复构建而维护的一块特殊内存，当代码创建字符串对象时，JVM首先会对对字面量进行检查，如果字符串常量池中存在这个字符串对象的**引用**，那么就将这个字符串对象的**引用**返回，否则新的字符串对象被创建，**引用**被放入常量池。**要注意的是，String对象是不可变的，你可以让一个字符串的引用指向新的字符串对象，但你不可以改变字符串对象，所以常量池才能正常工作，否则一个引用改变就会导致所有引用改变**

2. 堆/栈

   堆中存放的是所有JVM创建的**实例对象和数组**，而栈中存放的是方法调用和引用

   ```java
   Object o = new Object();
   //很显然，o存在栈中，而new Object出的对象存在堆中
   ```

   

3. 寄存器

   java运行时数据区有一个**程序计数器**，该寄存器是线程私有的，用来记录当前线程正在执行的指令

#### JVM垃圾回收

https://www.jianshu.com/p/76959115d486

* 哪些内存需要回收？

  1. 程序计数器/栈这些随线程产生而产生，随线程结束而消失的内存不需要过多考虑回收
  2. JAVA堆和方法区作为共享区域，要重点考虑回收

* 对象什么时候回收？

  1. 引用计数算法：给每个对象添加一个引用计数器。其他地方对其有引用时+1，引用失效时就-1，到0就可以回收（缺点：A引B，B引A，但AB都不被使用，此时AB都不可回收）

  2. 可达性分析算法：通过GC Boots对象能否到达这个对象，如果不能到达这个对象，就把它回收，GC Boots包含：

     | 位置       | 对象                              |
     | ---------- | --------------------------------- |
     | 虚拟机栈   | 本地变量表                        |
     | 本地方法栈 | JNI引用的对象                     |
     | 方法区     | 静态属性引用对象（1.8后为元空间） |
     | 方法区     | 常量引用对象（1.8后为元空间）     |

* 方法区啥时候回收？

  1. 该类所有实例被回收
  2. 加载该类的ClassLoader被回收
  3. 该类的java.long.Class对象没有在任何地方被引用

* 如何回收？

  1. **标记-清除算法**

     1. 标记阶段：首先通过GC Boots可到达的不用回收，不可到达的全部标记
     2. 清除阶段：清除所有被标记的对象

     <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200728111808835.png" alt="image-20200728111808835" style="zoom:50%;" />

  2. **标记-复制算法**

     1. 标记阶段：同上
     2. 复制阶段：将原有的内存空间分为两块，每次只使用一块，在垃圾回收时，将正在使用的内存中的**存活对象**复制到未被使用的内存块中，然后清除正在使用的内存块中的**所有对象**

     <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200728111829805.png" alt="image-20200728111829805" style="zoom:50%;" />

  3. **标记-整理算法**

     1. 标记阶段：同上
     2. 整理阶段：将所有存活对象压缩到一个统一区域，然后清理外面所有空间

     <img src="/Users/a1466055840/Library/Application Support/typora-user-images/image-20200728111911851.png" alt="image-20200728111911851" style="zoom:50%;" />

  4. **分代收集算法（目前大部分都是用这个）**

     1. 将内存区域按生命周期分为老年区和新生区
     2. 老年区对象生命周期长，每次回收只有少量对象要被回收
     3. 新生区对象生命周期短，每次回收都有大量对象要被回收，长期存活的新生代会变为老年代
        * 新生区分为eden（伊甸）、to Survivor和from Survivor三个区域
        * 所有新的实例都在eden区，eden满了触发GC
        * GC将eden和from Survivor存活对象复制到to survivor，然后清理前两个区
        * 颠倒此时两个Survivor的名字（两个Survivor是为了解决碎片化）
     4. 所以对老年区采用**标记-清理法**，对新生区采用**标记-复制法**

* 垃圾收集器

  这是对垃圾回收方法的具体实现

  | Serial（新生代）            | 单线程，运行时要停掉其他线程                                 |
  | --------------------------- | ------------------------------------------------------------ |
  | ParNew（新生代）            | 多线程的Serial                                               |
  | Parallel Scavenge（新生代） | 采用标记-复制，多线程，注重吞吐量（代码运行时间 / (代码运行时间 + 垃圾收集时间)） |
  | Serial Old                  | 标记-整理，单线程                                            |
  | Parallel Old                | 标记-整理，和Parallel Scavenge可以组成吞吐量最高的组合       |
  | CMS                         | 标记-清除，重视响应，支持并发，需要多核CPU                   |
  | G1                          | G1 GC 使用并发和并行阶段实现其目标暂停时间，并保持良好的吞吐量。当 G1 GC 确定有必要进行垃圾回收时，它会先收集存活数据最少的区域（垃圾优先)，g1的特别之处在于它**强化了分区**，弱化了分代的概念，是区域化、增量式的收集器，它不属于新生代也不属于老年代收集器。用到的算法为标记-清理、复制算法 |

  回收模式：

  * Minor GC：年轻代
  * Major GC：老年代
  * FULL GC：统一回收
  * mixed gc：G1特有的，收集整个young gen以及部分old gen的GC

  stop the world具体是什么，有没有办法避免？

  * stop the world简单来说就是gc的时候，停掉除gc外的java线程。
  * 无论什么gc都难以避免停顿，即使是g1也会在初始标记阶段发生，stw并不可怕，可以尽可能的减少停顿时间。