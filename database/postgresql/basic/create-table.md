---
description: Sohib Jaynarov
---
# CREATE Table

PostgreSQL CREATE TABLE iborasi berilgan ma'lumotlar bazasining istalgan qismida yangi jadval yaratish uchun ishlatiladi.

Undan quyidagicha foydanalamiz.

```cmd
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( one or more columns )
);
```

CREATE TABLE — maʼlumotlar bazasi tizimiga yangi jadval yaratishni bildiruvchi kalit soʻz. Avval bo'sh jadval yaratib olinadi, keyin qavs ichida unga har xil ustunlar va ma'lumot turlari(data type) beriladi.

**Misol**

Misol uchun COMPANY degan jadval yarataylik va unda ID, NAME, AGE, ADDRESS va SALARY degan ustunlar bo'lsin. Birinchi o'rinda ustun nomlari, keyin qanday data typeligi, agar kerak bo'lsa "NOT NULL" ya'ni yaratilgan vaqti bo'sh qolishi mumkin emasligini anglatadi.

```cmd
CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL
);
```

Keling yana bir jadval yarataylik.

```cmd
CREATE TABLE DEPARTMENT(
   ID INT PRIMARY KEY      NOT NULL,
   DEPT           CHAR(50) NOT NULL,
   EMP_ID         INT      NOT NULL
);
```

Siz jadvallaringiz yaratilganligini bilish uchun \d buyrug'ini yozib, yaratilgan jadvallar ro'yxatini olishingiz mumkin.

```cmd
testdb-# \d
```

Buyruq quyidagi natijalarini beradi.

```cmd
          List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | company    | table | postgres
 public | department | table | postgres
(2 rows)
```

Agarda siz **\d tablename**dan foydalansansiz jadval haqidagi ma'lumotlarni olishingiz mumkin.

```cmd
testdb-# \d company
```

Quyidagi natija chiqdi.

```cmd
 Table "public.company"
  Column   |     Type      | Modifiers
-----------+---------------+-----------
 id        | integer       | not null
 name      | text          | not null
 age       | integer       | not null
 address   | character(50) |
 salary    | real          |
 join_date | date          |
Indexes:
    "company_pkey" PRIMARY KEY, btree (id)

```
