
## Xóa Document trong MongoDB

Để xóa một document trong một collection trong MongoDB, có thể sử dụng các phương thức như `deleteOne()`, `deleteMany()`, `findOneAndDelete()` hoặc `remove()`.


1. Phương thức deleteOne(): xóa một document đầu tiên trùng với điều kiện
```roomsql
db.collection('ten_collection').deleteOne({name: 'ABC'}).then(function(){
   console.log("Xóa document thành công");
});
```

2. Phương thức deleteMany(): xóa tất cả các document thỏa mãn điều kiện
```roomsql
db.collection('ten_collection').deleteMany({name: 'ABC'}).then(function(){
   console.log("Xóa tất cả các documents thành công");
});
```

3. Phương thức findOneAndDelete(): Tìm và xóa một document trùng với điều kiện, sau đó trả về document đã xóa.
```roomsql
db.collection('ten_collection').findOneAndDelete({name: 'ABC'}).then(function(result){
   console.log(result.value); // Document đã xóa
});
```














