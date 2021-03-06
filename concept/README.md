## 概念集合
- 进入计算机领域之后，有过几次尝试，想把涉及到的概念都梳理一遍，之前摊子铺的有些大，都是过了一段时间就放下了，这次尽量能持续地长一些。日常工作、学习过程中，遇到的概念，及时进行整理、总结、归纳，肯定能理解的更透彻点，然后，再慢慢梳理概念之间的联系。


### 计算相关概念整理
- 位
  - 位是信息论、计算机和数字通信中的基本单位，是 binary digit的组合。呈现形式有0/1、true/false、on/off、yes/no等等。
- 字节
  - 8位组成一个字节，8位组成一个字节的原因还没搞清楚。
- 字符
  - 汉字和英文字母都可算作是字符
- 字符集
  - 字符的集合
- Session
  - 会话是一种临时和交互的信息交互，在两个或多个通信设备，或者计算机与用户之间。
- HTTP cookie
  - 一小段从网站发送的数据，当用户浏览的时候，通过用户的浏览器存储在用户的计算机上
- API
  - 指的就是程序与程序之间的接口（主要目的是为了方便交流吧，A程序可以通过B程序API来调用B程序的数据，计算机真的有好多解决问题的思想，可以应用在自己的生活、学习、工作当中。）
- webhook
  - 是一种通过自定义回调来扩充或改变web页面或应用的方法，与API的区别是webhook只有post请求
- Git
  - 时间穿梭机，这个就得多用、多练，熟能生巧、勤能补拙。
- SQL
  - 结构化查询语言。
- Computational Thinking
  - 用计算机思维去解决问题，把大问题拆解为小问题的步骤，在实作中寻找资源。这种思维模式，在做事的过程完全可以应用，是很好的一个解决问题的方式，之前怎么就不用呢。
- 脚本可复用：在实际项目中，会写迁移脚本，要写成即使发生错误，也能再次运行的脚本，不能写那种仅能运行一次的脚本，如果再运行的话，会出现错误的数据，那就不合格了
- 并发
  - 处理多任务的能力，比如你在看书，突然来了一个电话，不看书了去接电话，接完之后继续看书，说明你只支持并发
- 并行
  - 同时处理多任务的能力，比如你在看书，突然来了一个电话，边看书边听电话，说明你支持并行
> 理解并发和并行的关键点在于是否 `同时`


- class
  - 类，拥有同一种类别的集合
- module
  - 不可被实例化，不可被继承
- 对象
  - 对象是Ruby代码的基本构建块（一切都是对象），有两个主要的属性：状态和行为。
- 抽象
  - 把问题抽象成现实世界中的概念，更关注于人，而不是机器。更关注与问题本身，而不用担心像二进制代码或者代码要运行在一个特定操作系统的问题。让我们把注意力放在对象的状态和行为的两个属性上面。
- 封装
  - 将关注点控制在一定范围内，保证程序的安全，也让工程师的注意力更聚焦。Ruby中，封装有许多方式，分类方法包括public、private和protected。
- 多态
- 继承

- 运算符
- 脚本语言
- 函数式编程（functional programming）
- 汇编语言
- 现代计算机语言

- Rails
  - Rails是一个服务端的web应用框架，用Ruby编写，2005年12月13日发布稳定版本。

#### 编译原理
- 编译
  - 全部一次性去执行，类似于吃满汉全席
- 编译器与解释器之间的区别
  - 解释器转化高级语言指令为中间代码，然后执行结果代码。编译器转化高级编程语言代码为目标代码。解释器一行一行执行代码，然而，编译器执行结果文件
  - 解释器和编译器在编程语言执行程序中，起着非常重要的作用。许多人倾向于认为他们之间是相似的。然而，他们在很多地方不同。
  - 我们通过计算机语言与计算机交流。计算机只懂得0和1的二进制语言。然而，大多数程序是用高级语言写的，因此需要转化为二进制格式。解释器和编译器都是将程序语言转化为计算机可懂的机器语言的程序。你可以认为他们有相同的目的，然而，他们之间有很大的不同
  - `它两之间最大的不同时编译器直接将源码转化为机器语言，而解释器生成中间代码，然后，执行中间代码以便生成机器可懂的代码`。解释器和编译器有将源码转化为机器码相同的任务，但是他们转化的方式非常不同。编译器具备诊断的能力，然而，当时编译高级程序的时候，他们能提示恰当的错误信息。至于解释器，目标代码不能存储，因此不能被复用。
  - 编译器在为相同的对象创建可执行文件之前生成目标代码。编译程序使用目标直接被执行。另一方面，解释器通过每次读取一行来执行源代码。在执行期间，原生代买一行一行被执行。编译器和解释器都是用高级编程语言写的。例如，一个java解释器可以用Java、Pascal等来写。他们都有各自的缺点和优点。两种方法可以混合使用获得混合的方法。例如，LISP语言，在LISP解释环境开发完成。结果模块被很好测试，被LISP编译器编译。下面中列出了不同：
  - 原文地址：http://www.differencebetween.info/difference-between-interpreter-and-compiler
- 词法分析
- 语法分析
- 语义分析
  - 针对上下文的情况做处理
- 引用的消解
  - 函数的
  - 变量的
- 左值
- 右值
- 属性计算
- Antrl
  - 一个开源工具，支持根据规则文件生成词法分析器和语法分析器
- 二义性文法
- 作用域（Scope）
  - 块作用域（Block）
  - 函数作用域（Function）
  - 类作用域（Class）
  - 静态作用域（Static）
  - 动态作用域（Dynamic）
