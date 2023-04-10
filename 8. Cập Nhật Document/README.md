
## Cập nhật Document trong MongoDB
Phương thức update() cập nhật các giá trị trong Document đang tồn tại.

Cú pháp cơ bản của phương thức update() là như sau:
```roomsql
>db.COLLECTION_NAME.update(SELECTIOIN_CRITERIA, UPDATED_DATA)
```

Ví dụ:

Bạn theo dõi Collection có tên mycol có dữ liệu sau:
```roomsql
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"MongoDB Overview"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point Overview"}
```


Ví dụ sau sẽ thiết lập tiêu đề mới 'New MongoDB Tutorial' của Document có tiêu đề là 'MongoDB Overview':
```roomsql
>db.mycol.update({'title':'MongoDB Overview'},{$set:{'title':'New MongoDB Tutorial'}})
>db.mycol.find()
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"New MongoDB Tutorial"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point Overview"}
>
```


Theo mặc định, MongoDB sẽ chỉ cập nhật một Document đơn, để cập nhật nhiều Document, bạn thiết lập tham số 'multi' thành true.
```roomsql
>db.mycol.update({'title':'MongoDB Overview'},{$set:{'title':'New MongoDB Tutorial'}},{multi:true})
```


## Phương thức save() trong MongoDB
Phương thức save() thay thế Document đang tồn tại với Document mới đã được truyền trong phương thức save() này.

Cú pháp cơ bản của phương thức save() như sau:
```roomsql
>db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})
```

Ví dụ:

Ví dụ sau sẽ thay thế Document với _id là '5983548781331adf45ec7'.
```roomsql
>db.mycol.save(
   {
      "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point New Topic", "by":"Tutorials Point"
   }
)
>db.mycol.find()
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"Tutorials Point New Topic", "by":"Tutorials Point"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Tutorials Point Overview"}
>
```



















