# 起步
> 开始使用Mongoose前，请先安装好[MongoDB](http://www.mongodb.org/downloads)和[Node.js](https://nodejs.org/en/)
#### npm安装mongoose

```bash
$ npm install mongoose
``` 

#### 连接MongoDBa数据库
```js
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/test');
```

#### 监听数据库连接状态
```js
var db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', function (callback) {
  // yay!
});
```

#### 定义模式
```js
var kittySchema = mongoose.Schema({
    name: String
})
```

#### 将模式编译为模型
```js
var Kitten = mongoose.model('Kitten', kittySchema)
```

#### 由模型 New 一个实例
```js
var silence = new Kitten({ name: 'Silence' })
console.log(silence.name) // 'Silence'
```
    
#### 为模式创建方法
methodss方法必须在schema编译为model之前添加
```js
kittySchema.methods.speak = function () {
  var greeting = this.name
    ? "Meow name is " + this.name
    : "I don't have a name"
  console.log(greeting);
}
var Kitten = mongoose.model('Kitten', kittySchema)
```

#### 文档实例使用methods方法
```js
var fluffy = new Kitten({ name: 'fluffy' });
fluffy.speak() // "Meow name is fluffy"
```
    
#### 保存文档实例
```js
fluffy.save(function (err, fluffy) {
  if (err) return console.error(err);
  fluffy.speak();
});
```

#### 查询文档实例
.find()可以查询并返回对应集合里面的所有文档
```js
Kitten.find(function (err, kittens) {
  if (err) return console.error(err);
  console.log(kittens)
})
```

#### 通过条件查询文档实例
```js
Kitten.find({ name: /^Fluff/ }, callback)
```



    

    







    

