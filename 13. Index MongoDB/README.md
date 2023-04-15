
## Chỉ mục (Index) trong MongoDB
- Chỉ mục (Index) hỗ trợ việc phân giải các truy vấn hiệu quả hơn.
- Nếu không có chỉ mục, MongoDB phải quét qua mọi Document của một Collection để chọn các Document mà kết nối với lệnh truy vấn.
- Việc quét này có thể không hiệu quả và yêu cầu MongoDB xử lý một số lượng lớn dữ liệu.
- Chỉ mục (Index) là các cấu trúc dữ liệu đặc biệt, lưu giữ một phần nhỏ của tập hợp dữ liệu, giúp việc "vọc" vào Collection một cách dễ dàng hơn.
- Chỉ mục lưu giữ giá trị của một trường cụ thể hoặc tập hợp các trường, được sắp xếp bởi giá trị của trường như đã được xác định trong chỉ mục.


## Phương thức ensureIndex() trong MongoDB
- Để tạo một chỉ mục, bạn cần sử dụng phương thức ensureIndex() của MongoDB.

Cú pháp cơ bản của phương thức ensureIndex() là như sau:
```roomsql
>db.COLLECTION_NAME.ensureIndex({KEY:1})
```
Trong đó:
key là tên của trường mà bạn muốn tạo chỉ mục
- 1 là cho thứ tự tăng dần.
- -1 tạo chỉ mục theo thứ tự giảm dần.


Ví Dụ:
```roomsql
>db.mycol.ensureIndex({"title":1})
>

///////////////////////////////////////////////

>db.mycol.ensureIndex({"title":1,"description":-1})
>
```

| Tham số            | 	Kiểu            | 	Miêu tả                                                                                                                                                                                                                                                                         |
|--------------------|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| background         | 	Boolean         | 	Xây dựng chỉ mục trong Background để mà nó không gây trở ngại các hoạt động cơ sở dữ liệu khác. Xác định true để xây dựng trong Background. Giá trị mặc định là false                                                                                                           |
| unique             | 	Boolean         | 	Tạo một unique index để mà Collection đó sẽ không chấp nhận việc chèn các Document có key kết nối với một giá trị đang tồn tại trong chỉ mục. Xác định là true để tạo unique index. Giá trị mặc định là false                                                                   |
| name               | 	Chuỗi           | 	Tên của chỉ mục. Nếu không được xác định, MongoDB tạo một tên chỉ mục bằng cách nối chuỗi các tên của các trường đã được lập chỉ mục và sắp xếp thứ tự                                                                                                                          |
| dropDups           | 	Boolean         | 	Tạo một dropDups index trên một trường mà có thể có các bản sao. MongoDB chỉ lập chỉ mục choc ho lần xuất hiện đầu tiên của key và xóa tất cả Document từ Collection mà chứa lần xuất hiện tiếp theo của key đó. Xác định true để tạo dropDups index. Giá trị mặc định là false |
| sparse             | 	Boolean         | 	Nếu true, chỉ mục chỉ tham chiếu tới các Document với trường đã xác định. Các chỉ mục này sử dụng ít không gian hơn, nhưng vận hành theo cách khác nhau trong một số tình huống (cụ thể với sắp xếp). Giá trị mặc định là false                                                 |
| expireAfterSeconds | 	Số nguyên       | 	Xác định một giá trị (bằng giây), dưới dạng một TTL để điều khiển thời gian bao lâu MongoDB duy trì các Document trong Collection này                                                                                                                                           |
| v                  | 	Phiên bản index | 	Số phiên bản của chỉ mục. Phiên bản mặc định phụ thuộc vào phiên bản của MongoDB đang chạy khi tạo chỉ mục                                                                                                                                                                      |
| weights            | 	document        | 	Là một số trong dãy từ 1 tới 99999 và biểu thị ý nghĩa của trường quan hệ tới các trường được lập chỉ mục khác về mặt score                                                                                                                                                     |
| default_language   | 	Chuỗi           | 	Với một text index, đây là ngôn ngữ xác định các qui tắc của chỉ mục. Giá trị mặc định là english                                                                                                                                                                               |
| language_override  | 	Chuỗi           | 	Với một text index, xác định tên của trường được chứa trong Document, ngôn ngữ để nạp chồng ngôn ngữ mặc định. Giá trị mặc định là language                                                                                                                                     |









