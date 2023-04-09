
## Tạo Collection trong MongoDB

Cú pháp cơ bản của lệnh createCollection() trong MongoDB như sau:
```roomsql
db.createCollection(name, options)
```
```roomsql
db.createCollection(<name>, 
  { 
    capped: <boolean>,
    autoIndexId: <boolean>,
    size: <number>,
    max: <number>,
    storageEngine: <document>,
    validator: <document>,
    validationLevel: <string>,
    validationAction: <string>,
    indexOptionDefaults: <document>,
    viewOn: <string>,
    pipeline: <pipeline>,
    collation: <document>,
    writeConcern: <document>
  } )
```

| Tham Số             | Kiểu dữ liệu | Mô tả                                                                                                                                                                                                                                                                                                                          |
|---------------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name                | string       | Tên của Collection cần tạo                                                                                                                                                                                                                                                                                                     |
| capped              | boolean      | Không bắt buộc. Để tạo Collection có giới hạn nếu giá trị là true (đúng). Nếu xác định là true, bạn cũng phải thiết lập giá trị lớn nhất của kích thước trong trường size.                                                                                                                                                     |
| size                | number       | Không bắt buộc. Xác định giá trị lớp nhất tính theo byte để giới hạn cho Collection. Khi Collection đạt đến kích thước lớn nhất thì MongoDB sẽ xoá những document (tài liệu) cũ để tạo khoảng trống cho document mới.                                                                                                          |
| max                 | number       | Không bắt buộc. Xác định số lượng lớn nhất của document được phép trong giới hạn Collection. Để giới hạn Collection thì nên sử dụng thuộc tính này để xác định giới hạn. Nếu một Collection đạt đến kích thước giới hạn số lượng document tối đa, MongoDB sẽ xoá các document cũ để đảm bảo giới hạn tối đa đã được xác định   |
| autoIndexId         | boolean      | Không bắt buộc. Xác định là false để vô hiệu hoá việc tự động đánh index (chỉ mục) cho trường _id. Bắt đầu từ MongoDB 4.0 trở về sau, bạn không thể thiết lập được tuỳ chọn autoIndexId là false khi tạo Collection trong database                                                                                             |
| usePowerOf2Sizes    | boolean      | Không bắt buộc. Chỉ có sẵn trong bộ lưu trữ MMAPv1                                                                                                                                                                                                                                                                             |
| noPadding           | boolean      | Không bắt buộc. Chỉ có sẵn trong bộ lưu trữ MMAPv1 Giá trị mặc định là false                                                                                                                                                                                                                                                   |
| storageEngine       | document     | Không bắt buộc. Chỉ có sẵn trong bộ lưu trữ WiredTiger                                                                                                                                                                                                                                                                         |
| validator           | document     | Không bắt buộc. Cho phép xác định các quy tắc hoặc biểu thức xác nhận hợp lệ cho Collection                                                                                                                                                                                                                                    |
| validationLevel     | string       | Không bắt buộc. Xác định cách MongoDB áp dụng quy tắc hợp lệ cho các document đã tồn tại trong lúc cập nhật                                                                                                                                                                                                                    |
| validationAction    | string       | Không bắt buộc. Xác định xem sẽ thông báo lỗi hay đưa ra cảnh báo khi các document không hợp lệ được thêm vào                                                                                                                                                                                                                  |
| indexOptionDefaults | document     | Không bắt buộc. Cho phép người dùng xác định cấu hình mặc định cho index (chỉ mục) trong lúc tạo Collection                                                                                                                                                                                                                    |
| viewOn              | string       | Không bắt buộc. Tên của Collection hoặc khung nhìn (view) nguồn trong lúc tạo khung nhìn. Tên không phải là namespace (không gian tên) đầy đủ của Collection hay khung nhìn, tức là không bao gồm tên CSDL như trong cùng một CSDL trong lúc khung nhìn được tạo                                                               |
| pipeline            | array        | Không bắt buộc. Là một mảng tập hợp các đoạn đường ống. Câu lệnh db.createView() tạo khung nhìn bằng cách áp dụng các đoạn đã được chỉ định cho Collection hoặc khung nhìn trong thuộc tính viewOn                                                                                                                             |
| collation           | document     | Không bắt buộc. Xác định đối chiếu mặc định cho Collection                                                                                                                                                                                                                                                                     |
| writeConcer         | document     | Không bắt buộc. Một document diễn tả mối liên hệ bằng văn bản cho các thao tác. Thường bỏ qua thuộc tính này, sử dụng chế độ ghi mặc định                                                                                                                                                                                      |


Ví Dụ:

- Tạo Collection đơn giản
```roomsql
db.createCollection("students")
```

- Tạo Collection với xác định kích thước tối đa là 1MB
```roomsql
db.createCollection("students", {
  capped: true,
  size: 1024
})
```

- Tạo Collection với xác định số lượng document (tài liệu) tối đa là 100
```roomsql
db.createCollection("students", { max: 100 })​
```

## 
1. Sử dụng phương thức createCollection(): Bạn có thể sử dụng phương thức này để tạo một collection mới trong cơ sở dữ liệu. Ví dụ:
```roomsql
db.createCollection("myCollection")
```

2. Thêm dữ liệu vào collection: Nếu bạn thêm dữ liệu vào một collection chưa tồn tại, MongoDB sẽ tự động tạo collection đó. Ví dụ:
```roomsql
db.myCollection.insertOne({name: "John", age: 30})
```

3. Copy một collection: Bạn có thể sao chép một collection bằng cách sử dụng phương thức copyTo(). Ví dụ:
```roomsql
db.myCollection.copyTo("newCollection")
```

4. Import dữ liệu từ tập tin: Bạn có thể import dữ liệu từ tập tin vào một collection bằng cách sử dụng lệnh mongoimport. Ví dụ:
```roomsql
mongoimport --db myDatabase --collection myCollection --file myData.json
```

5. Chạy một câu lệnh tạo collection trong shell: Bạn có thể chạy một câu lệnh để tạo collection trong shell bằng cách sử dụng lệnh mongo. Ví dụ:
```roomsql
mongo myDatabase --eval 'db.createCollection("myCollection")'
```












