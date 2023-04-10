
## Chèn Document trong MongoDB

1. Sử dụng phương thức insertOne(): Phương thức này được sử dụng để chèn một tài liệu vào một bộ sưu tập. Ví dụ:
```roomsql
db.collection('myCollection').insertOne({ name: 'John', age: 30 });
```

2. Sử dụng phương thức insertMany(): Phương thức này được sử dụng để chèn nhiều tài liệu vào một bộ sưu tập. Ví dụ:
```roomsql
db.collection('myCollection').insertMany([
  { name: 'John', age: 30 },
  { name: 'Jane', age: 25 }
]);
```

3. Sử dụng phương thức bulkWrite(): Phương thức này được sử dụng để thực hiện nhiều thao tác chèn dữ liệu và/hoặc cập nhật dữ liệu trong một bộ sưu tập. Ví dụ:
```roomsql
db.collection('myCollection').bulkWrite([
  { insertOne: { name: 'John', age: 30 } },
  { insertOne: { name: 'Jane', age: 25 } },
  { updateOne: { filter: { name: 'John' }, update: { $set: { age: 31 } } } }
]);
```

















