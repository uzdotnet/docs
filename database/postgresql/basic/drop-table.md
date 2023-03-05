---
description: Yo'ldoshxo'jayev Saidnabi
---

# Drop Table

PostgreSQL DROP TABLE buyrug'i berilgan ma'lumotlar bazasining istalgan jadvalini o’chirish uchun ishlatiladi. Bundan ehtiyot bo’lib foydalanish kerak, chunki o’chirilgan TABLE ni qayta tiklab bo’lmaydi.

Bu buyruq oddiy yoziladi va hech qanday qiyinchilik tug’dirmaydi. Faqat o’sha nomdagi TABLE bo’lsa bo’ldi, ketooradi  .

Syntax : 
```
DROP TABLE table_nomi ;
```

Buni ishlatish quyidagicha :

Biz oldin TABLE larni ro’yxatini ko’rib chiqamiz. Buning uchun `testdb-# \d` yozsak barcha table larni ko’rsatadi:

 Schema |    Name    | Type  |  Owner
------- | -----------|-------|------
 public | students   | table | postgres
 public | teachers | table | postgres
 public | drivers | table | postgres

(3 rows)


Ko'rib turganingizdek, bizda 3 ta TABLE chiqdi. Ulardan bizga kerak bo'lmagan ixtiyoriy TABLE ni o’chirib yuborishimiz mumkin. Keling, drivers TABLE  ni o’chiramiz:
```sql
DROP TABLE drivers;
```
Ushbu buyruq bajarilgandan keyin drivers Table ichidagi barcha ma'lumotlari bilan birga butunlay o'chib ketadi.

Buyruq to'g'ri bajarilganini tekshirib ko'rish uchun yana `testdb-# \d` yozsak barcha table larni ko’rsatadi 

Schema |    Name    | Type  |  Owner
--------|------------|-------|----------
 public | students    | table | postgres
 public | teachers | table | postgres 
 
(2 rows)

Endi bu yerda “drivers” table mavjud emas.
