（资源一）[[尚硅谷Java零基础视频教程(宋红康主讲)]](https://www.youtube.com/watch?v=v_Rcib9_VyQ&list=PLjbISPgF5zwIaAYG7KfYq3N2N6p_zuT3z)

（资源二）[廖雪峰官网Java](https://www.liaoxuefeng.com/wiki/1252599548343744/1264738568571776)

（资源三）[2020年黑马 Java 基础教程 IDEA 版](https://www.youtube.com/watch?v=4nMUFCR-lbg&list=PLD3Xyx6ef38wYlxahZ1RRgwAMjCm1ze7V&index=6)

【看 Mac 是 x86 还是 arm】

```bash
$name -a
 =>Darwin MacBook-Pro.lan 21.3.0 Darwin Kernel Version 21.3.0: Wed Jan  5 21:37:58 PST 2022; root:xnu-8019.80.24~20/RELEASE_X86_64 x86_64
```

【'Git is not installed' on IntelliJ】

```bash
$which git
=> /usr/local/bin/git
Set'Path to Git executable' in the Preferences > Version Control > Git
```

【安装 brew】- https://brew.sh/

```bash
$/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
$brew --version
 ==> Homebrew 3.5.2
$brew install git 
 ==> git version 2.32.1 (Apple Git-133)
```

【卸载 java16】

```bash
$ls ~/Library/Java/JavaVirtualMachines/
$sudo rm -rf ~/Library/Java/JavaVirtualMachines/jdk-16.0.1.jdk
```

卸载并重装 jdk11

Oracle：JDKLisa22!

想知道 java 具体安装到哪个目录，可以执行

```bash
$/usr/libexec/java_home -V
```

会得到以下输出-> 

``` bash
Matching Java Virtual Machines (2):
    17.0.2 (x86_64) "Oracle Corporation" - "OpenJDK 17.0.2" /Users/lisahuang/Library/Java/JavaVirtualMachines/openjdk-17.0.2/Contents/Home
    11.0.14.1 (x86_64) "Amazon.com Inc." - "Amazon Corretto 11" /Users/lisahuang/Library/Java/JavaVirtualMachines/corretto-11.0.14.1/Contents/Home
/Users/lisahuang/Library/Java/JavaVirtualMachines/openjdk-17.0.2/Contents/Home
```

上面两个是已安装的`jdk`目录地址
最下面一个是目前Mac默认使用的`jdk`版本目录地址

更改默认版本 - 在终端运行

```bash
$ export JAVA_HOME=$(/usr/libexec/java_home -v 11.0.14.1)
```

如果想永久生效，那就把命令加入到你的 .bash_profile 文件中，文件更新后为

```bash
# Setting PATH for Python 3.9
# The original version is saved in .bash_profile.pysave
PATH="/Library/Frameworks/Python.framework/Versions/3.9/bin:${PATH}"
export PATH

#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
export SDKMAN_DIR="$HOME/.sdkman"
[[ -s "$HOME/.sdkman/bin/sdkman-init.sh" ]] && source "$HOME/.sdkman/bin/sdkman-init.sh"

GRADLE_USER_HOME=~/Documents/gradle_repo
JAVA_HOME=~/Library/Java/JavaVirtualMachines/corretto-11.0.14.1/Contents/Home/
PATH="$JAVA_HOME/bin:$PATH:$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin"
CLASSPATH="$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:."

export GRADLE_USER_HOME
export PATH=$PATH:usr/local/mysql/bin
export CLASSPATH
export JAVA_HOME
```

让配置生效

```bash
$source ~/.bash_profile
```

Zsh Terminal 新开窗口后，java -version 还是老的，需要：将 .bash_profile 的内容复制到 .zshrc 中

```bash
$ps -p $$
 =>
   PID TTY           TIME CMD
 5941 ttys000    0:00.12 -zsh
```

【Spring Boot】

**开发的系统需要具有**：

高可用：稳定不容易down - Multi Avaliability Zone

高性能

易扩展

可伸缩

且安全

**xJwt token**



**Merge 的三种方式：**

Squash & merge: 看不到历史记录，只保留一次commit

Rebase

...

【Run the App】

```bash
$./gradlew bootRun
```

【Java 推荐书籍】/ Gotlin

Thinking in Java

Effective Java

Head First Design Patterns

【Tiger 课堂 3-20 SQL Design】

docker、docker-compose 讲解

dto - 跟前端有关

dto 和 entity 有mapping

autowire ？？？

// 数据库设计原则

​	Column 不可再分割

​	每个表要有 primary key，无意义 - 关系型数据库（非关系型不是这样）

​	

【Tiger 课堂 3-16】

Tiger 使用 java11,  java11 是 AWS Lambda 支持的版本

先装 gradle，再装 jdk

真正开发时，不用自己新建项目，一般用 Spring（事实上的标准）；

gradle 目录 ～ 前端 nvm

class名称 大写开头

Generate / Getter & Setter

8 primitive types: byte int short boolean ...

Spring initialiser / Gradle + Lombok && Spring Web

Lombok @Getter @Setter @Data -- 自动导入

Gradle / build / build --> build 目录，包括 .class 文件

Debug - Evaluate Expression / Null pointer exception

两个 String 用 equals() 而不是用 == 来比较，== 返回 true 的原因 待查  if("xiao".equals(user.getName()))

【Tiger课堂 3-17 Restful API】

Spring Initialiser 使用 + 代码目录结构 讲解 2:54'01"

代码范例1：Tic Tac Toe

代码范例2：wholesale - 包含 CI/CD pipeline 

CI/CD pipeline + AWS + Jenkins + Kubernetes

【Tiger 课堂 3-18 Docker】

实体机 --> VM --> Docker Container

AWS / EC2 可以看作是 VM，

Docker file - repo 下面有一个，描述了怎么 build 该app 的 docker image

Docker compose up - 可以在本地启动所有app，好像整个系统的环境, 

==> docker-based app 已经成为事实上的标准

任何一个 container 都是基于一个 docker image

可从 Docker Hub 下载(pull) docker image

```bash
$docker ps
$docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5431:5432 postgres
```

pgAdmin -- web-based client 端，安装后，可以建一个 server，在 server 里面可以与启动的数据库进行连接，可以看到数据库表

pgAdmin: Master - db

PostgreSQL: 　server - master

postgres/postgres: admin - cheetah

【Tiger 课堂 3-25 Message Driven】

Server to server talk, host to host talk

microservice 之间不 share 数据库

【Tiger 课堂 3-18 SQL】

非关系型 NoSQL: MongoDB, LevelDB, Redis...

关系型 SQL: Sqlite, MySQL, PostgreSQL, SQL Server...

一个数据库通常包含一个或多个表，每个表有名字，包含若干条记录；

SQL - 结构化查询语言 是访问 SQL 数据库的标准语言，是一门 ANSI 的标准计算机语言；

SQL 语法：对大小写不敏感，某些数据库系统要求在每条 SQL 命令后加分号，可以分行；

DDL - 数据定义语言

```
- create database database_name //建库
- create table table_name  //建表
	(
	列名1 数据类型,
	列名2 数据类型,
	)
- alter table 改表
- drop table 删表
- create index //创建索引（搜索键）index 可以重复，用于查询提高性能
 `daretime` on `price_history`(`datetime`)
- drop index 删索引
```

DML - 数据操作语言

```
- select first_name, last_name from actors//从数据库表中获取数据
where first_name like 'P_'
where first_name like 'Pe%'
where first_name is not null
where first_name > 'P'
where movie_length between 90 and 120
where first_name in ('John', 'Tom')
where first_name not in ('John', 'Tom')

order by first_name asc / desc //升 降序

limit 5 //取前 5 条记录
limit 5 offset 3 //跳过 3 条
fetch first 10 row only

- select distinct last_name from actors
- select count(*) from actors 
- select movie_lang, count(movie_lang) from movies 
group by movie_lang 
having count(movie_lang) > 1
- update //改数据库表数据
- delete //删除
- insert into //插入
```

连接

```bash
// inner join ... on ... -- ‼️ 每个项目都会用到
select dir.director_is, dir.first_name, mo.movie_name from director dir
inner join movies mo on dir.director_id=mo.director_id
// left/right (outer) join 
select dir.director_is, dir.first_name, mo.movie_name from director dir
left join movies mo on dir.director_id=mo.director_id
==> 会显示左/右边表（director/movie）所有的 记录，就算 movie 里面没有的，包含 inner join 的结果
// full join - 不怎么使用
```

【Tiger 课堂 3-19】-- demo 讲解 + Service //...待复习

Intelli + Spring：不需要手工写 import，会自动导入

ResponseEntities.ok - http 请求 200 // 在 Restful API 讲到过 复习...

// 范例代码

tictactoe / src / main / resources / application-posstgresql.properties 连数据库的

需要改名为：application.properties

// 基本知识点：

400 - bad request

403 - access denied

作业：调通 要求 1:59’

// 分页功能的实现：

第一种：从后端一次申请所有，client 端来实现分页逻辑

第二种：从后端申请当前页需要的，然后在前端显示

Spring Boot 中：调用 Page< T> findAll(Pageable pageable) 即可实现分页，很简单；

 实际工作中：主要使用 @Query - JPQL，也可以使用 native sql，参考官网

安装 Postman，多人可以 share 同一个

New Collection / new API => export ***Collection.json，别人可以 import 

可参考范例：wholesale / postman

连接多个数据源 - 使用机会不多

【Tiger课堂 3-25 MD】1:37'32"

Dead Letter Queue - DLQ

AWS - SQS / FIFO / fanout / SNS / Lambda (小工具) / ECS / EKS / RDS

```bash
// docker 下启动 rabbitmq
$docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management

// 浏览器 http://localhost:15672/ 进入登录界面
login user/pwd:guest/guest
// Queues / Add queue - Mobile
// 代码 rabbitmq-publisher
运行
Postman --> publisher --> rabbitmq --> listener
            8080           5672
// 代码 rabbitmq-listener
@RabbitListener(queue = "Mobile")
```

listener 里面：

implements Serializable - 如果想要 msg 能传输，必须如此，因为 java bean 是存在硬盘上的；包名定义与 publisher 一致；

NPPA - 澳洲新支付平台 New Payments Platform

```bash
// 如果不用上面 docker 的版本
// Install homebrew
$brew update
// Install rabbitmq using homebrew
$brew install rabbitmq
// Install Erlang if there is Erlang download failure
$brew install erlang or brew reinstall erlang
// Run below command to fix issue "Error: Could not symlink sbin/cutterfish/usr/loacl/sbin is not writable" 
$sudo chown -R 'whoami':admin /usr/local/sbin
$sudo mkdir /usr/local/sbin
$brew link rabbitmq
// Check all the rabbitMQ folders and files
$cd /usr/local/sbin/
// Start broker
$sh rabbitmq-server
```

交换机

交换机的功能主要是接收消息并转发到绑定的队列，交换机不存储消息，在启用 ack 模式后，交换机找不到队列，会返回错误。交换机有四种类型：Direct、Topic、Headers 和 Fanout；

Direct：先匹配再投送，即在绑定时设定一个 routing key，消息的 routing key 匹配时，才会被交换机投送到绑定的队列中去；

Topic：按规则转发消息（最灵活）；

Headers：设置 header attribute 参数 交换机；

Fanout：转发消息到所有绑定队列。

【Tiger课堂 3-27】测试 + 后端架构

unit test - 不能连接外部的资源，如果测试连接数据库，用 H2，配置好当 跑测试的时候，H2 也开始跑

Mockito - mock 单元测试中使用的其他函数

service 测试 参照 wholesale 的写法 [21'25"]

【微服务 Microservices】

语言无关性

可以用 Restful API 的形式提供

是和 container based app 结合的，一个 app 是一个可以被 dockerised 的 container

【 JDK 检查 及 配置】

MAC 的 JDK 自己带了，检查版本

```
$ java -version
java version "16.0.1" 2021-04-20
```



bin目录下存放 JDK 用于开发的一些终端命令工具。

​	“javac” -- 将java源文件编译为class文(即自解码文件)；

​	“java” -- 运行class文件。

include目录下是一些C语言的头文件；

lib目录下存放JDK开发工具所依赖的一些库文件；

man目录下存放JDK开发工具的说明文档。



**需要配置的环境变量（windows环境下）：**

**JAVA_HOME** -- C:\Program Files (x86)\Java\jdk1.8.0_91     // 要根据自己的实际路径配置

**CLASSPATH** --  .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;     //记得前面有个"."

**Path** -- %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;

**编辑配置文件**

```
$ open -e .bash_profile
$ vi ~/.bash_profile. //打开文件并修改
```

打开文件 并 修改，将下面的配置信息输进去

```
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-16.0.1.jdk/Contents/Home
PATH=$JAVA_HOME/bin:$PATH:.
CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
export JAVA_HOME
export PATH
export CLASSPATH
```

保存并关闭窗口；

查看配置是否成功：

```
$ source .bash_profile  //让配置文件生效
$ java -version

$ env | grep "Java" //环境变量 中 查找带 “Java”的
```

 **查看已安装的jdk路径的方法** 

```
$/usr/libexec/java_home -V
```

 

【JDK 安装】

JDK 的安装目录 bin 下面存放了 JDK 的各种工具命令，javac 和 java 就放在这个目录；其他目录包括 conf、include、jmods、legal、lib、man、release

env 可以查看环境变量

env | grep "jdk" 查看环境变量里面包含 “jdk” 的部分

JAVA_HOME 为：/Library/Java/JavaVirtualMachines/jdk-16.0.1.jdk/Contents/Home

Path 环境变量的配置，解决的问题 - javac 和 java 工具 和需要编译的代码不在相同目录下；如果配置后，能够在任意的位置 都能 找到 bin 目录下的 javac 和 java 工具；

Windows 下面 Win+E 打开我的电脑，配置环境变量，系统变量 新建 JAVA_HOME = D:\Develop\jdk16 不带 bin；

系统变量 Path，编辑 补充：%JAVA_HOME%\bin;

网页：通过浏览器将数据展示在用户面前，跟后台服务器没有交互；

网站：通过跟后台服务器的交互，将查询到的真实数据再通过网页展示出来； 

【跨平台原理】Java 程序可以在任意操作系统上运行

平台：操作系统

.net 只能跑在 windows 系统上

JVM 虚拟机，一款软件，不同的版本可以安装在不同操作系统上；

JVM 虚拟机不允许跨平台，允许跨平台的是 Java 程序

【JRE & JDK】

Java 程序开发的三步骤：写代码、编译代码（使用 Java 提供在 JDK中的工具）、运行代码

​                                  .java 源文件  -->  .class 字节码文件

**写代码：**

Java JRE 运行时环境 = JVM 虚拟机 + Java 核心类库（Java 已经写好的，非常核心的，代码仓库）

我们在编写代码的过程中，需要使用到 java 存放在 JRE 中，已经写好的 java 文件；

**编译 & 运行 代码：**

Java Development Kit 软件开发工具包，包含了：编译工具 和 运行工具；

代码需要运行在 JVM 当中；

JDK = 开发工具 + JRE （ JVM + 核心类库）

Java规定，某个类定义的`public static void main(String[] args)`是Java程序的固定入口方法，因此，Java程序总是从`main`方法开始执行。

```
/**
 * 可以用来自动创建文档的注释
 */
public class Hello { //类名大写开头
    
    //Java入口程序规定的方法必须是静态方法，方法名必须为main，括号内的参数必须是String数组。
    public static void main(String[] args) { //方法名小写开头
        // 向屏幕输出文本:
        System.out.println("Hello, world!");
        /* 多行注释开始
        注释内容
        注释结束 */
    }
} // class定义结束

```

Java是面向对象的语言，一个程序的基本单位就是`class`，`class`是关键字，这里定义的`class`名字就是`Hello`；此处Hello前若不写`public`，也能正确编译，但是这个类将无法从命令行执行。

- java：这个可执行程序其实就是JVM，运行Java程序，就是启动JVM，然后让JVM执行指定的编译后的代码；
- javac：这是Java的编译器，它用于把Java源码文件（以`.java`后缀结尾）编译为Java字节码文件（以`.class`后缀结尾）；
- jar：用于把一组`.class`文件打包成一个`.jar`文件，便于发布；
- javadoc：用于从Java源码中自动提取注释并生成文档；
- jdb：Java调试器，用于开发阶段的运行调试。

【编码格式】注意遵守Java社区约定的编码格式

那约定的编码格式有哪些要求呢？其实我们在前面介绍的Eclipse IDE提供了快捷键`Ctrl+Shift+F`（macOS是`⌘+⇧+F`）帮助我们快速格式化代码的功能，Eclipse就是按照约定的编码格式对代码进行格式化的，所以只需要看看格式化后的代码长啥样就行了。具体的代码格式要求可以在Eclipse的设置中`Java`-`Code Style`查看。

【classpath】

JVM通过环境变量`classpath`决定搜索`class`的路径和顺序；

不推荐设置系统环境变量`classpath`，始终建议通过`-cp`命令传入；

如果我们 Java 编译后的class文件不在当前目录，我们可以使用 -classpath 或 -cp 来指定class文件目录

```
C:> java -classpath C:\java\DemoClasses HelloWorld
```

如果class文件在jar文件中，则命令如下：

```
c:> java -classpath C:\java\myclasses.jar
```

在IDE中运行Java程序，IDE自动传入的`-cp`参数是当前工程的`bin`目录和引入的jar包。

codetest-demo项目打出的jar包结构如下：

![Pasted Graphic 4](/Users/lisahuang/Library/Group Containers/group.com.apple.notes/Media/1EB84007-8D39-401E-85E2-08C0839290CD/Pasted Graphic 4.tiff)

`/META-INF/MANIFEST.MF`文件中`MANIFEST.MF`是纯文本，可以指定`Main-Class`和其它信息；

JVM会自动读取这个`MANIFEST.MF`文件，如果存在`Main-Class`，我们就不必在命令行指定启动的类名，而是用更方便的命令：

```bash
java -jar codetest-demo.jar
```





**方法的命名：**

方法的名字的第一个单词应以小写字母作为开头，后面的单词则用大写字母开头写，不使用连接符；

下划线可能出现在 [JUnit 测试]()方法名称中用以分隔名称的逻辑组件。一个典型的模式是：**test<MethodUnderTest>_<state>**，例如 **testPop_emptyStack**。

Java语言支持的变量类型有：

- 类变量：独立于方法之外的变量，用 static 修饰。
- 实例变量：独立于方法之外的变量，不过没有 static 修饰。
- 局部变量：类的方法中的变量 -- 在方法、构造方法、或者语句块被执行的时候创建，当它们执行完成后，变量将会被销毁；在栈上分配；没有默认值，所以必须初始化。

```java
public class Variable{
    static int allClicks=0;    // 类变量
    String str="hello world";  // 实例变量
    public void method(){
        int i =0;  // 局部变量
    }
}
```



```java
//创建对象
public class Puppy{
   public Puppy(String name){
      //这个构造器仅有一个参数：name
      //调用系统类 System 中的标准输出对象 out 中的方法 println()
      System.out.println("小狗的名字是 : " + name ); 
   }
   //main 方法是被 JVM 调用的，这是与其他方法的区别；
   public static void main(String[] args){
      // 下面的语句将创建一个Puppy对象
      Puppy myPuppy = new Puppy( "tommy" );
   }
}
```

【**修饰符-final**】

对象可以赋值的位置：

1.默认初始化

2.显示初始化 / 5.在代码块中赋值

3.构造器中初始化

4.有了对象以后，通过 "对象.方法" 的方式进行赋值

final -- 修饰的变量为常量，是不可修改的；

用`final`修饰`class`可以阻止被继承；

用`final`修饰`method`可以阻止被子类覆写；

用`final`修饰`field`可以阻止被重新赋值，可以考虑赋值的位置：2 5 3；

用`final`修饰局部变量可以阻止被重新赋值。



static -- 声明独立于对象的静态变量（类变量），无论一个类实例化多少对象，它的静态变量只有一份拷贝；

```java
//数组 作为 函数 返回值
public static int[] reverse(int[] list) {
  int[] result = new int[list.length];
 
  for (int i = 0, j = result.length - 1; i < list.length; i++, j--) {
    result[j] = list[i];
  }
  return result;
}
```

```bash
./gradlew run  //运行gradle下的java程序
```

**javadoc** 工具将你 Java 程序的源代码作为输入，输出一些包含你程序注释的HTML文件。//...

【使用JDK Logging】

java.util.logging.Logger使用详解 - https://www.cnblogs.com/lukelook/p/8646908.html

```java
Logger logger = Logger.getLogger("LoggerLog");
logger.setLevel(Level.INFO);

try {
  //add fileHandler
  FileHandler fileHandler = new FileHandler(".//log//logMain.md");
  fileHandler.setLevel(Level.INFO);
  //设置 log 记录格式，缺省 xml 
  fileHandler.setFormatter(new MyFormat());

  //add fileHandler to logger
  logger.addHandler(fileHandler);
}
 
public class MyFormat extends Formatter {

    @Override
    public String format(LogRecord log) {
      // TODO Auto-generated method stub
      SimpleDateFormat format = new SimpleDateFormat("YYYY-MM-dd HH:mm:ss S");

      return log.getLevel() + ": " + format.format(log.getMillis())+" " + log.getMessage() +"\n";
  }

}
```

【Commons Logging】一个第三方日志库，是由Apache创建的日志模块

Commons Loggin自动搜索并使用Log4j（Log4j是另一个流行的日志系统），如果没有找到Log4j，再使用JDK Logging。

第一步，通过`LogFactory`获取`Log`类的实例； 第二步，使用`Log`实例的方法打日志。

```java
import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;

public class Main {
    public static void main(String[] args) {
        Log log = LogFactory.getLog(Main.class);
        log.info("start...");
        log.warn("end.");
    }
}
```

上面的用法在gradle项目中编译不过，

【Log4j2 实战】

（资源）slf4j、log4j、log4j2、logback到底用哪些jar   https://www.jianshu.com/p/34acd3d3da1c

（资源）Log4j 2环境配置和适配组件配置（maven/ivy/gradle）http://www.noobyard.com/article/p-rreqfhaf-cs.html

这就是slf4j和其他框架的组合：

使用slf4j需要首先导入**slf4j-api.jar**；

和log4j配合，要导入**log4j.jar**，以及他们之间的桥接包**slf4j-log412.jar**；

和log4j2配合，导入桥接包**log4j-slf4j-impl.jar**和log4j2的**log4j-api.jar**、**log4j-core.ja**r；

logback只需要导入**logback-classic**和**logback-core.jar**即可，不需要桥接包。



```java
//使用 Log4j2 的步骤：
//1. build.gradle 增加：
    implementation 'org.apache.logging.log4j:log4j-api:2.17.2'
    implementation 'org.apache.logging.log4j:log4j-core:2.17.2'
    testImplementation 'org.slf4j:slf4j-log4j12:2.0.0-alpha6'
    implementation 'org.slf4j:slf4j-api:2.0.0-alpha6'
    
    //👆写法来自Maven
    //https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-slf4j-impl/2.17.2

//2. import      
import lombok.extern.log4j.Log4j2;
//3. 注解
@Log4j2
pulilc class Bundle(){
		private BundleBreakdown minNumBtwIndex(int targetNum, int preIndex) {
      //4. 使用
        log.info("minNumBtwIndex targetNum = " + targetNum + " preIndex = " + preIndex);
}
```

SLF4J和Logback可以取代Commons Logging和Log4j；

始终使用SLF4J的接口写入日志，使用Logback只需要配置，不需要修改代码。



作者：Seven0007_
链接：https://www.jianshu.com/p/34acd3d3da1c
来源：简书

在Java 9之前，`.class`文件是JVM看到的最小可执行文件，而一个大型程序需要编写很多Class，并生成一堆`.class`文件，很不便于管理，所以，`jar`文件就是`class`文件的容器。一个大型Java程序会生成自己的jar文件，同时引用依赖的第三方jar文件，而JVM自带的Java标准库，实际上也是以jar文件形式存放的，这个文件叫`rt.jar`，一共有60多M。jar只是用于存放class的容器，它并不关心class之间的依赖。

从Java 9开始引入的模块（Module），主要是为了解决“依赖”这个问题。

【Maven】

Maven就是是专门为Java项目打造的管理和构建工具，它的主要功能有：

- 提供了一套标准化的项目结构；
- 提供了一套标准化的构建流程（编译，测试，打包，发布……）；
- 提供了一套依赖管理机制。

```ascii
a-maven-project
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   └── test
│       ├── java
│       └── resources
└── target
```

项目的根目录`a-maven-project`是项目名，它有一个项目描述文件`pom.xml`，存放Java源码的目录是`src/main/java`，存放资源文件的目录是`src/main/resources`，存放测试源码的目录是`src/test/java`，存放测试资源的目录是`src/test/resources`，最后，所有编译、打包生成的文件都放在`target`目录里。这些就是一个Maven项目的标准目录结构。



Sun 公司 1995年，James Gosling

Java SE：标准版，用于桌面应用的开发，是其他两个版本的基础；

​                学习目的：为今后要从事的 Java EE 开发打基础

Java ME：Java语言的小型版，用于嵌入式消费类电子设备

Java EE：企业版，用于 Web 方向的网站开发

2004 Java(5.0) - 里程碑

2009 Oracle 收购 Sun

2014 Java(8.0) - 应用最广

官网下载：www.oracle.com

【IDE-Eclipse】

[Eclipse](https://www.eclipse.org/) 是由 IBM 开发并捐赠给开源社区的一个 IDE，也是目前应用最广泛的 IDE

【IDE - IntelliJ Idea】

 (https://www.jetbrains.com/idea/)是由 JetBrains 公司开发的一个功能强大的 IDE，分为免费版和商用付费版。

Project > Module > Package > .java

包名：英文小写字母数字句点 命名

psvm：public static void main(){}

sout: System.out.println();

Ctrl+Alt+L：格式化

Ctrl+Shift+t : 看定义

Alt+Shift+⬆️⬇️：上移下移

Ctrl+/：加注释

自动保存，自动编译

Command+4 -- 打开之前的运行窗口包含结果

Command+1 -- 打开隐藏工程目录结构树 

Command+delete -- 删除当前行

class文件默认不显示在左边树中；

**settings** 设置 字体Font、快捷键 Keymap 

Ctrl+； Project structure 界面弹出

Ctrl+， Preferences 界面弹出

Command+N -- generate

Ctrl+Shift+x -- 大写

【Module】增、导、删除模块

删除时：第一次只是从项目中移除，第二次会删除硬盘文件夹

导入时有时会显示黄色条在界面顶部，setup sdk即可，跟sdk版本不一致有关；

【遍历数组】for，for each

```java
public class Main {
    public static void main(String[] args) {
        int[] ns = { 1, 4, 9, 16, 25 };
        for (int n : ns) { //变量n直接拿到ns数组的元素，而不是索引
            System.out.println(n);
        }
        //Java标准库的Arrays.toString()快速打印数组内容：
        System.out.println(Arrays.toString(ns));
    }
}
```

【抽象类】

定义非抽象方法的时候，必须有实现语句。

如果一个`class`定义了方法，但没有具体执行代码，这个方法就是抽象方法，抽象方法用`abstract`修饰。

因为无法执行抽象方法，因此这个类也必须申明为抽象类（abstract class）。

使用`abstract`修饰的类就是抽象类。我们无法实例化一个抽象类：

```
Person p = new Person(); // 编译错误
```

无法实例化的抽象类有什么用？

因为抽象类本身被设计成只能用于被继承，因此，抽象类可以强迫子类实现其定义的抽象方法，否则编译会报错。因此，抽象方法实际上相当于定义了“规范”。

尽量引用高层类型，避免引用实际子类型的方式，称之为【面向抽象编程】。

```java
Person s = new Student();
Person t = new Teacher();
// 不关心Person变量的具体子类型:
s.run();
t.run();
```

面向抽象编程的本质就是：

- 上层代码只定义规范（例如：`abstract class Person`）；
- 不需要子类就可以实现业务逻辑（正常编译）；
- 具体的业务逻辑由不同的子类实现，调用者并不关心。

【接口 interface】

所谓`interface`，就是比抽象类还要抽象的纯抽象接口，因为它连字段都不能有。因为接口定义的所有方法默认都是`public abstract`的，所以这两个修饰符不需要写出来（写不写效果都一样）。

```java
//类 Student 使用implements关键字 实现了两个接口
class Student implements Person, Hello { 
    ...
}

```



```ascii
┌───────────────┐
│   Iterable    │
└───────────────┘
        ▲                ┌───────────────────┐
        │                │      Object       │
┌───────────────┐        └───────────────────┘
│  Collection   │                  ▲
└───────────────┘                  │
        ▲     ▲          ┌───────────────────┐
        │     └──────────│AbstractCollection │
┌───────────────┐        └───────────────────┘
│     List      │                  ▲
└───────────────┘                  │
              ▲          ┌───────────────────┐
              └──────────│   AbstractList    │
                         └───────────────────┘
                                ▲     ▲
                                │     │
                                │     │
                     ┌────────────┐ ┌────────────┐
                     │ ArrayList  │ │ LinkedList │
                     └────────────┘ └────────────┘
```

在使用的时候，实例化的对象永远只能是某个具体的子类，但总是通过接口去引用它，因为接口比抽象类更抽象：

```java
List list = new ArrayList(); // 用List接口引用具体子类的实例
Collection coll = list; // 向上转型为Collection接口
Iterable it = coll; // 向上转型为Iterable接口
```

```java
interface Person {
    String getName();
    default void run() { //可以定义default方法；
        System.out.println(getName() + " run");
    }
}
```

实现类可以不必覆写`default`方法。`default`方法的目的是，当我们需要给接口新增一个方法时，会涉及到修改全部子类。如果新增的是`default`方法，那么子类就不必全部修改，只需要在需要覆写的地方去覆写新增方法。

`default`方法和抽象类的普通方法是不同：interface`没有字段，`default 方法无法访问字段，而抽象类的普通方法可以访问实例字段。

【静态字段】描述`class`本身的字段，推荐用类名来访问静态字段 

【静态方法】经常用于工具类。例如：

- Arrays.sort()
- Math.random()

静态方法也经常用于辅助方法。

【接口的静态字段】

`interface`可以有`final`类型的静态字段；

```java
public interface Person {
    public static final int MALE = 1;
    public static final int FEMALE = 2;
}
```

因为`interface`的字段只能是`public static final`类型，所以我们可以把这些修饰符都去掉，上述代码可以简写为：

```java
public interface Person {
    // 编译器会自动加上public statc final:
    int MALE = 1;
    int FEMALE = 2;
}
```

【包 package】用来解决名字冲突

一个类总是属于某个包，类名（比如`Person`）只是一个简写，真正的完整类名是`包名.类名`；

在Java虚拟机执行的时候，JVM只看完整类名，因此，只要包名不同，类就不同；

包可以是多层结构，用`.`隔开。例如：`java.util`；

包没有父子关系：java.util和java.util.zip是不同的包，两者没有任何继承关系；

没有定义包名的`class`使用的是默认包，易引起名字冲突，因此，不推荐；

所有Java文件对应的目录层次要和包的层次一致；编译后的`.class`文件也需要按照包结构存放；

编译的命令相对比较复杂，我们需要在`src`目录下执行`javac`命令：

假设包组织起来的java文件结构如下，并且用命令行编译：

```ascii
package_sample
└─ src
    ├─ hong
    │  └─ Person.java
    │  ming
    │  └─ Person.java
    └─ mr
       └─ jun
          └─ Arrays.java
```

```bash
javac -d ../bin ming/Person.java hong/Person.java mr/jun/Arrays.java
```

在IDE中，会自动根据包结构编译所有Java源码；

位于同一个包的类，可以访问包作用域的字段和方法，不用`public`、`protected`、`private`修饰的字段和方法就是包作用域。

Java编译器最终编译出的`.class`文件只使用*完整类名*；

【当编译器遇到一个`class`名称】时：

- 如果是完整类名，就直接根据完整类名查找这个`class`；
- 如果是简单类名，按下面的顺序依次查找：
  - 查找当前`package`是否存在这个`class`；
  - 查找`import`的包是否包含这个`class`；
  - 查找`java.lang`包是否包含这个`class`。

如果按照上面的规则还无法确定类名，则编译报错。

编写class的时候，编译器会自动 import`当前`package`的其他`class 和 java.lang.*。

【作用域 - 访问权限】public、private、protected、package

`private`访问权限被限定在`class`的内部，而且与方法声明顺序*无关*。推荐把`private`方法放到后面，因为`public`方法定义了类对外提供的功能，阅读代码的时候，应该先关注`public`方法：

一个`.java`文件只能包含一个`public`类，但可以包含多个非`public`类。如果有`public`类，文件名必须和`public`类的名字相同。

```
package abc;
// package 权限的类: 没有 public、private 修饰
class Hello {
    // package 权限的方法:没有 public、protected、private 修饰
    void hi() {
    }
}
```

使用局部变量时，应尽可能把局部变量的作用域缩小，尽可能延后声明局部变量。



【Inner Class】

```java
public class Main {
    public static void main(String[] args) {
        Outer outer = new Outer("Nested"); // 实例化一个Outer
        Outer.Inner inner = outer.new Inner(); // 实例化一个Inner
        inner.hello();
    }
}

class Outer {
    private String name;

    Outer(String name) {
        this.name = name;
    }

    class Inner {
        void hello() {
            System.out.println("Hello, " + Outer.this.name);
        }
    }
}
```

Inner Class的作用域在Outer Class内部，所以能访问Outer Class的`private`字段和方法。

Static Nested Class是独立类，但拥有Outer Class的`private`访问权限。

【classpath】

`classpath`是JVM用到的一个环境变量，它用来指示JVM如何搜索`class`；

`classpath`是一组目录的集合，它设置的搜索路径与操作系统相关；

`classpath`的设定方法有两种：

在系统环境变量中设置`classpath`环境变量，不推荐 -- 会污染整个系统环境；

在启动JVM时设置`classpath`变量，推荐。

```bash
java -classpath .;C:\work\project1\bin;C:\shared abc.xyz.Hello
java -cp .;C:\work\project1\bin;C:\shared abc.xyz.Hello
```

没有设置系统环境变量，也没有传入`-cp`参数，那么JVM默认的`classpath`为`.`，即当前目录；

在IDE中运行Java程序，IDE自动传入的`-cp`参数是当前工程的`bin`目录和引入的jar包。

【jar包】相当于目录，可以包含很多`.class`文件，方便下载和使用；

```
java -cp ./hello.jar abc.xyz.Hello

//如果存在Main-Class，就可以用更方便的命令：
java -jar hello.jar
```

【模块】

从Java 9开始引入的模块，主要是为了解决“依赖”的问题；

把一堆class封装为jar仅仅是一个打包的过程，而把一堆class封装为模块则不但需要打包，还需要写入依赖关系，并且还可以包含二进制代码（通常是JNI扩展）。此外，模块支持多版本，即在同一个模块中可以为不同的JVM提供不同的版本；

编写模块示例，假设工程目录结构如下：

```ascii
oop-module
├── bin
├── build.sh
└── src
    ├── com
    │   └── itranswarp
    │       └── sample
    │           ├── Greeting.java
    │           └── Main.java
    └── module-info.java
```

```bash
$ javac -d bin src/module-info.java src/com/itranswarp/sample/*.java
```

如果编译成功，新目录结构为：

```ascii
oop-module
├── bin
│   ├── com
│   │   └── itranswarp
│   │       └── sample
│   │           ├── Greeting.class
│   │           └── Main.class
│   └── module-info.class
└── src
    ├── com
    │   └── itranswarp
    │       └── sample
    │           ├── Greeting.java
    │           └── Main.java
    └── module-info.java
```

把bin目录下的所有class文件打包成jar，在打包的时候，传入`--main-class`参数，让这个jar包能自己定位`main`方法所在的类：

```
$ jar --create --file hello.jar --main-class com.itranswarp.sample.Main -C bin .
```

就在当前目录下得到了`hello.jar`这个jar包，可以直接使用命令`java -jar hello.jar`来运行它。

为了创建模块，继续使用JDK自带的`jmod`命令把一个jar包转换成模块：

```bash
$ jmod create --class-path hello.jar hello.jmod
```

这样当前目录下又得到了`hello.jmod`这个模块文件。

JRE自身的标准库已经分拆成了模块，只需要带上程序用到的模块，其他的模块就可以被裁剪掉。怎么裁剪JRE呢？并不是说把系统安装的JRE给删掉部分模块，而是“复制”一份JRE，但只带上用到的模块。为此，JDK提供了`jlink`命令来干这件事。命令如下：

```bash
$ jlink --module-path hello.jmod --add-modules java.base,java.xml,hello.world --output jre/
```

现在，在当前目录下，我们可以找到`jre`目录，这是一个完整的并且带有我们自己`hello.jmod`模块的JRE。试试直接运行这个JRE：

```bash
$ jre/bin/java --module hello.world
Hello, xml!
```

要分发我们自己的Java应用程序，只需要把这个`jre`目录打个包给对方发过去，对方直接运行上述命令即可，既不用下载安装JDK，也不用知道如何配置我们自己的模块，极大地方便了分发和部署。

class的这些访问权限只在一个模块内有效，模块和模块之间，例如，a模块要访问b模块的某个class，必要条件是b模块明确地导出了可以访问的包。

【反射 - Reflection】通过`Class`实例获取`class`信息的方法

JVM为每个加载的`class`创建了对应的`Class`实例，并在实例中保存了该`class`的所有信息，包括类名、包名、父类、实现的接口、所有方法、字段等，因此，如果获取了某个`Class`实例，我们就可以通过这个`Class`实例获取到该实例对应的`class`的所有信息。

Reflection 是动态语言的关键；

【获取一个`class`的`Class`实例？】有三个方法：

```java
Class cls = String.class; //通过一个class的静态变量class获取

String s = "Hello";
Class cls = s.getClass(); //通过实例变量提供的getClass()方法

Class cls = Class.forName("java.lang.String"); //通过静态方法，传入 class 的完整类名
```

//。。。未完待续 有点难的说

反射使用类的空参构造器来造对象；

【反射API】

java.lang.Class 代表一个类，用来描述类的类

java.lang.reflect.Method 类的方法

java.lang.reflect.Field 类的成员变量

java.lang.reflect.Constructor 类的构造器

- `Class.isAnnotationPresent(Class)`
- `Field.isAnnotationPresent(Class)`
- `Method.isAnnotationPresent(Class)`
- `Constructor.isAnnotationPresent(Class)`

- `Class.getAnnotation(Class)`
- `Field.getAnnotation(Class)`
- `Method.getAnnotation(Class)`
- `Constructor.getAnnotation(Class)`

【注解】//使用注解。。。未完成

一定程度上：框架 = 注解 + 反射 + 设计模式 

Java5.0 新增的功能，是代码里的特殊标记 

从JVM的角度看，注解本身对代码逻辑没有任何影响，如何使用注解完全由工具决定；

包括三类：

1 编译器使用的：`@Override`：让编译器检查该方法是否正确地实现了覆写，不会被编译进入`.class`文件，它们在编译后就被编译器扔掉；

2 工具处理 .class 使用的：会被编译进入`.class`文件，但加载结束后并不会存在于内存中；

3 程序运行期能读取的：在加载后一直存在于JVM中，这也是最常用的注解；例如：`@PostConstruct`的方法会在调用构造方法后自动被调用（这是Java代码读取该注解实现的功能，JVM并不会识别该注解）

注解可以配置参数，没有指定配置的参数使用默认值；

如果参数名称是`value`，且只有一个参数，那么可以省略参数名称；

【自定义注解】，参照 @SuppressWarnings

```java
public @interface MyAnnotation{
	String value() default “hello”;
}
```

Annotation 的成员变量在 定义中 以 无参数方法的形式来声明。其方法名和返回值定义了该成员的名字和类型。我们称为 配置参数。类型只能是八种基本数据类型、String、Class、enum、Annoatation、以上所有类型的数组。如果注解有成员，使用的时候需要指定值（没有默认值的情况下）。 

@Override 是一个无参的注解，也叫 标记；

自定义注解必须配上注解的 信息处理流程（使用反射） 才有意义；

【JDK 中的元注解】修饰现有其他注解的解释说明的注解

JDK5.0 提供了4个标准的 meta-annotation类型(自定义注解通常都会指明前面两个类型)：

Retention - 指明被修饰注解的生命周期，

```java
@Retention(RetentionPolicy.SOURCE)
@Target(TYPE, FIELD, METHOD, ...TYPE_PARAMETER,  TYPE_USE)
public enum RetentionPolicy{
SOURCE, // 编译完丢弃
CLASS,  // 进入 class 文件
RUNTIME // 能通过反射在运行时获取
}
```

Target - 指明 被修饰注解 可以修饰的程序元素

Documented - 所修饰的注解 在被 javadoc  解析时，保留下来

Inherited - 被修饰注解 将具有继承性

一个例子：通过反射可以 获取 注解信息；

元数据的理解：String name = “atguigu”；

【JDK8 - 可重复注解】//...未完待续 508

https://www.youtube.com/watch?v=hKzyUbQaorM&list=PLmOn9nNkQxJH0qBIrtV6otI0Ep4o2q67A&index=508

```java
@Repeatable
Public @Interface MyAnnotaion(){
   
}
```

【JDK8 - 类型注解】

JDK1.8之后，元注解 @Target 的参数类型 ElementType 枚举值多了两个：

TYPE_PARAMETER - 表示该注解能写在类型变量的声明语句中（如：范型声明）

TYPE_USE - 该注解能写在 使用类型的 任何语句中



【如何读取`RUNTIME`类型的注解】

注解定义后是一种`class`，都继承自`java.lang.annotation.Annotation`，因此读取注解，需要使用反射API；

```java
// 判断@Report是否存在于Person类:
Person.class.isAnnotationPresent(Report.class);
```

```java
// 获取Person定义的@Report注解:
Report report = Person.class.getAnnotation(Report.class);
int type = report.type();
String level = report.level();
```

【Java集合】在内部持有若干其他Java对象，并对外提供访问接口的 Java 对象 

分为 Collection 和 Map 两种体系；

集合类定义在`java.util`包中，支持泛型，主要提供了3种集合类，包括`List`，`Set`和`Map`；Java集合使用统一的`Iterator`遍历；

```
|----Collection 单列集合
      |----List 有序可重复数据，--> “动态”数组
             |----ArrayList
             |----LinkedList
             |----Vector
      |----Set 无需不可重复数据  -->数学集合的概念
|----Map 双列集合，用来存储（key - value）数据 --> 数学里函数
      |----HashMap
      |----properties
```

面试题：ArrayList 怎么扩容，HashMap 底层实现

集合、数组都是对多个数据进行存储操作的结构，此时的存储，指的是内存层面的存储；

```
Array 数组 存储数据的特点：

1 初始化后长度确定；

2 一旦定义好，元素类型也就确定。

所以有一些弊端：初始化后其长度不能修改；提供的方法非常有限，对于添加、删除、插入数据非常不便，效率也不高；
```

集合框架涉及到的 API

Collection 中的方法：add、addAll、clear、size、toArray



【List】

`List`接口的两种实现：ArrayList 和 LinkedList，优先使用 ArrayList；

`List`接口允许我们添加重复的元素，允许添加`null`；

通过`List`接口提供的`of()`方法，根据给定元素快速创建`List`：

```java
List<Integer> list = List.of(1, 2, 5); //List.of()方法不接受null值
```

遍历 List 不推荐使用 for + get(i) 的方式，因为`get(int)`方法只有`ArrayList`的实现是高效的；

应坚持使用迭代器`Iterator`来访问`List`，因为不同的`List`类型，返回的`Iterator`对象实现也不同的，但总是具有最高的访问效率；

```java
import java.util.Iterator;
import java.util.List;

public class Main {
    public static void main(String[] args) {
      
      List<String> list = List.of("apple", "pear", "banana");
      //Iterator本身也是一个对象, list.iterator()执行时创建 
      for (Iterator<String> it = list.iterator(); it.hasNext(); ) {
            String s = it.next(); //.hasNext 和 .next 两个方法
            System.out.println(s);
        }
    }
}
```

Java的`for each`循环本身就可以帮我们使用`Iterator`遍历，上面的代码再改写如下：

```java
public class Main {
    public static void main(String[] args) {
        List<String> list = List.of("apple", "pear", "banana");
        for (String s : list) {
            System.out.println(s);
        }
    }
}
```

👆代码就是我们编写遍历`List`的常见代码！

实现了`Iterable`接口的集合类都可以直接用`for each`循环来遍历，Java编译器本身并不知道如何遍历集合对象，但它会自动把`for each`循环变成`Iterator`的调用，原因就在于`Iterable`接口定义了一个`Iterator<E> iterator()`方法，强迫集合类必须返回一个`Iterator`实例。

【List --> Array 】

```java
 List<Integer> list = List.of(12, 34, 56);
 //1. 此处的 Number 可以换成 Integer
 Number[] array = list.toArray(new Number[list.size()]);
 for (Number n : array) { 
            System.out.println(n);
        }
 //2.      
 Integer[] array = list.toArray(new Integer[list.size()]);
```

【List <-- Array】

```java
Integer[] array = { 1, 2, 3 };
List<Integer> list = List.of(array); //返回的是一个只读 List
```

思维方式：

1. 大处着眼，小处着手

2. 逆向思维、反证法

3. 透过问题看本质

小不忍则乱大谋

识时务者为俊杰

【Java8】661-663/715

语言层面/面向对象/接口 - 默认方法、静态方法

日期时间 API - datatimeFormatter

注解 - 类型注解、重复注解

对集合的修改 - 造数据、hashMap 底层红黑树、B树 B+树

Lambda 表达式 - 代码更少

函数式接口 Functional - 只有一个抽象方法的接口

方法引用与构造器引用

Stream API - 功能强大

Optional 类 - 最大化减少 空指针异常

Nashorn 引擎，替换掉 Rhino，允许在 JVM 上运行 JS 应用 jjs

【Java8 - Lambda 表达式】

本质：作为函数式接口的实例；

```java
Runnable run2 = () -> System.out.println("ggggg");
```

以前用匿名实现类表示的现在都可以用 Lambda 来写；

【函数式接口 Functional Interface】666-667 只有一个抽象方法的接口

可以使用 @FunctionalInterface 注解，来帮助检查；

javadoc 也会包含一条声明，说明该接口是一个函数式接口；

java.util.funciton 包下面定义了 Java8 的丰富的函数式接口； 

【Java8 - Stream】

（资源）尚硅谷 Java8新特性 创建 Stream - Java8新特性 - 李贺飞

https://www.youtube.com/watch?v=Ij1lJyZRBnE&list=PLLPovsDEpByb8w-0zVVp-ZSxOgLkgfg5H&index=7

集合 -- 数据，流 -- 计算

Stream 不会存储元素，不会改变源对象，延迟执行

实现`String`到`Person`的转换，我们可以引用`Person`的构造方法：

```java
public class Main {
    public static void main(String[] args) {
      List<String> names = List.of("Bob", "Alice", "Tim");
      List<Person> persons = names.stream().map(Person::new).collect(Collectors.toList());
      //构造方法的引用写法是类名::new  
      System.out.println(persons);
    }
}

class Person {
    String name;
    public Person(String name) {
        this.name = name;
    }
    public String toString() {
        return "Person:" + this.name;
    }
}
```

Stream API的基本用法就是：创建一个`Stream`，然后做若干次转换，最后调用一个求值方法获取真正计算的结果，例如：

```java
int result = createNaturalStream() // 创建Stream
             .filter(n -> n % 2 == 0) // 任意个转换
             .map(n -> n * n) // 任意个转换
             .limit(100) // 任意个转换
             .sum(); // 最终计算结果
```

- Stream API提供了一套新的流式处理的抽象序列；
- Stream API支持函数式编程和链式操作；
- Stream可以表示无限序列，并且大多数情况下是惰性求值的。

创建`Stream`的方法有 ：

- 通过指定元素、指定数组、指定`Collection`创建`Stream`；
- 通过`Supplier`创建`Stream`，可以是无限序列；
- 通过其他类的相关方法创建。

基本类型的`Stream`有`IntStream`、`LongStream`和`DoubleStream`。

```java
//1. 传入可变参数，用Stream.of()静态方法 创建
Stream<String> stream = Stream.of("A", "B", "C", "D");
//2. 把数组变成Stream使用Arrays.stream()方法
Stream<String> stream1 = Arrays.stream(new String[] { "A", "MC" });
//3. 对于Collection（List、Set、Queue等），直接调用stream()方法
Stream<String> stream2 = List.of("X", "Y", "Z").stream();
//4. 通过Stream.generate()方法，传入一个Supplier对象
public class Main {
    public static void main(String[] args) {
        Stream<Integer> natual = Stream.generate(new NatualSupplier());
        // 注意：无限序列必须先变成有限序列再打印:
        natual.limit(20).forEach(System.out::println);
    }
}
class NatualSupplier implements Supplier<Integer> {
    int n = 0;
    public Integer get() {
        n++;
        return n;
    }
}
//5. 通过一些API提供的接口，直接获得Stream
//5-1. Files类的lines()方法把文件变成Stream，每个元素代表文件的一行内容
try (Stream<String> lines = Files.lines(Paths.get("/path/to/file.txt"))) {
    ...
}
//5-2. 正则表达式的Pattern对象的splitAsStream()方法，把字符串分割成Stream序列
Pattern p = Pattern.compile("\\s+");
Stream<String> s = p.splitAsStream("The quick brown fox jumps over the lazy dog");
s.forEach(System.out::println);
```

Java的范型不支持基本类型，所以无法用`Stream<int>`这样的类型，会发生编译错误。为了保存`int`，只能使用`Stream<Integer>`，但这样会产生频繁的装箱、拆箱操作。为了提高效率，Java标准库提供了`IntStream`、`LongStream`和`DoubleStream`这三种使用基本类型的`Stream`，它们的使用方法和范型`Stream`没有大的区别，设计这三个`Stream`的目的是提高运行效率：

```java
// 将int[]数组变为IntStream:
IntStream is = Arrays.stream(new int[] { 1, 2, 3 });
// 将Stream<String>转换为LongStream:
LongStream ls = List.of("1", "2", "3").stream().mapToLong(Long::parseLong);
```

`map()`方法用于将一个`Stream`的每个元素映射成另一个元素并转换成一个新的`Stream`；

可以将一种元素类型转换成另一种元素类型；

使用`filter()`方法可以对一个`Stream`的每个元素进行测试，通过测试的元素被过滤后生成一个新的`Stream`；

`reduce()`方法：

```java
public class Main {
    public static void main(String[] args) {
      //1-1. 首先初始化结果为指定值（这里是0），
      //1-2. reduce()对每个元素依次调用(acc, n) -> acc + n，其中，`acc`是上次计算的结果  
      int sum = Stream.of(1, 2, 3, 4, 5, 6, 7, 8, 9).reduce(0, (acc, n) -> acc + n);
        System.out.println(sum); // 45
    }
}
//上面代码与下面的等价
Stream<Integer> stream = ...
int sum = 0;
for (n : stream) {
    sum = (sum, n) -> sum + n;
}
```

转换操作只是保存了转换规则，无论我们对一个`Stream`转换多少次，都不会有任何实际计算发生；

聚合操作则不一样，聚合操作会立刻促使`Stream`输出它的每一个元素，并依次纳入计算，以获得最终结果；所以，对一个`Stream`进行聚合操作，会触发一系列连锁反应；

对一个`Stream`做聚合计算后，结果就不是一个`Stream`，而是一个其他的Java对象。

如何将一组`String`先过滤掉空字符串，然后把非空字符串保存到`List`中：

```
public class Main {
    public static void main(String[] args) {
        Stream<String> stream = Stream.of("Apple", "", null, "Pear", "  ", "Orange");
        List<String> list = stream.filter(s -> s != null && !s.isBlank()).collect(Collectors.toList());
        System.out.println(list);
    }
}

```

把`Stream`的每个元素收集到`List`的方法是调用`collect()`并传入`Collectors.toList()`对象，它实际上是一个`Collector`实例，通过类似`reduce()`的操作，把每个元素添加到一个收集器中（实际上是`ArrayList`）。

类似的，`collect(Collectors.toSet())`可以把`Stream`的每个元素收集到`Set`中。

`Stream`可以输出为集合：

`Stream`通过`collect()`方法可以方便地输出为`List`、`Set`、`Map`，还可以分组输出。

//。。。分组输出 未完待续

`Stream`提供的常用操作有：

转换操作：`map()`，`filter()`，`sorted()`，`distinct()`；

合并操作：`concat()`，`flatMap()`；

并行处理：`parallel()`；

聚合操作：`reduce()`，`collect()`，`count()`，`max()`，`min()`，`sum()`，`average()`；

其他操作：`allMatch()`, `anyMatch()`, `forEach()`。

【补：Supplier】

【JavaBean】是一种 Java 语言写成的可重用组件

是指符合以下标准的 Java 类：

公共、有一个无参的公共的构造器、有属性且有对应的get和set方法；

属性是一种通用的叫法，并非Java语法规定；

主要用来传递数据，即把一组数据组合成一个JavaBean便于传输；

可以利用IDE快速生成`getter`和`setter`；

使用`Introspector.getBeanInfo()`可以获取属性列表。

```java
import java.beans.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BeanInfo info = Introspector.getBeanInfo(Person.class);
        for (PropertyDescriptor pd : info.getPropertyDescriptors()) {
            System.out.println(pd.getName());
            System.out.println("  " + pd.getReadMethod());
            System.out.println("  " + pd.getWriteMethod());
        }
    }
}

class Person {
    private String name;
    private int age;

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
}
```

//。。。需要理解 用户可以使用 JavaBean 将功能、处理、值、数据库访问和其他任何可以用 Java 代码创造的对象进行打包，并且其他的开发者可以通过内部的 JSP 页面、Servlet、其他 JavaBean、applet 程序或者应用来使用这些对象。用户可以认为 JavaBean 提供了一种随时随地的复制和粘贴的功能，而不用关心任何改变。

【String/StringBuffer/StringBuilder】

464 尚硅谷 常用类 StringBuffer的源码分析

| String         | StringBuffer   | StringBuilder       |
| -------------- | -------------- | ------------------- |
| 底层使用char[] | 底层使用char[] | 底层使用char[]      |
| 不可变         | 可变           | 可变                |
|                | 线程安全       | 5.0新增，线程不安全 |
|                | 效率低         | 效率高              |



【Java9、10、11】

#### 



【Terminal-bash 坏了】

改用 csh，设置：Terminal / Preferences / General - Shells open with: /bin/csh

【MapStruct】

在 build.gradle 里面

```bash
dependencies {
	implementation 'org.mapstruct:mapstruct:1.5.2.Final'
	annotationProcessor 'org.mapstruct:mapstruct-processor:1.5.2.Final'
}
```

【安装 mysql】

root / password 

安装路径 /usr/local/mysql/bin

```bash
$cd /usr/local/mysql/bin 
$./mysql --version
 =>./mysql  Ver 8.0.29 for macos12 on x86_64 (MySQL Community Server - GPL)
```

但是在其他路径下没法直接看版本信息，需要 修改 .bash_profile，增加：

```bash
export PATH=$PATH:/usr/local/mysql/bin

$mysql -u root -p // to access the MySQL monitor

mysql>create database flyway_migrations; // Database Setup
```

解决问题

```bash
mysql>UPDATE mysql.user SET authentication_string = PASSWORD('Mysql22!') WHERE User = 'root' AND Host = 'localhost';
```

【Flyway+Mysql/PostgreSQL】

**Database Migration** - 实现对数据库更改的版本控制

Flyway vs. Liquibase(使用xml)

https://flywaydb.org/documentation/gradle

https://www.liquibase.org/

参考：wholesale / src / main / resources / db / migration *.sql

**Spring Boot** 提供了对 **Flyway** 的自动配置，只需: 引入依赖 + Set up数据库 +  编写 sql 脚本

1. 引入依赖：在 build.gradle 里面设置

```bash
dependencies {
	implementation 'org.flywaydb:flyway-core:6.5.7'
	}
```

2. Set up数据库：mysql

```bash
mysql>create database flyway_test;

```

或者：PostgreSQL + Docker

```bash
// 0. 启动 Docker App
// 1. 终端用 docker 启动 postgres container，设置端口号，密码 => $docker ps 可查看启动的 postgres
$ docker run  --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5431:5432 postgres
// 2. 打开 pgAdmin App，Register 连接 postgres 数据库服务器 => Tables 为空，postgres / SQL 可看到数据库名为 postgres 
// 3. Intellij 运行 spring boot app => Successfully applied 4 migrations to schema "public" 
$ ./gradlew bootRun
// 4. 数据迁移成功 => pgAdmin / Refresh 可以看到数据已经在了
```

3. SQL脚本 mysql 范例：

```mysql
CREATE TABLE student
(
    student_id          bigint(20) not null AUTO_INCREMENT,
    first_name          varchar(50) not null,
    last_name           varchar(50) not null,
    email               varchar(50) not null,
    course              varchar(50) not null,
    registration_number varchar(50)  not null,
    primary key (student_id),
    unique key UK_email(email)
)
```

SQL脚本 PostgreSQL 范例：

```postgresql
create table users (
    id serial primary key,
    user_id varchar(30),
    encoded_password varchar(100)
);
```

一旦 Spring Boot 在本地起来以后，这些 sql 文件会自动和数据库进行关联，并依次执行，执行完某个 sql 后，会在数据库表中添加一条记录；等再一次 启动 Spring Boot 时，不会再执行，因为表中已经有了记录；新增改动都要新添加一个 sql 文件；

打开 pgAdmin 可以看到，数据库中 flyway 自动创建的表： flyway_schema_history



SQL 注入的解决办法：复杂查询 / 多参数 使用 : 以及 @Param，Spring Data JPA 会屏蔽掉不合法的输入

```
flyway.url=jdbc:h2:file:./foobardb
flyway.user=Lisa
flyway.password=
```

![SQL Cheet Sheet 1](https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-Cheet-Sheet-1.png)

![SQL Cheat Sheet 2](https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-Cheat-Sheet-2.png)

![SQL Cheat Sheet 3](https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-Cheat-Sheet-3.png)
