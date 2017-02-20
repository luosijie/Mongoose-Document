##Documents文档
Mongoose文档

###Retrieving检索
Mongoose检索方法有很多种,Querying章节会详细介绍

###Updating更新

Mongoose更新文档的方法有很多种,比较常见的方法可以用 findById
```
Tank.findById(id, function (err, tank) {
  if (err) return handleError(err);
  
  tank.size = 'large';
  tank.save(function (err, updatedTank) {
    if (err) return handleError(err);
    res.send(updatedTank);
  });
});
```
findById先从MongoDB检索数据,再用save方法保存修改后的数据。不过，有时候我们不需要将数据返回到应用，仅仅是想在数据库中更新,这时候就可以用
```
Tank.update({ _id: id }, { $set: { size: 'large' }}, callback);
```
如果想把文档返回到应用中，还有一个更好的方法
```
Tank.findByIdAndUpdate(id, { $set: { size: 'large' }}, { new: true }, function (err, tank) {
  if (err) return handleError(err);
  res.send(tank);
});
```
###Validating验证
文档在保存之前往往会先经过验证，Validating章节会详细介绍
