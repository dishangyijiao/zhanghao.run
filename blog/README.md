## MongoDB
### MongoDB如何更新内内嵌对象的值？

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


### MongoDB如何进行数组元素大于某个值的查询

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

### mongoDB在设定datatime默认值的时候，需要注意格式
- 设置默认值，有两种格式，如下：
```ruby
field :expired_at, type: DateTime, default: Time.zone.now # 第一种
field :expired_at, type: DateTime, default: -> { Time.zone.now } # 第二种
```
- 最近在这方面遇到了问题，开始的时候设置为第一种格式，导致默认时间出现了错误，查文档之后，改为放在proc中，才显示正确
- 第一种设定的默认时间为类的加载时间
- 第二种为文档状态的时间，即文档修改的时间

## 上线规则
### 上线不规范导致的问题记录

- 问题
  - 部分用户出现信息更新失败的情况
- 原因
  - 一个迭代中的新功能部署正式，上线后需要跑运维脚本，当时在忙其他工作，认为不会对其他功能造成影响，手上工作忙完后再执行脚本，在上线后到跑运维脚本之间，延期会触发某个字段更新操作，由于初始化数据有validation验证，导致更新失败
- 解决措施
  - 有问题的用户，手动执行更新操作
- 后续可改进的
  - 功能上线后，应及时跑运维脚本
  - 有数据运维的功能上线，尽量选用户使用少的时间，防止出现意外问题，将损失降到最低
  - 对于初始化数据的 Validations和Callbacks，综合全面考虑可能带来的影响