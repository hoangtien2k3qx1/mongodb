
## Sắp xếp bản ghi:
Phương thức sort() trong MongoDB
- Để sắp xếp các Document trong MongoDB, bạn cần sử dụng phương thức sort(). 
- Để xác định thứ tự sắp xếp, 1 và -1 được sử dụng. 
- 1 được sử dụng cho thứ tự tăng dần, trong khi -1 được sử dụng cho thứ tự giảm dần.


#### Cú pháp cơ bản của phương thức sort() là như sau:
```roomsql
>db.COLLECTION_NAME.find().sort({KEY:1})
```

Ví Dụ:
```roomsql
// lấy ra dữ liệu document và được sắp xếp giảm dần (key:-1)
>db.mycol.find({},{"title":1, _id:0}).sort({"title":-1})
{"title":"Tutorials Point Overview"}
{"title":"NoSQL Overview"}
{"title":"MongoDB Overview"}
>
```




















