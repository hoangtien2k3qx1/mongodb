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
