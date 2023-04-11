
## Projection in MongoDB

- Trong MongoDB, ý nghĩa của projection là chỉ chọn dữ liệu cần thiết thay vì chọn toàn bộ dữ liệu của một Document. 
- Nếu một Document có 5 trường và bạn chỉ cần 3 trường, thì bạn chỉ nên chọn 3 trường từ Document đó.


Phhương Thức find() trong MongoDB: tìm kiếm và hiên thị thông tin trong document:
- Để giới hạn điều này, bạn cần thiết lập danh sách các trường với giá trị 1 hoặc 0. 
- Giá trị 1 được sử dụng để hiển thị trường, trong khi 0 được sử dụng để ẩn trường.


Syntax find() trong projection:
```roomsql
db.COLLECTION_NAME.find({condition},{field1:1,field2:0,...})
```

Trong đó:
- {condition}: là điều kiện tìm kiếm, nếu bạn để {} thì nó sẽ tìm tất cả document.
- field1:1: biểu thị field1 sẽ được hiển thị trong kết quả trả về. (Mặc định trường _id luôn trược trả về)
- field2:0: biểu thị field2 sẽ không được hiển thị trong kết quả trả về.


## Hiển thị name của tất cả các document thì câu lệnh sẽ là:
```roomsql
db.testmongo.find({}, {'name':1})

=> tuơng đương với SQL 
Select _id, name From testmongo
```


Ví Dụ:
```roomsql
db.testmongo.insertMany([
	{'_id':'1', 'name':'neymar', 'email':'hoangtien2k3qx1@gmail.com', 'age':25},
	{'_id':'2', 'name':'hazard', 'email':'2k3qx1@gmail.com', 'age':25},
	{'_id':'3', 'name':'mbappe', 'email':'hoang2k3qx1@gmail.com', 'age':18},
	{'_id':'4', 'name':'modric', 'email':'tien2k3qx1@gmail.com', 'age':30},
	{'_id':'5', 'name':'ronaldo', 'email':'qx1@gmail.com', 'age':33}
]
)

// lấy ra toàn bộ dữ liệu trong Collection testmongo
// tương đương Select * From testmongo
db.testmongo.find() 


// lấy dữ liệu của một cột _id trong document _id
// SQL: Select _id From testmongo
db.testmongo.find({}, {'_id':1}) 



// lấy ra age trong Collection với điều kiện age = 25
// name:1 có nghĩa là hiển thị thông tin của cột tuổi phù hợp với điều kiện
// _id:0 có nghĩa là ẩn thông tin của cột _id (không hiển thị nó ra)
// SQL: Select name, _id From age = 25
db.testmongo.find({'age':25}, {'name':1, '_id':0})
```