- 生存期
- 函数
- 高阶函数（High-order function）
- 闭包（Closure）
- 语法树
- 缺省（默认）
- 类型
  - 高级语言才有
  - 类型是针对一个组数值，以及在这数值之上的一组操作。
  - 类型是高级语言赋予的一种语义，有了类型这种机制，相当于定了规矩，可以检查加在数据上的操作是否合法
  - 类型最大的好处是降低计算出错的概率
- 类型系统
  - 类型系统是一门语言所有的类型的集合，操作这些类型的规则，以及类型之间怎么相互作用的（比如一个类型能否转换成另一个类型）。
- 静态类型语言和动态类型语言
  - 根据类型检查是在编译期还是在运行期进行，把计算机分为两类
    - 静态类型语言（全部或者几乎全部的类型检查是在编译期进行）
    - 动态类型语言（类型的检查是在运行期进行）
  - 说的是什么时候检查的问题
- 强类型和弱类型（分别都有哪些语言呢？）
  - 强类型语言中，变量的类型一旦声明就不能改变
  - 弱类型语言中，变量类型在运行期时可以改变
  - 区别是，强类型不允许违法操作，而弱类型从机制上无法禁止违法操作，所以是不安全的
  - 说的是就算检查，也检查不出来，或者没法检查的问题
- 类型检查（Type Inference）
- 类型推导（Type Checking）
- 类型转换（Type Conversion）
- 类型论（Type Theory）


#### 网络系统
- TCP
  - 传输控制协议
  - 
- IP
  - 就是你们家的门牌号
- DHCP
  - Dydamic Host Configuration Protocl 动态主机配置协议
- DNS
  - The Domain Name System is a hierarchical and decentralized naming system for computers, services, or other resources connected to the internet or a private network. It associates various information with domain names assigned to each of the participating entities. 域名服务器
- CDN
  - A content delivery network or conent distribution network is a geographically distributed network of proxy servers and their data centers. The goal is to provide high availability and high performance by distributing the service spatially relative to end-users.内容分发网络
- 防盗链
- 负载均衡
  - 举了个例子，比如我想去吃海底捞，但是有很多家，我会选择就近的一家，而不是大家都去同一家，这就是负载均衡。这个定义先凑合着用吧
- 全局负载均衡器：（GSLB Global Server Load Balance）
- 内部负载均衡器：（SLB Server Load Balance）
- 本地DNS解析器：
- 边缘节点：
- 区域节点：
- 中心节点：
- CNAME
- 流媒体协议：
- RTMP协议
- http
- https
- udp
- 线程
- 进程
#### 计算机组成原理
- CPU
  - Central Processing Unit 中央处理器
- 算术逻辑单元（ALU）
- 逻辑门
- CPU时钟
- GPU
  - Graphics Processing Unit 图形处理器
- 触发器
- 高速缓存
- 功耗墙
- 功耗
- 内存
  - 计算机中，内存指一种设备，用来存储信息，用于在计算机或相关计算机硬件设备中立即使用
- 硬盘
  - hard disk drive 硬盘是一个机电数据存储设备 使用磁存储器去存储和检索数字数据，使用一个或多个涂有磁性材料的刚性快速旋转盘片
- 主板
  - Motherboard，是在通用计算机和其他可扩展系统中够贱的主要印刷电路板（printed circuit board）
- 冯诺依曼体系结构（存储程序计算机）
  - 可编程计算机
  - 可存储计算机
  - [First Draft of a Report on the EDVAC](https://en.wikipedia.org/wiki/First_Draft_of_a_Report_on_the_EDVAC)
- 控制器
- 运算器
- 存储器
- 输入设备
- 输出设备
- 显卡
  - Graphics Card
#### 数据结构与算法
-- 算法
-  - 操作数据的一组方法
-  - 一系列有效和通用的解决问题的步骤
-  - 一个有限的指令集
-- 复杂度分析（最重要的概念）
-  - 时间复杂度
-    - 渐进时间复杂度，表示算法的执行时间与数据规模之间的增长关系
-  - 空间复杂度
-    - 渐进空间复杂度，表示算法的存储空间与数据规模之间的增长关系
-- 大O复杂度分析
-- 最好情况复杂度
-- 最坏情况复杂度
-- 平均情况时间复杂度
-- 均摊时间复杂度
-- 摊还分析法
-- 递归
-  - 一种循环，函数本体的循环。自己调自己，从来不停止的
-    - 例子：从前有座山，山里有个庙，庙里有个和尚讲故事
-- 递归下降算法（Recursive Descent Parsing）
-- 排序算法
-- 二分查找
-- 哈希算法
-- 搜索算法
-- 字符串匹配算法
-- 贪心算法
-- 分治算法
-- 位运算
-- 回溯算法
-- 动态规划
-- 数据结构
-  - 广义：一组数据的存储结构；
-  - 狭义：指某些著名的数据结构和算法，比如队列、栈、堆、二分查找、动态规划等
-  - 数据结构是信息和数据的抽象表达
-  - 数据结构是为算法服务的，算法要作用在特定数据结构之上
-- 数组 Array
-  - 一种连续表的数据结构。存储连续性额数据，并且是相同类型的数据。
-  - 之所以设计数组这样的数据结构是为了随机访问？
-- 链表 Linked List
-- 栈（Stack）
-- 队列 Queues
-- 堆
-- 树 Trees
-- 图 Graphs
-- 布隆过滤器
-- LRU Cache
-- 散列表
-- 二叉树
-- 并查集
-- 跳表
-- Trie(字典)树
-- 栈桢（Stack Frame

#### 软件工程
- 软件工程
  - 将系统化的、规范的、可度量的方法用于软件的开发、运行和维护的过程，即将工程化应用于软件开发中。


#### Programming
#### Computer Architecture
#### Algorithms and Data Structures
#### Mathmetic For Computer Science
#### Operating Systems
#### Database
#### Computer Networking
#### Languages and Compilers
#### Distributed Systems