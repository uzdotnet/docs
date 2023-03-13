---
description: Axmadjonov Abdulloh
---

# Ma'lumot turlari

PostgreSQL - bu turli xil ma'lumotlar turlarini qo'llab-quvvatlaydigan kuchli "relational" ma'lumotlar bazasini boshqarish tizimi. Ma'lumotlar turlarini tushunish samarali ma'lumotlar bazasi tuzilmalarini loyihalash va ma'lumotlarni aniq saqlash va qidirishni ta'minlash uchun zarurdir.

PostgreSQL ma'lumotlar turlarining boy to'plamini taqdim etadi, jumladan:
* Raqamli ma'lumot turlari: Bu ma'lumot turlari raqamli qiymatlarni saqlash uchun ishlatiladi. Masalan, "integer", "float" va "numeric".
* Belgili ma'lumot turlari: Bu ma'lumot turlari belgilar ma'lumotlarini saqlash uchun ishlatiladi. Masalan, "character", "text" va "varchar".
* Sana va vaqt ma'lumot turlari: Bu ma'lumot turlari sana va vaqt qiymatlarini saqlash uchun ishlatiladi. Misollar "date", "time" va "timespan" o'z ichiga oladi.
* Mantiqiy ma'lumot turi: Bu ma'lumotlar turi true/false qiymatlarni saqlash uchun ishlatiladi.
* Massiv ma'lumot turlari: Bu ma'lumot turlari massivlarini yoki qiymatlar ro'yxatini saqlash uchun ishlatiladi. Masalan, integer[], text[] va numeric[].
* Kompozit ma'lumot turlari: Bu ma'lumot turlari bir-biriga bog'liq maydonlarni bitta tuzilishga guruhlash uchun ishlatiladi. 
* Tarmoq manzili ma'lumot turlari: Ushbu ma'lumot turlari IP manzillari va MAC manzillari kabi tarmoq manzillarini saqlash uchun ishlatiladi. Masalan, "inet" va "macaddr".
* Geometrik ma'lumot turlari: Ushbu ma'lumot turlari nuqtalar, chiziqlar va ko'pburchaklar kabi geometrik shakllarni saqlash uchun ishlatiladi. Masalan, "point" va "polygon".
* JSON ma'lumot turi: Ushbu ma'lumot turi JSON (JavaScript Object Notation) ma'lumotlarini saqlash uchun ishlatiladi.

PostgreSQL-da ustunning ma'lumotlar turini belgilash uchun jadval yaratishda tegishli ma'lumotlar turi kalit so'zidan foydalanishingiz mumkin. Masalan:
```sql
CREATE TABLE ishchilar (
  id integer,
  ism text,
  familiya text,
  ishga_kirgan_sana date
);
```
Ushbu misolda biz har biri turli xil ma'lumotlar turiga ega bo'lgan to'rtta ustunli "ishchilar" deb nomlangan jadval yaratmoqdamiz. "id" ustuni butun sonli ma'lumotlar turi, "ism" va "familiya" ustunlari matnli ma'lumotlar turlari va "ishga_kirgan_sana" ustuni "date" ma'lumot turidir.

Mavjud ma'lumot turlaridan tashqari, PostgreSQL foydalanuvchilarga "CREATE TYPE" operatoridan foydalangan holda maxsus ma'lumot turlarini yaratishga ham imkon beradi. 
Quyida "CREATE TYPE" uchun misol keltirilgan:
```sql
CREATE TYPE user_info AS (
  id integer,
  ism text,
  familiya text,
  ishga_kirgan_sana date
);
```
Xulosa qilib aytganda, ma'lumot turlari PostgreSQLning muhim jihati bo'lib, ustunda saqlanishi mumkin bo'lgan ma'lumot formati va hajmini aniqlash uchun ishlatiladi. PostgreSQL turli xil ma'lumotlarni saqlash va qidirish ehtiyojlarini qo'llab-quvvatlash uchun o'rnatilgan ma'lumot turlarining keng doirasini, shuningdek, o'zimiz yaratgan ma'lumot turlarini yaratish qobiliyatini ta'minlaydi. 
