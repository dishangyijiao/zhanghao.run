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
product.update(itme: new_item)
```

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
