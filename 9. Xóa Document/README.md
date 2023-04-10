
## Xóa Document trong MongoDB

Phương thức remove() trong MongoDB
- Phương thức remove() trong MongoDB được sử dụng để xóa Document từ Collection. Phương thức remove() nhận hai tham số.
  1. deletion criteria : (Tùy ý) Xác định Document để xóa.
  2. justOne : (Tùy ý) Nếu được thiết lập là true hoặc 1, thì chỉ xóa một Document.


Cú pháp cơ bản của phương thức remove() là như sau:
```roomsql
>db.COLLECTION_NAME.remove(DELLETION_CRITTERIA)
```


Ví dụ:

Bạn theo dõi Collection có tên mycol có dữ liệu sau:
```roomsql
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"MongoDB Overview"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point Overview"}
```

Ví dụ sau sẽ xóa tất cả Document có title là 'MongoDB Overview':
```roomsql
>db.mycol.remove({'title':'MongoDB Overview'})
>db.mycol.find()
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point Overview"}
>
```


## Chỉ xóa một Document trong MongoDB
Nếu có nhiều bản ghi và bạn chỉ muốn xóa bản ghi đầu tiên, thì thiết lập tham số justOne trong phương thức remove().
```roomsql
>db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)
```

## Xóa tất cả Document trong MongoDB
Nếu bạn không xác định deletion criteria, thì MongoDB sẽ xóa toàn bộ Document từ Collection. Điều này tương đương với lệnh truncate trong SQL.
```roomsql
>db.mycol.remove()
>db.mycol.find()
>
```























