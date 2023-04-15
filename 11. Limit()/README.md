
## Giới hạn bản ghi trong MongoDB
- Để giới hạn các bản ghi trong MongoDB, bạn cần sử dụng phương thức limit(). 
- Phương thức limit() nhận một tham số ở dạng kiểu số, là số Document mà bạn muốn hiển thị.
- Có nghĩa là nó sẽ hiển thị giới hạn với number cung câp trong limit(number)

##

Cú pháp cơ bản của phương thức limit() là như sau:
```roomsql
>db.COLLECTION_NAME.find().limit(NUMBER)
```

Ví Dụ:
```roomsql
// lấy ra tất cả thông tin về 'title' với giới hạn 2 document
>db.mycol.find({},{"title":1,_id:0}).limit(2)
{"title":"MongoDB Overview"}
{"title":"NoSQL Overview"}
>
```


## Phương thức skip() trong MongoDB
- Phương thức khác là skip() cũng nhận một tham số ở dạng số và được sử dụng để nhảy qua số Document đã xác định.

Cú pháp cơ bản của phương thức skip() là như sau:
```roomsql
>db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
```

Ví Dụ:
```roomsql
// lấy ra tất cả thông tin về 'title' với giới hạn 1 document và nhảy qua 1 document
>db.mycol.find({},{"title":1,_id:0}).limit(1).skip(1)
{"title":"NoSQL Overview"}
>
```


Ví Dụ: để tạo một collection với giới hạn tối đa là 100 bản ghi, ta sử dụng lệnh sau:
```roomsql
db.createCollection("myCollection", { "max": 100 })
```














