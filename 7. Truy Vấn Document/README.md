
## Truy vấn Document trong MongoDB

Cú pháp cơ bản của phương thức find() là như sau:
```roomsql
>db.COLLECTION_NAME.find()
```

Để hiển thị các kết quả theo một cách đã được định dạng, bạn có thể sử dụng phương thức pretty().
```roomsql
>db.mycol.find().pretty()
```

```roomsql
Ví Dụ:

    >db.mycol.find().pretty()
    {
       "_id": ObjectId(7df78ad8902c),
       "title": "MongoDB Overview", 
       "description": "MongoDB is no sql database",
       "by": "tutorials point",
       "url": "http://www.tutorialspoint.com",
       "tags": ["mongodb", "database", "NoSQL"],
       "likes": "100"
    }
    >
```


### Truy vấn trong MongoDB mà tương đương mệnh đề WHERE trong RDBMS

| Phép toán           | Cú pháp                | Ví dụ                                            | WHERE tương đương            |
|---------------------|------------------------|--------------------------------------------------|------------------------------|
| Equality            | {<key>:<value>}        | db.mycol.find({"by":"tutorials point"}).pretty() | where by = 'tutorials point' |
| Less Than           | {<key>:{$lt:<value>}}  | db.mycol.find({"likes":{$lt:50}}).pretty()       | where likes < 50             |
| Less Than Equals    | {<key>:{$lte:<value>}} | db.mycol.find({"likes":{$lte:50}}).pretty()      | where likes <= 50            |
| Greater Than        | {<key>:{$gt:<value>}}  | db.mycol.find({"likes":{$gt:50}}).pretty()       | where likes > 50             |
| Greater Than Equals | {<key>:{$gte:<value>}} | db.mycol.find({"likes":{$gte:50}}).pretty()      | where likes >= 50            |
| Not Equals          | {<key>:{$ne:<value>}}  | db.mycol.find({"likes":{$ne:50}}).pretty()       | where likes != 50            |


### AND trong MongoDB
Trong phương thức find(), nếu bạn truyền nhiều key bằng cách phân biệt chúng bởi dấu phảy (,), thì MongoDB xem nó như là điều kiện AND. Cú pháp cơ bản của AND trong MongoDB như sau:
```roomsql
>db.mycol.find({key1:value1, key2:value2}).pretty()
```


Ví Dụ:
- Ví dụ sau hiển thị tất cả loạt bài hướng dẫn (tutorials) được viết bởi 'tutorials point' có title là 'MongoDB Overview'
```roomsql
>db.mycol.find({"by":"tutorials point","title": "MongoDB Overview"}).pretty()
{
   "_id": ObjectId(7df78ad8902c),
   "title": "MongoDB Overview", 
   "description": "MongoDB is no sql database",
   "by": "tutorials point",
   "url": "http://www.tutorialspoint.com",
   "tags": ["mongodb", "database", "NoSQL"],
   "likes": "100"
}
>

/////////////////////////////////////////////////////
Nó sẽ tương đương với RDBMS sau:
where by='tutorials point' AND title='MongoDB Overview'
```


### OR trong MongoDB
- Để truy vấn Document dựa trên điều kiện OR, bạn cần sử dụng từ khóa $or. Cú pháp cơ bản của OR trong MongoDB như sau:
```roomsql
>db.mycol.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```

Ví Dụ:
```roomsql

```>db.mycol.find({$or:[{"by":"tutorials point"},{"title": "MongoDB Overview"}]}).pretty()
{
   "_id": ObjectId(7df78ad8902c),
   "title": "MongoDB Overview", 
   "description": "MongoDB is no sql database",
   "by": "tutorials point",
   "url": "http://www.tutorialspoint.com",
   "tags": ["mongodb", "database", "NoSQL"],
   "likes": "100"
}
>



### Sử dụng AND và OR cùng nhau trong MongoDB
```roomsql
>db.mycol.find({"likes": {$gt:10}, $or: [{"by": "tutorials point"},{"title": "MongoDB Overview"}]}).pretty()
{
   "_id": ObjectId(7df78ad8902c),
   "title": "MongoDB Overview", 
   "description": "MongoDB is no sql database",
   "by": "tutorials point",
   "url": "http://www.tutorialspoint.com",
   "tags": ["mongodb", "database", "NoSQL"],
   "likes": "100"
}
>


///////////////////////////////////////////////////////////
Tương đương với:
where likes>10 AND (by = 'tutorials point' OR title = 'MongoDB Overview')
```
















