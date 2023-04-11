
## Aggregation trong MongoDB
Trong SQL, count(*) và GROUP BY là tương đương với Aggregation trong MongoDB.

#### Phương thức aggregate() trong MongoDB
Cú pháp cơ bản của phương thức aggregate() là như sau:
```roomsql
>db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```

```roomsql
<=> Một số Operation cơ bản trong Aggregation :

$project : chỉ định các field mong muốn truy vấn.
$match : chọn document mong muốn truy vấn.
$limit: giới hạn số lượng document
$skip : bỏ qua document nhất định
$group: nhóm các document theo điều kiện nhất định
$sort: sắp xếp document
$unwind : thực hiện thao tác mở rộng trên một mảng , tạo một ouput document cho mỗi giá trị trong mảng đó
$out : ghi kết quả sau khi thực hiện trên pipeline vào một collection. (chỉ áp dụng đối với version 2.6 trở đi)
```


### Bảng so sánh giữa SQL và aggregation framework :
| SQL command | Aggregation framework operator                    | 
|-------------|---------------------------------------------------|
| SELECT      | $project $group functions: $sum, $min, $avg, etc. | 
| FROM        | db.collectionName.aggregate(...)                  |
| JOIN        | $unwind                                           |
| GROUP BY    | $group                                            |
| HAVING      | $match                                            |




| Biểu thức | Miêu tả                                                                          | Ví dụ                                                                                      |
|-----------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| $sum      | 	Tổng giá trị được xác định từ tất cả Document trong Collection đó               | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}])      |
| $avg      | Tính trung bình của tất cả giá trị đã cho từ tất cả Document trong Collection đó | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}])      |
| $min      | Lấy giá trị nhỏ nhất của các giá trị từ tất cả Document trong Collection đó      | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}])      |
| $max      | Lấy giá trị lớn nhất của các giá trị từ tất cả Document trong Collection đó      | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}])      |
| $push     | Chèn giá trị vào trong một mảng trong Document kết quả                           | db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}])                 |
| $addToSet | Chèn giá trị tới một mảng trong Document kết quả, nhưng không tạo các bản sao    | db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}])            |
| $first    | Lấy Document đầu tiên từ Source Document theo nhóm                               | db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}])         |
| $last     | Lấy Document cuối cùng từ Source Document theo nhóm                              | db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}])           |























