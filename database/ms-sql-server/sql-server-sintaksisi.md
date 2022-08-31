---
description: Jahongir Temirov
---

# SQL Server sintaksisi


SQL ni UPPER-CASE da yozgan ma'qul.

{% hint style="info" %}
SQL katta-kichik harflarga sezgir emas. SELECT va select keywordlari bir ma'noni beradi
{% endhint %}


### Comments
**Single-line**:  2 ta tire qo'yilgan joydan o'ng tomoni qator oxirigacha comment

**Multi-line** — `/*    */` orasida joylashgan barchasi comment

![Comment](https://user-images.githubusercontent.com/91861166/187704231-9d999b9c-bb9e-4024-8c83-ecfc0299da4e.png)

### SQL Sub Languages
SQL turli imkoniyatlarni ta'minlaydigan ko'plab pastki tillardan iborat. SQL ning pastki tillari tomonidan taqdim etiladigan imkoniyatlar - bu yaratish, ma'lumotlarni manipulyatsiya qilish, so'rovlar va ularni boshqarish

![Sub languages](https://user-images.githubusercontent.com/91861166/187704339-6a8f9ca4-31e3-475a-b95a-45bc1f4c8ed2.png)

* DDL - Data Definition Language
* DML - Data Manipulation Language
* DQL/DRL  - Data Query/Retrieval Language
* TCL - Transaction Control Language
* DCL - Data Control Language

## Database bilan ishlash
{% hint style="info" %}
SQL Serverda db nomi Unique (yagona)  bo'lishi, maksimum 128 belgi bo'lishi lozim.
{% endhint %}
DB xosil qilishni 2 xil yo'li mavjud. UI va Query. Faqat Queryni yozaman.


### CREATE DATABASE
```sql
CREATE DATABASE <Database_name>

CREATE DATABASE Student;
```

Yangi database(keyingi o'rinlarda db) bilan 2 file ham hosil bo'ladi.

`*.mdf` — master data file. Asosiy ma'lumotlar, jadvallar ushbu fileda saqlanadi.

`*.ldf` — log data file. Querylar tarixi(dbni tiklash uchun) ushbu fileda.


### ALTER DATABASE
```sql
ALTER DATABASE <Databse_name>              
MODIFY NAME = <New Name>

ALTER DATABASE Student
MODIFY NAME = Students;
```
ALTER orqali db nomini, sozlamalarini, file nomi va joylashuvini va boshqalarni o'zgartirishimiz mumkin.

File nomi:
```sql
Alter DATABASE Edu_TSQL_Alter;
MODIFY FILE ( NAME = Edu_TSQL, NEWNAME = Edu_TSQL_newName );
```

File joylashuv:
```sql
Alter DATABASE Edu_TSQL_Alter;
MODIFY FILE ( NAME = Edu_TSQL_NewName, FILENAME = N"C:\Program Files\Microsoft SQL Server\MSSQL14.SQL_MS\MSSQL\DATA\New_File\Edu_TSQL_log.ldf" );
```

### DROP DATABASE
```sql
DROP DATABASE <Databse_name>

DROP DATABASE Students;
```

Shu bilan db olib tashlanadi.


### BACKUP DATABASE
```sql
BACKUP DATABASE <Databse_name>
TO DISK = 'filePath';

BACKUP DATABASE Students
TO DISK = 'J:\Databases\';
```

SQL ma'lumotlar bazasining to'liq zaxira nusxasini yaratish uchun ishlatiladi
```sql
BACKUP DATABASE <Databse_name>
TO DISK = 'filePath'
WITH DIFFERENTIAL;
```
Differensial zahira nusxasi faqat oxirgi to'liq ma'lumotlar bazasi zahira nusxasidan keyin o'zgargan ma'lumotlar bazasi qismlarini zaxiralaydi.


### RESTORE DATABASE
```sql
RESTORE DATABASE <Databse_name>
FROM DISK = 'filePath + fileName';

RESTORE DATABASE Students
FROM DISK ='J:\Databases\Students.bak';
```
Zaxiraga olingan db ni yuklash



## Table bilan ishlash
{% hint style="info" %}
Jadval(Table) - bu ma'lumotlarni satr va ustun formatida saqlaydigan ob'ekt 
{% endhint %}

Jadvalni quyidagi usullar bilan yaratishimiz mumkin:

1. Query: Barcha ustunlar va uning ma'lumotlar turini belgilash orqali yangi jadval yarating.
2. Query: Mavjud jadval yordamida yangi jadval yaratish
3. Jadval dizayneridan foydalanish

### CREATE TABLE
```sql
CREATE TABLE tableName
( 
  column_1 datatype [ NULL | NOT NULL ],
  column_2 datatype [ NULL | NOT NULL ],
  ...
);

CREATE TABLE Student
(
    Id INT NOT NULL,
    Name VARCHAR(30) NOT NULL,
    Address TEXT,
    Email TEXT
);
```
CREATE TABLE nomi (ustun_nomi ma'lumot_turi null_yoki_null_emasligi);

NOT NULL yoki NULL ni belgilamasa default NULL olinadi.

Jadval nomi, column nomi Unique bo'lishi lozim. Nomi _ dan boshqa belgi va raqamlardan boshlanmasligi lozim. Iloji boricha space(" ")dan foydalanmang. O'rniga _ dan foydalaning. Nomi kamida 1 belgi, max 128 belgi, ustunlar soni 1 dan 1024 gacha bo'lishi lozim.


```sql
SELECT (Column 1, …) INTO <New Table name> FROM <Old Table name>;
SELECT (Id,Email) INTO Emails FROM Student;
```
Mavjud table dan yangi table ochish.



### ALTER TABLE
```sql
ALTER TABLE tableName ADD column_1 datatype, column_1 datatype;

ALTER TABLE Students ADD Age INT;
```
ALTER TABLE bilan column nomini, o'lchamini, datatype ini o'zgartirish,  null yoki not null ni belgilash, yangi column qo'shish, olib tashlash, cheklovlar qo'shish, olib tashlash mumkin.


```sql
ALTER TABLE tableName ALTER COLUMN column_1 datatype NOT NULL or NULL;

ALTER TABLE Students ALTER COLUMN Address VARCHAR(100) NOT NULL;
```
Address column NULL dan NOT NULL ga o'zgardi.


```sql
ALTER TABLE tableName ALTER COLUMN column_1 datatype;

ALTER TABLE Students ALTER COLUMN Address VARCHAR(100);
```
Columnni size va typeni o'zgartirish. Sizeni o'zgartirganda mavjud datalarni eng kam belgi borini oladi.
Masalan: "Tashkent, Amir Temur Street 108" da 31 dan kam qila olmaysiz.


```sql
EXEC sp_rename 'Table.Column', 'newName';

EXEC sp_rename 'Customers.ID', 'CustomerID';
```
Column nomini o'zgartirish. sp_rename saqlangan protsedura hisoblanadi.


```sql
ALTER TABLE tableName DROP COLUMN column_1;

ALTER TABLE Students DROP COLUMN Address;
```
Ustunni olib tashlash



### DROP/TRUNCATE TABLE
```sql
DROP TABLE <tableName>;
DROP TABLE Students

TRUNCATE TABLE <tableName>;
TRUNCATE TABLE Students
```
DROP jadvalni o'chiradi. TRUNCATE esa jadvaldagi ma'lumotlarni tozalaydi.
