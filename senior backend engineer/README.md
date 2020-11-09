# 高级后端工程师指南

- 我就想把所有可能出现的问题，可能不会的问题，可能会被问到的问题全部写出来，这样才能够让自己的内心踏实，那就需要写出来，需要开源出去，这个就

- 作为一个高级后端工程师，在计算机领域，各个方面知识都需要掌握到什么程度，可以通过文字加代码的方式记录下来，这样能够给自己信心和力量，希望别人看到的时候，能够带来一些启发和帮助。

- 计算机领域的两个开山鼻祖是冯诺依曼和图灵，分别写了《》《》两篇论文，1945年1月30日冯诺依曼发表的论文的《First Draft of a Report on EDVAC》为冯诺依曼体系结构奠定了理论基础，现在的计算机组成是以这篇论文为基础发展而来的；1936年5月28日图灵的《On Computable Numbers, With An Application To The Entscheidungsproblem》论文发表，《在可计算数字，通过一个应用的判定问题》，这篇论文发表之后，对于计算机的可判定问题有了理论基础，该问题是1928年由David Hilbert和Wilhelm Ackermann提出。
- 现在的想法是既然这两篇论文是计算机领域的基础，那么就有必要去精读，需要把这两篇论文自己花时间翻译一遍，定期翻译一点，总要翻译完的那一天



### 算法与数据结构
#### 重要的概念
- 复杂度分析
- 时间复杂度
- 空间复杂度


- 常见的数据结构与算法
- 数据结构
  - 数组
  - 链表
  - 栈
  - 队列
  - 散列表
  - 二叉树
  - 堆
  - 跳表
  - 图
  - Trie树
- 算法
  - 递归
  - 排序
  - 二分查找
  - 搜索
  - 哈希算法
  - 贪心算法
  - 分治算法
  - 回溯算法
  - 动态规划
  - 字符串匹配算法

### 网络协议
- 网络的分层
  - Application Layer 应用层
  - Presentation Layer 展示层
  - Session Layer 会话层
  - Transimit Layer 传输层
  - Network Layer 网络层
  - Data Link Layer数据连接层
  - Physical Layer 物理层

### 操作系统
- 操作系统分为几个部分
  - 系统初始化
  - 内存管理
  - 进程管理
  - 进程间通信
  - 文件系统
  - 网络系统
  - 虚拟化
  - 容器化

### 设计原则
#### 重要的概念
- 

- 知道设计模式的重要性，常见的有23种设计模式，但设计模式并不只是有这23种，还有其他的，是什么决定了设计模式？在实际的软件设计中，不可能去死记硬背这23种设计模式，需要去灵活运用，运用的时候遵循的设计原则要比知道有哪些设计模式更重要，就跟做事遵循一定的原则一样，设计软件的时候，遵循一定的原则也非常重要
- 有哪些设计原则
  - 开闭原则
  - SOLID原则
  - 单一职责原则
  - 


### 数据库
#### 重要的概念
- 关系型数据库
- 非关系型数据库
- 主从复用
- 读操作
- 写操作
- 数据库模型
- 现在对数据库的认知中，熟悉下面的五种数据库，分别是关系型数据、非关系型数据、缓存数据库

#### MongoDB
##### MongoDB如何更新内内嵌对象的值？

- 遇到一个更新MongoDB更新内嵌对象的问题，Model如下：

```ruby
class Product
  include Mongoid::Document
  include Mongoid::Timestamps

  embeds_one :item
end

class Item
  include Mongoid::Document
  include Mongoid::Timestamps

  field :title, type: String
end
```

- 对于embeds_one的关系，按照mongoid官方文档，可以使用下面方法进行修改
```ruby
product.item.assign_attributes(title: "商品条目名称")
```

- 但上面的方法并没有成功，查找原因可能是在Item中，未加`embeds_in :product`

- 继续找解决方案，找到一个折中的方案，即先把内前对象item的值，通过`product.remove_attribute(:item)`删除，再重新赋值，可以解决遇到的问题，而不是直接更新

```ruby
product.remove_attribute(:item)
product.update!(itme: new_item)
```
实际操作，今天在正式环境更新了两个link，需要使用 update! 更新内嵌的资源 

- 2020.05.07 在线上环境，修复有问题数据的时候，使用上面的方法，尝试了五六次，得到product.item一直是nil，但过了一会就好了，不知道原因，记录一下。
- 参考资料
  - [update embedded document in mongoid](https://stackoverflow.com/questions/42331389/update-embedded-document-in-mongoid)
  - [mongoid官方文档](https://docs.mongodb.com/mongoid/current/tutorials/mongoid-documents/)


##### MongoDB如何进行数组元素大于某个值的查询

- 遇到一个MongoDB数组查询问题，商品标签字段为数组，需要查找出标签元素大于2个的所有商品，一般情况下，会先使用[Ruby Array select method](https://apidock.com/ruby/Array/select)，如下：

  ```ruby
  Product.all.select { |p| p.tags_name.count > 2 }
  ```
  > 上面方法，在数据量少的时候，不存在性能问题，商品数据很多（需要举出具体例子，达到哪个数量级之后，会有性能问题），会导致查询很慢，需要优化

- 找到一个次优方法，把标签为空的商品先去掉，再通过select方法查询：

  ```ruby
  Product.all.where(:tags_name.ne => []).select { |p| p.tags_name.count > 2 }
  ```
  > 上面方法可以减少部分查询，但[mongoid query](https://mongoid.github.io/old/en/mongoid/docs/querying.html#queries)中并不支持数组的筛选，本质还是select方法查询，性能并未改善，需要继续优化

- 继续寻找更优方法，[MongoDB collection find method](https://docs.mongodb.com/manual/reference/method/db.collection.find/)，找到对于数组的查询方法，再添加一个筛选条件，某两个渠道的商品
  ```ruby
  Product.collection.find(
    {
    "channel_id": { "$exists": true, "$in": ["A", "B"], # 筛选渠道为A、B的所有值
    "tags_name.2": { "exists : true} } # 筛选元素大于2的所有值
    }
  )
  ```
  > 注意上面结果，class 是`Mongo::Collection::View`

##### mongoDB在设定datatime默认值的时候，需要注意格式
- 设置默认值，有两种格式，如下：
```ruby
field :expired_at, type: DateTime, default: Time.zone.now # 第一种
field :expired_at, type: DateTime, default: -> { Time.zone.now } # 第二种
```
- 最近在这方面遇到了问题，开始的时候设置为第一种格式，导致默认时间出现了错误，查文档之后，改为放在proc中，才显示正确
- 第一种设定的默认时间为类的加载时间
- 第二种为文档状态的时间，即文档修改的时间
#### Redis

#### Memcache

#### MySQL

#### Postgresql

### 编程语言

#### Ruby
##### 重要的概念

#### Go
##### 重要的概念
- 

#### JavaScript
##### 重要的概念

#### HTML

#### 重要的概念
- elements 元素
- HTML
- head
- body

#### CSS
###### 重要的概念
- css 层叠样式表


### 软件工程

- 在实际开发中，学到的非常重要的一点，就是在开发之前做任务分解，分解的颗粒度要细，以一个完整的小功能为颗粒度，完成之后可以提交一个commit，这样不至于任务量很大，有其他紧急事情插入的时候，着手去忙其他的事情，到时再回来忘记自己开发的进度在哪里的情况。