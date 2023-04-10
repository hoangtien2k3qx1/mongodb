
## Xóa Collection trong MongoDB

Cú pháp cơ bản của lệnh drop() là như sau:
```roomsql
db.COLLECTION_NAME.drop()
```


Ví Dụ:

Đầu tiên, bạn kiểm tra các Collection có sẵn bên trong cơ sở dữ liệu mydb.

```roomsql
>use mydb
switched to db mydb
>show collections
mycol
mycollection
system.indexes
tutorialspoint
>
```

Bây giờ, bạn xóa Collection với tên mycollection như sau:
```roomsql
>show collections
mycol
system.indexes
tutorialspoint
>
```

















