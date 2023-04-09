
## Xóa Database trong MongoDB

Cú pháp cơ bản của lệnh dropDatabase() là như sau:
```roomsql
db.dropDatabase()
```
- Lệnh này sẽ xóa cơ sở dữ liệu đã chọn. Nếu bạn không chọn bất kỳ cơ sở dữ liệu nào, thì nó sẽ xóa cơ sở dữ liệu mặc định test.


Đầu tiên, bạn kiểm tra danh sách các cơ sở dữ liệu có sẵn bởi sử dụng lệnh show dbs.
```roomsql
>show dbs
local      0.78125GB
mydb       0.23012GB
test       0.23012GB
>
```


Nếu bạn muốn xóa cơ sở dữ liệu mới mydb, thì lệnh dropDatabase() sẽ là như sau:
```roomsql
>use mydb
switched to db mydb
>db.dropDatabase()
>{ "dropped" : "mydb", "ok" : 1 }
>
```











