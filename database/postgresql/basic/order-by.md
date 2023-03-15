---
description: Axmadjonov Abdulloh
---

# Order By

Order by
Ma'lumotlarni boshlarishning muhim jihatlaridan biri ma'lum ustunlar yoki maydonlar asosida ma'lumotlarni saralash qobiliyatidir. PostgreSQL-dagi "ORDER BY" bandi foydalanuvchilarga ma'lumotlarni bir yoki bir nechta ustunlar asosida o'sish yoki kamayish tartibida saralash imkonini beruvchi foydali vositadir.
"ORDER BY" bandi "SELECT" operatorining natijalar to'plamini saralash uchun ishlatiladi. Argument sifatida bir yoki bir nechta ustunlarni oladi va natijalar to'plamini tartiblash tartibini belgilaydi.

**Sintaksis**:
```sql
SELECT ustun1, ustun2, ...
FROM jadval_nomi
ORDER BY ustun1 [ASC|DESC], ustun2 [ASC|DESC], ...;
```
"ORDER BY" bandi natijalar to'plamini o'sish tartibida tartiblaydi. Natijalar to'plamini kamayish tartibida saralash uchun ustun nomidan keyin "DESC" kalit so'zi ishlatiladi. Agar "ASC" yoki "DESC" ko'rsatilmagan bo'lsa, "ASC" qabul qilinadi.

Aytaylik sizda quyidagi jadval bor:

![](https://user-images.githubusercontent.com/91861166/225201331-560315c3-c02b-430b-81c1-a10e17d2de3b.png)

Sizga xodimlarni yoshi bo'yicha saralash kerak bo'lib qoldi, endi siz ORDER BY ni ishga solasiz. Quyida shu jadvalni yosh ustuni bo'yicha o'sish tartibida saralash kodi keltirilgan.
```sql
SELECT * FROM xodimlar
ORDER BY yosh;
```
Natija:

![](https://user-images.githubusercontent.com/91861166/225201387-999adf2d-27df-456a-89b8-d70edee51782.png)

Quyidagi kod esa tepada keltirilgan jadvalni birinchi darajada ismi bo'yicha keyin esa familiyasi bo'yicha saralash kodi:
```sql
SELECT * FROM xodimlar
ORDER BY ism, familiya;
```
Natija:

![](https://user-images.githubusercontent.com/91861166/225201446-6007b8b4-427a-4aee-87e2-d7cc805a16bf.png)
 
Xulosa qilib aytganda, "ORDER BY" bandi foydalanuvchilarga PostgreSQL-da ma'lum ustunlar yoki qiymatlar asosida ma'lumotlarni saralash imkonini beruvchi kuchli vositadir. Bu har qanday ma'lumotlarni boshqarish vazifasining muhim qismi bo'lib, ma'lumotlarni mazmunli tarzda tartibga solish va tushunish uchun foydalidir.
