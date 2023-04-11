
## Chỉ mục (Index) trong MongoDB
Phương thức ensureIndex() trong MongoDB

Cú pháp cơ bản của phương thức ensureIndex() là như sau:
```roomsql
>db.COLLECTION_NAME.ensureIndex({KEY:1})
```


Ví Dụ:

```roomsql
>db.mycol.ensureIndex({"title":1})
>

///////////////////////////////////////////////

>db.mycol.ensureIndex({"title":1,"description":-1})
>
```











