![](https://images.viblo.asia/566f87af-2553-42b4-be61-f769444b8dc7.png)


## - Các kiểu dữ liệu trong MongoDB
| Type                    | 	Number | 	Alias                     |
|-------------------------|---------|----------------------------|
| Double                  | 	1      | 	              “double”    |
| String                  | 	2	     | “string”                   |
| Object                  | 	3      | 	“object”                  |
| Array                   | 4       | 	“array”                   |
| Binary data             | 	5      | 	“binData”                 |
| Undefined               | 	6      | 	“undefined”               |
| ObjectId                | 	7      | 	“objectId”                |
| Boolean                 | 	8	     | “bool”                     |
| Date                    | 	9      | 	“date”                    |
| Null                    | 	10     | 	“null”                    |
| Regular Expression      | 	11	    | “regex”                    |
| DBPointer               | 	12     | 	“dbPointer”               |
| JavaScript              | 	13     | 	“javascript”              |
| Symbol                  | 	14     | “symbol”                   |
| JavaScript (with scope) | 	15	    | “javascriptWithScope”      |
| 32-bit integer          | 	16	    | “int”                      |
| Timestamp               | 	17	    | “timestamp”                |
| 64-bit integer          | 	18	    | “long”                     |
| Decimal128              | 19	     | “decimal”                  |
| Min key                 | 	-1	    | “minKey”                   |
| Max key                 | 	127    | 	“maxKey”                  |

Chú Thích:
- [Chuỗi](): Đây là kiểu dữ liệu được sử dụng phổ biến nhất để lưu giữ dữ liệu. Chuỗi trong MongoDB phải là UTF-8 hợp lệ.
- [Số nguyên](): Kiểu dữ liệu này được sử dụng để lưu một giá trị số. Số nguyên có thể là 32 bit hoặc 64 bit phụ thuộc vào Server của bạn.
- [Boolean](): Kiểu dữ liệu này được sử dụng để lưu giữ một giá trị Boolean (true/false).
- [Double](): Kiểu dữ liệu này được sử dụng để lưu các giá trị số thực dấu chấm động.
- [Min/ Max keys](): Kiểu dữ liệu này được sử dụng để so sánh một giá trị với các phần tử BSON thấp nhất và cao nhất.
- [Mảng](): Kiểu dữ liệu này được sử dụng để lưu giữ các mảng hoặc danh sách hoặc nhiều giá trị vào trong một key.
- [Timestamp](): Đánh dấu thời điểm một Document được sửa đổi hoặc được thêm vào.
- [Object](): Kiểu dữ liệu này được sử dụng cho các Document được nhúng vào.
- [Null](): Kiểu dữ liệu này được sử dụng để lưu một giá trị Null.
- [Symbol](): Kiểu dữ liệu này được sử dụng giống như một chuỗi
- [Date](): Kiểu dữ liệu này được sử dụng để lưu giữ date và time hiện tại trong định dạng UNIX time.
- [Object ID](): Kiểu dữ liệu này được sử dụng để lưu giữ ID của Document.
- [Binary data](): Kiểu dữ liệu này được sử dụng để lưu giữ dữ liệu nhị phân.
- [Code](): Kiểu dữ liệu này được sử dụng để lưu giữ JavaScrip code vào trong Document.
- [Regular expression](): Kiểu dữ liệu này được sử dụng để lưu giữ Regular Expresion.



## Một số câu lệnh dùng trong MongoDB

| Câu lệnh                   | 	SQL                                                                                                                           | 	MongoDB                                                                |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Create table               | 	CREATE TABLE people (id MEDIUMINT NOT NULL AUTO_INCREMENT, user_id Varchar(30), age Number, status char(1), PRIMARY KEY (id)) | 	db.people.insertOne({User_id: “abc123”, Age: 55, Status: “A”})         |
| Drop table                 | 	DROP TABLE people                                                                                                             | 	db.people.drop()                                                       |
| Insert records into tables | 	INSERT INTO people(user_id, age, status) VALUES ("bcd001", 45, "A")	                                                          | db.people.insertOne( { user_id: "bcd001", age: 45, status: "A" })       |
| Select                     | 	SELECT *FROM people                                                                                                           | 	db.people.find()                                                       |
|                            | SELECT id,user_id, status FROM people	                                                                                         | db.people.find( { }, { user_id: 1, status: 1 } )                        |
|                            | SELECT * FROM people WHERE status = "A"                                                                                        | 	db.people.find( { status: "A" } )                                      |
|                            | SELECT * FROM people WHERE status = "A" AND age = 50                                                                           | 	db.people.find( { status: "A", age: 50 } )                             |
|                            | SELECT * FROM people WHERE status = "A" OR age = 50                                                                            | 	db.people.find( { $or: [ { status: "A" } , { age: 50 } ] } )           |
|                            | SELECT * FROM people WHERE user_id like "%bc%"                                                                                 | 	db.people.find( { user_id: /bc/ } )                                    |
|                            |                                                                                                                                | db.people.find( { user_id: { $regex: /bc/ } } )                         |
|                            | SELECT COUNT(user_id) FROM people	                                                                                             | db.people.count( { user_id: { $exists: true } } )                       |
|                            |                                                                                                                                | db.people.find( { user_id: { $exists: true } } ).count()                |
| Update records             | 	UPDATE people SET status = "C" WHERE age > 25	                                                                                | db.people.updateMany( { age: { $gt: 25 } }, { $set: { status: "C" } } ) |
|                            | UPDATE people SET age = age + 3 WHERE status = "A"	                                                                            | db.people.updateMany( { status: "A" } , { $inc: { age: 3 } } )          |
| Delete Records             | 	DELETE FROM people WHERE status = "D"	                                                                                        | db.people.deleteMany( { status: "D" } )                                 |
|                            | DELETE FROM people	                                                                                                            | db.people.deleteMany({})                                                |





## - Các thuật ngữ hay sử dụng trong MongoDB

### _id 
- Là trường bắt buộc có trong mỗi document. Trường _id đại diện cho một giá trị duy nhất trong document MongoDB. Trường _id cũng có thể được hiểu là khóa chính trong document. 
- Nếu bạn thêm mới một document thì MongoDB sẽ tự động sinh ra một _id đại diện cho document đó và là duy nhất trong cơ sở dữ liệu MongoDB.


### Collection
- Là nhóm của nhiều document trong MongoDB. Collection có thể được hiểu là một bảng tương ứng trong cơ sở dữ liệu RDBMS (Relational Database Management System). 
- Collection nằm trong một cơ sở dữ liệu duy nhất. Các collection không phải định nghĩa các cột, các hàng hay kiểu dữ liệu trước.

### Cursor
- Đây là một con trỏ đến tập kết quả của một truy vấn. 
- Máy khách có thể lặp qua một con trỏ để lấy kết quả.

### Database
- Nơi chứa các Collection, giống với cơ sở dữ liệu RDMS chúng chứa các bảng.
- Database có một tập tin riêng lưu trữ trên bộ nhớ vật lý. Một mấy chủ MongoDB có thể chứa nhiều Database.

### Document 
- Một bản ghi thuộc một Collection thì được gọi là một Document.
- Document lần lượt bao gồm các trường tên và giá trị.

### Field 
- Là một cặp name – value trong một document.
- Một document có thể có không hoặc nhiều trường. Các trường giống các cột ở cơ sở dữ liệu quan hệ.

### JSON
- Viết tắt của JavaScript Object Notation.
- Định dạng văn bản đơn giản thể hiện cho các dữ liệu có cấu trúc.

### Index
- Là những cấu trúc dữ liệu đặc biệt, dùng để chứa một phần nhỏ của các tập dữ liệu một cách dễ dàng để quét.
- Chỉ số lưu trữ giá trị của một fields cụ thể hoặc thiết lập các fields, sắp xếp theo giá trị của các fields này.


![](https://images.viblo.asia/c17118e5-9791-462f-878c-a51778dc357d.jpg)






















