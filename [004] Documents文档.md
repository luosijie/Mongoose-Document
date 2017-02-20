##Documents文档
Mongoose文档

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
