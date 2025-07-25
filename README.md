# MySQL
## I. Giới thiệu chung
- download: [MySQL Community Server v8.4.6 LTS](https://dev.mysql.com/downloads/mysql/)
- run MySQL 
``` bash
# ~\MySQL\bin>
mysql.exe -u <user> -p <password>
```
## II. Kiến trúc MySQL
## III. MySQL SQL
### 1. Data Type
### 2. Comment
### 3. SELECT
- SELECT thường dùng để chọn dữ liệu từ database 
- Hiển thị một phần dữ liệu
``` sql
SELECT <feild ...> FROM <Table_name>;
``` 
- Hiển thị toàn bộ dữ liệu
``` sql
SELECT * FROM <Table_name>;
``` 
### 4. WHERE
- WHERE được dùng để sử dụng để lọc bản ghi
``` sql
SELECT <feild ...> FROM <Table_name> 
WHERE <condition ...>;
```
### 5. Operators
#### Arithmetic Operators
#### Bitwise Operators
#### Comparison Operators
#### Compound Operators
#### Logical Operators

#### Toán tử so sánh
|Operator|Description|
|:-------|:----------|
|=|	Bằng	|
|>|	lớn hơn	|
|<|	nhỏ hơn	|
|>=|	lớn hơn hoắc bằng	|
|<=|	nhỏ hơn hoặc bằng	|
|<>|	khác|

#### Toán tử quan hệ
|Operator|Description|
|:-------|:----------|
|AND| hiển thị bảng ghi nếu tất cả điều kiện được phân tách bằng AND đều đúng  | 
|OR|hiển thị bảng ghi nếu một trong số điều kiện được phân tách bằng OR đều đúng|
|NOT|hiển thị một bản ghi nếu điều kiện KHÔNG ĐÚNG|

#### IN
- IN Chỉ định nhiều giá trị có thể có cho một cột
``` sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

#### BETWEEN
- BETWEEN chỉ định giá trị giữa dải	
``` sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

#### LIKE
- LIKE được tìm kiếm một mẫu đã được chỉ định trong một trường.
``` sql
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```
- Có hai ký tự đại diện thường được sử dụng kết hợp với toán tử LIKE:

    - % : biểu thị không, một hoặc nhiều ký tự
    - _ : biểu thị một ký tự đơn

| Toán tử | Mô tả |
|:--------|:------|
| 'a%' |Tìm bất kỳ giá trị nào bắt đầu bằng "a"|
| '%a' |Tìm bất kỳ giá trị nào kết thúc bằng "a"|
| '%or%'| Tìm bất kỳ giá trị nào có "or" ở bất cứ vị trí nào |
| '_r%' | Tìm bất cứ giá trị nào có "r" ở vị trí thứ 2 |
| 'a_%' | Tìm bất kỳ giá trị nào bắt đầu bằng "a" và có độ dài ít nhất 2 ký tự |
| 'a__%' |Tìm bất kỳ giá trị nào bắt đầu bằng "a" và có độ dài ít nhất 3 ký tự|
| 'a%o' |Tìm bất kỳ giá trị nào bắt đầu bằng "a" và kết thúc bằng "o"|

### 6. ORDER BY
- ORDER BY dùng để sắp xếp dữ liệu  tăng/giảm dần trong bảng
    - ASC : Sắp xếp theo thứ tự tăng dần
    - DESC: Sắp xếp theo thứ tự giảm dần
``` sql
SELECT <feild ...> 
FROM <Table_name>
ORDER BY <feild ...> <ASC|DESC>;
```

### 7. INSERT INTO
- INSERT INTO dùng để chèn phần tử vào bản ghi 
``` sql
INSERT INTO table_name (feild1, feild2, feild3, ...)
VALUES (value1, value2, value3, ...);
```
#### INSERT INTO SELECT
- Câu lệnh INSERT INTO SELECT sao chép dữ liệu từ một bảng và chèn vào một bảng khác.
- Câu lệnh INSERT INTO SELECT yêu cầu kiểu dữ liệu trong bảng nguồn và bảng đích phải khớp nhau.
``` sql
INSERT INTO table2
SELECT * FROM table1
WHERE condition;
```
``` sql
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```
### 8. NULL
- NULL là trường không có giá trị. Được dùng trong các điều kiện so sánh 
``` sql
SELECT <feild ...>
FROM <table_name>
WHERE <feild ...> IS (NOT) NULL;
```

### 9. UPDATE
- UPDATE được sử dụng để sửa đổi các bản ghi hiện có trong một bảng.
``` sql
UPDATE <table_name>
SET feild1 = value1, feild2 = value2, ...
WHERE <condition ...>;
```

### 10. DELELTE 
- DELETE được sử dụng để xóa các bản ghi hiện có trong một bảng.
```sql
DELETE FROM <Table_name> 
WHERE <condition ...>;
```

### 11. LIMIT
- LIMIT được sử dụng để chỉ định số lượng bản ghi cần trả về.
- LIMIT hữu ích trên các bảng lớn với hàng nghìn bản ghi.Việc trả về một số lượng lớn bản ghi có thể ảnh hưởng đến hiệu suất.
``` sql
SELECT <feild ...> FROM <Table_name> 
WHERE <condition ...> 
LIMIT number;
```
### 12. AS 
- AS được sử dụng để đặt tên tạm thời cho một bảng hoặc một cột trong bảng. 
- Tên chỉ tồn tại trong khoảng thời gian của truy vấn đó.
``` sql
SELECT column_name AS alias_name
FROM table_name;
```

### 13. JOIN
- JOIN được sử dụng để kết hợp các hàng từ hai hoặc nhiều bảng, dựa trên cột có liên quan giữa chúng.
- các loại JOIN được hỗ trợ trên MySQL

![image](./Tutorial_imgs/JOIN.png)

#### i. INNER JOIN
- ``INNER JOIN`` chọn tất cả các hàng từ cả hai bảng miễn là có sự trùng khớp giữa các cột. Nếu có bản ghi trong bảng "table1" không trùng khớp với "table2", những đơn hàng này sẽ không được hiển thị!
``` sql
SELECT <feild ...>  
FROM <Table_name1>
INNER JOIN <Table_name2> 
ON table1.column_name = table2.column_name;
```

#### ii. LEFT JOIN
- LEFT JOIN trả về tất cả các bản ghi từ bảng bên trái (table1) và các bản ghi khớp (nếu có) từ bảng bên phải (table2).
``` sql
SELECT <feild ...>  
FROM <Table_name1>
LEFT JOIN <Table_name2> 
ON table1.column_name = table2.column_name;
```

#### iii. RIGHT JOIN
- RIGHT JOIN trả về tất cả các bản ghi từ bảng bên phải (table2) và các bản ghi khớp (nếu có) từ bảng bên trái (table1).
``` sql
SELECT <feild ...>  
FROM <Table_name1>
RIGHT JOIN <Table_name2> 
ON table1.column_name = table2.column_name;
```

#### iv. CROSS JOIN
- CROSS JOIN trả về tất cả các bản ghi từ cả hai bảng (table1 và table2).
``` sql
SELECT <feild ...>  
FROM <Table_name1>
CROSS JOIN <Table_name2> ;
```

### 14. UNION
- UNION được sử dụng để kết hợp tập kết quả của hai hoặc nhiều câu lệnh SELECT.

    - Mỗi câu lệnh SELECT trong UNION phải có cùng số cột
    - Các cột cũng phải có kiểu dữ liệu tương tự
    - Các cột trong mỗi câu lệnh SELECT cũng phải có cùng thứ tự
- UNION chỉ cho phép chọn giá trị riêng biệt
```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```
- UNION cho phép chọn cả các giá trị trùng lắp
``` sql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```


### 15. GROUP BY
- GROUP BY nhóm các hàng có cùng giá trị vào các hàng tóm tắt, chẳng hạn như "tìm số lượng khách hàng ở mỗi quốc gia".

- GROUP BY thường được sử dụng với các hàm tổng hợp (COUNT(), MAX(), MIN(), SUM(), AVG()) để nhóm tập kết quả theo một hoặc nhiều cột.
``` sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```
### 16. HAVING
- HAVING được thêm vào SQL vì từ khóa WHERE không thể được sử dụng với các hàm tổng hợp
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

### 17. EXISTS
- EXISTS được sử dụng để kiểm tra sự tồn tại của bất kỳ bản ghi nào trong một truy vấn con.
- EXISTS trả về TRUE nếu truy vấn con trả về một hoặc nhiều bản ghi.
```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

## IV. MySQL Database
### 1. Database
#### i. CREATE DATABASE
``` sql
CREATE DATABASE <Database_name>;
```
#### ii. DROP DATABASE
``` sql
DROP DATABASE <Database_name>;
```
#### iii. USE DATABASE
``` sql
USE <Database_name>
```
### 2. TABLE
#### i. CREATE TABLE
- Tạo bảng trống
``` sql
CREATE TABLE <Table_name>;
```
- Tạo bảng lấy dữ lệu từ bản khác
``` sql
CREATE TABLE <Table_new> 
AS SELECT <feild> from <Table_name>;
```
#### ii. DROP TABLE
```sql
DROP TABLE table_name;
```
#### iii. DESC TABLE
- Hiển thị mô tả thông tin của bảng
``` sql
DESC <Table_name>;
```
#### iv. ALTER TABLE
- ALTER TABLE được sử dụng để thêm, xóa hoặc sửa đổi các cột trong một bảng hiện có.
- ALTER TABLE cũng được sử dụng để thêm và xóa các ràng buộc khác nhau trên một bảng hiện có.
``` sql
ALTER TABLE table_name
ADD column_name datatype;
```
#### v. constraint
- 
``` sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);
```
### 3. NOT NULL
- Ràng buộc NOT NULL buộc một cột KHÔNG chấp nhận giá trị NULL.
- Ràng buộc này buộc một trường luôn chứa một giá trị, nghĩa là bạn không thể chèn bản ghi mới hoặc cập nhật bản ghi mà không thêm giá trị vào trường này.
``` sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```
### 4. UNIQUE
- Ràng buộc UNIQUE đảm bảo rằng tất cả các giá trị trong một cột đều khác nhau.

### 5. PRIMARY KEY
- Giới thiệu chung
    - Ràng buộc PRIMARY KEY xác định duy nhất mỗi bản ghi trong một bảng.
    - Khóa chính phải chứa các giá trị DUY NHẤT và không thể chứa các giá trị NULL.
    - Một bảng chỉ có thể có MỘT khóa chính; và trong bảng, khóa chính này có thể bao gồm một hoặc nhiều cột.
#### i. Tạo khoá chính
##### Tạo PRIMARY KEY trong khi tạo bảng
- Tạo một khoá chính
``` sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```
- Tạo một khoá chính từ 2/nhiều cột
``` sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```
##### Tạo PRIMARY KEY từ bảng có sẵn
- Tạo một khoá chính
```sql
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
```
- Tạo một khoá chính từ 2/nhiều cột
```sql
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID);
```
#### ii. Xoá khoá
``` sql
ALTER TABLE Persons
DROP PRIMARY KEY;
```
### 6. FOREIGN KEY
- FOREIGN KEY được sử dụng để ngăn chặn các hành động phá hủy liên kết giữa các bảng.
- FOREIGN KEY là một trường (hoặc tập hợp các trường) trong một bảng, tham chiếu đến KHÓA CHÍNH trong một bảng khác.
- Bảng có FOREIGN KEY được gọi là bảng con, và bảng có PRIMARY KEY  được gọi là bảng tham chiếu hoặc bảng cha.

Hãy xem xét hai bảng sau:
### 7. Check
- CHECK được sử dụng để giới hạn phạm vi giá trị có thể được đặt trong một cột/bảng.
#### i. CHECK Trong khi tạo bảng
``` sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
);
```
#### ii. CHECK Trong khi có bảng đã tồn tại
``` sql
ALTER TABLE Persons
ADD CONSTRAINT CHK_PersonAge CHECK (Age>=18 AND City='Sandnes');
```
#### iii. DROP a CHECK Constraint 
```sql 
ALTER TABLE Persons
DROP CHECK CHK_PersonAge;
```
### 8. Default
- DEFAULT được sử dụng để đặt giá trị mặc định cho một cột.
- Giá trị mặc định sẽ được thêm vào tất cả các bản ghi mới, nếu không có giá trị nào khác được chỉ định.
#### i. DEFAULT trong khi tạo bảng
``` sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);
```
#### ii. DEFAULT Trong khi có bảng đã tồn tại
``` sql
ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';
```
#### iii. Xoá DEFAULT
``` sql
ALTER TABLE Persons
ALTER City DROP DEFAULT;
```

### 9. INDEX
#### i. Tạo INDEX trên cột
- Tạo INDEX trên một bảng. Cho phép các giá trị trùng lặp
``` sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```
- Tạo INDEX duy nhất trên một bảng. Không cho phép các giá trị trùng lặp
``` sql
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```
#### ii. Xoá INDEX
``` sql
ALTER TABLE table_name
DROP INDEX index_name;
```
### 10. AUTO_INCREMENT
- AUTO_INCREMENT để thực hiện tính năng tự động tăng.
- Theo mặc định, giá trị khởi đầu của AUTO_INCREMENT là 1 và sẽ tăng thêm 1 cho mỗi bản ghi mới.
```sql
CREATE TABLE Persons (
    Personid int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (Personid)
);
```
``` sql
ALTER TABLE Persons AUTO_INCREMENT=100;
```






## Tối ưu hoá 
