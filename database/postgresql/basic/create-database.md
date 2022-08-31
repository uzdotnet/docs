---
description: Sohib Jaynarov
---
# CREATE Database

Ma'lumotlar bazasi bilan ishlaganda har doim birinchi qilinadigan ish bu ma'lumotlar bazasini yaratishdir. Hozir biz PostgerSqlda yangi ma'lumotlar bazasini yaratishni o'rganamiz, demak uning ikki xil usuli bor ekan.

1. CREATE DATABASE, SQL buyrug'idan foydalanish.
2. createdb buyrug'idan foydalanish.

## CREATE DATABASEdan foydalanish

**CREATE DATABASE** burug'i yordamida **cmd**(terminal)da ma'lumotlar bazasini yaratamiz.

Buni quyidagicha ishlatamiz:
```cmd
CREATE DATABASE dbname;
```

bu yerda **dbname** ma'lumotlar bazasining nomi.

## createdb'dan foydanish

**createdb**ning **CREATE DATABASE**dan farqi shundaki, u bilan bitta command-line'ning o'zida unga ***description*** ya'ni izoh berib ketish mumkin.

**createdb**ning ishlatilishi quyidagicha.

```cmd
createdb [option...] [dbname [description]]
```

**Parametrlari**

Quyidagi jadvalda parametrlari va ularga izoh berilgan.

1. **dbname** - Yaratilgan ma'lumotlar baza nomi 

2. **description** - Yaratilgan ma'lumotlar bazasiga izoh 

3. **options** - "createdb" qabul qiladigan buyruq qatori argumentlari

**Buyruqlar**

Quyida "createdb" qabul qiladigan buyruq qatori argumentlari ko'rsatilgan.

1. **-D tablespace** - Ma'lumotlar bazasi uchun standart jadval maydonini belgilaydi.

2. **-e** - "createdb" yaratadigan va serverga yuboradigan buyruqlarni aks ettiradi.

3. **-E encoding** - Ushbu ma'lumotlar bazasida ishlatiladigan belgilarni kodlash sxemasini belgilaydi.

4. **-l locale** - Ushbu ma'lumotlar bazasida ishlatiladigan locale'ni belgilaydi.

5. **-T template** - Ushbu ma'lumotlar bazasini yaratish uchun shablon ma'lumotlar bazasini yaratadi.

6. **--help** - Createb buyruq qatori argumentlari haqida yordamni ko'rsatadi.

7. **-h host** - Server ishlayotgan host nomini belgilaydi.

8. **-p port** - Server ulanishlarni tinglayotgan TCP portini yoki local Unix domen socket file kengaytmasini belgilaydi.

9. **-U username** - Connect qilish ya'ni ulash uchun foydalanuvchi nomi.

10. **-w** - Hech qachon parol so'rovini bermang.

11. **-W** - Ma'lumotlar bazasiga ulanishdan oldin createdb'ni parol so'rashga majburlash.

cmd'ni oching. PostgresSQL o'rnatilgan papkagani o'ching va undagi Bin papkasiga kirib, ma'lumotlar bazasini yaratish uchun quyidagi buyruqni yozing,

```cmd
createdb -h localhost -p 5432 -U postgres testdb
```

Yuqoridagini bajarganingizdan so'ng parol so'raydi va o'zingiz uchun istalgan parolni kiritib ma'lumotlar bazasini yaratishda davom eting.
Yaratib bo'lganingizdan keyin uni yaratilganligini tekshirish uchun yaratilgan ma'lumotlar bazasining ro'yxatini ko'rish uchun **\l** buyrug'rini yozing.

Quyidagiga o'xshash natija chiqishi lozim.

```cmd
postgres-# \l
                             List of databases
   Name    |  Owner   | Encoding | Collate | Ctype |   Access privileges   
-----------+----------+----------+---------+-------+-----------------------
 postgres  | postgres | UTF8     | C       | C     | 
 template0 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 template1 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 testdb    | postgres | UTF8     | C       | C     | 
(4 rows)

postgres-# 
```
