# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;

ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);

```

**Output:**
<img width="1220" height="477" alt="image" src="https://github.com/user-attachments/assets/52ee40b9-6cc3-41b9-8b9e-43d5cdf08033" />



**Question 2**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```sql
CREATE TABLE Orders(
    OrderID  INTEGER,
    OrderDate  TEXT,
    CustomerID  INTEGER
);

```

**Output:**

<img width="1224" height="460" alt="image" src="https://github.com/user-attachments/assets/179a4a7c-2e03-46c3-a095-40aad1c760e2" />


**Question 3**
---
Write a SQL query to Add a new column Country as text in the Student_details table.

```sql
ALTER TABLE  Student_details
ADD COLUMN Country TEXT;
```

**Output:**
<img width="1225" height="448" alt="image" src="https://github.com/user-attachments/assets/2a229650-620e-4080-b408-5d44cbeecf1b" />


**Question 4**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO  Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES (201,'David Lee','M','Physics',92);
```

**Output:**

<img width="1219" height="330" alt="image" src="https://github.com/user-attachments/assets/7c2c2185-50f7-4b94-88a8-7cf62cac2cd2" />


**Question 5**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
-CREATE TABLE item(
    item_id TEXT primary key,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHAR (4),
    FOREIGN KEY (icom_id) REFERENCES company (com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
);
```

**Output:**
<img width="1221" height="441" alt="image" src="https://github.com/user-attachments/assets/e64ee9b3-f49d-4d56-a9f5-cf7b391614bb" />


**Question 6**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
```sql
INSERT INTO Customers
SELECT CustomerID, Name, Address, Email FROM Old_customers;
```

**Output:**

<img width="1207" height="381" alt="image" src="https://github.com/user-attachments/assets/bccccaa4-63bc-434f-b422-2a56acd6b9c7" />


**Question 7**
---

Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300



```sql
INSERT INTO Products (Name    ,    Category  ,   Price   ,    Stock)
VALUES('Smartphone','Electronics',800,150),
    ('Headphones','Accessories',200,300);

```

**Output:**


<img width="1222" height="447" alt="image" src="https://github.com/user-attachments/assets/27648488-2b83-4cbd-a4b7-6188810ad6a2" />


**Question 8**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
CREATE TABLE Products(
    ProductID primary key,
    ProductName NOT NULL,
    Price REAL CHECK(Price>0),
    Stock INT CHECK(Stock>=0)
);
```

**Output:**


<img width="1225" height="379" alt="image" src="https://github.com/user-attachments/assets/d9fe3682-bc16-444a-b37a-ce41f2176644" />


**Question 9**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
```sql
CREATE TABLE Invoices(
InvoiceID  INTEGER primary key,
InvoiceDate DATE,
DueDate DATE CHECK(Duedate>= InvoiceDate),
Amount REAL CHECK(Amount>0)
);
```

**Output:**

<img width="1218" height="365" alt="image" src="https://github.com/user-attachments/assets/631d90e3-b557-4a9f-9b99-a09a99f451ca" />


**Question 10**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```sql
CREATE TABLE Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES  Orders(OrderID)
);
```

**Output:**


<img width="1224" height="328" alt="image" src="https://github.com/user-attachments/assets/bbc77b48-8a8f-4e7a-872a-ddc4cf54724d" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
