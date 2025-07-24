# MySQL
## I. Giới thiệu chung
- download: [MySQL Community Server v8.4.6 LTS](https://dev.mysql.com/downloads/mysql/)
- run MySQL 
``` bash
# ~\MySQL\bin>
mysql.exe -u<user> -p<password>
```
## II. Kiến trúc MySQL
## III. MySQL base
### Database
``` sql
USE <Database_name>
```
### CREATE
- Tạo bảng trống
``` sql
CREATE TABLE <Table_name>;
```
- Tạo bảng lấy dữ lệu từ bản khác
``` sql
CREATE TABLE <Table_new> 
AS SELECT <feild> from <Table_name>;
```
- Mô tả các thông tin của bảng
``` sql
DESC <Table_name>;
```
### SELECT
- Hiển thị một phần dữ liệu
``` sql
SELECT <feild ...> FROM <Table_name> 
``` 
- Hiển thị toàn bộ dữ liệu
``` sql
SELECT * FROM <Table_name> 
``` 
### WHERE
``` sql
SELECT <feild ...> FROM <Table_name> 
WHERE <condition ...>
```
### Operators
|Operator|Description|
|:-------|:----------|
|=|	Bằng	|
|>|	lớn hơn	|
|<|	nhỏ hơn	|
|>=|	lớn hơn hoắc bằng	|
|<=|	nhỏ hơn hoặc bằng	|
|<>|	khác|
|BETWEEN|	giữa giải giá trị	|
|LIKE|	tìm kiếm một mẫu ex: 'C%' -> chuỗi bắt đầu bằng C	|
|IN| Chỉ định nhiều giá trị có thể có cho một cột|
|AND| hiển thị bảng ghi nếu tất cả điều kiện được phân tách bằng AND đều đúng  | 
|OR|hiển thị bảng ghi nếu một trong số điều kiện được phân tách bằng OR đều đúng|
|NOT|hiển thị một bản ghi nếu điều kiện KHÔNG ĐÚNG|
### ORDER BY
``` sql
SELECT <feild ...> 
FROM <Table_name>
ORDER BY <feild ...> ASC|DESC;
```
- ASC : Sắp xếp theo thứ tự tăng dần
- DESC: Sắp xếp theo thứ tự giảm dần
### INSERT INTO
``` sql
INSERT INTO table_name (feild1, feild2, feild3, ...)
VALUES (value1, value2, value3, ...);
```

### NULL
NULL là trường không có giá trị 
``` sql
SELECT <feild ...>
FROM <table_name>
WHERE <feild ...> IS (NOT) NULL;
```

### UPDATE
``` sql
UPDATE <table_name>
SET feild1 = value1, feild2 = value2, ...
WHERE <condition ...>;
```



### Gom nhóm dữ liệu 
select countrycode, count(*) form city group by countrycode

Lấy dữ liệu từ nhiều bảng

### Thêm dữ liệu vào bảng
insert into <> values(feilds)
``` sql
```

## Tối ưu hoá 
