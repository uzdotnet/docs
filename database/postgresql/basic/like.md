---
description: Axmadjonov Abdulloh
---

# Like

Like
PostgreSQL - bu turli xil ma'lumotlar turlari va operatorlarini qo'llab-quvvatlaydigan kuchli ochiq manbali "relational" ma'lumotlar bazasini boshqarish tizimi. PostgreSQL-da eng ko'p ishlatiladigan operatorlardan biri "Like" operatori bo'lib, u namuna orqali solishtirish uchun ishlatiladi.

"Like" operatori PostgreSQL ma'lumotlar bazasidagi boshqa satr bilan satr namunasini solishtirish uchun ishlatiladi. Bu namuna mos keladimi yoki yo'qligini ko'rsatuvchi mantiqiy qiymatni (true yoki false) qaytaradi. PostgreSQL-da "Like" operatoridan foydalanish sintaksisi quyidagicha:
```sql
SELECT ustun_nomi
FROM jadval_nomi
WHERE ustun_nomi LIKE namuna;
```
Yuqoridagi sintaksisda "ustun_nomi" siz qidirmoqchi bo'lgan ustun nomini, "jadval_nomi" ustun joylashgan jadval nomini va "namuna" siz solishtirmoqchi bo'lgan qator namunasini ifodalaydi.

"Like" operatori namunani solishtirish uchun quyidagi maxsus belgilarni qo'llab-quvvatlaydi:
"%" - Nol yoki undan ortiq belgilarning istalgan ketma-ketligiga mos keladi.
"`_`" - Har qanday bitta belgiga mos keladi.

Aytaylik bizda quyidagi jadval bor:

![](https://user-images.githubusercontent.com/91861166/225200555-7accad64-2054-4b3c-bf87-f109194b00e2.png)

Jadvaldagi familiyasi "ov" bilan tugaydigan xodimlarni olish uchun quyidagi kod yoziladi:
```sql
SELECT * FROM xodimlar
WHERE familiya LIKE '%ov';
```
Natija:

![](https://user-images.githubusercontent.com/91861166/225200625-e119d9db-fd7c-4279-af66-4d3048070fe4.png)

Quyidagi kod esa familiyasi "A" bilan boshlanib 4-harfi ham "a" bo'lgan xodimlarni qaytaradi:
```sql
SELECT * FROM xodimlar
WHERE familiya LIKE 'A__a%';
```
Natija:

![](https://user-images.githubusercontent.com/91861166/225200835-09d28743-6e0d-4bda-8bc9-73a1d808c49d.png)

Xulosa qilib aytadigan bo'lsak, PostgreSQL-dagi "Like" operatori satrlarni namuna orqali solishtirish uchun kuchli vositadir. Maxsus belgilar va sintaksisni tushunib, PostgreSQL ma'lumotlar bazasida aniq ma'lumotlarni osongina qidirishingiz mumkin.
