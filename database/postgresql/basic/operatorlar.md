---
description: Axmadjonov Abdulloh
---

# Operatorlar

PostgreSQL-da operatorlar ma'lumotlar qiymatlari ustida turli xil operatsiyalarni bajarish uchun ishlatiladigan maxsus belgilar yoki kalit so'zlardir. Bu operatsiyalar matematik amallar, mantiqiy amallar, taqqoslash operatsiyalari va boshqalarni o'z ichiga olishi mumkin.

Operatorlar SQL so'rovlarining muhim qismi bo'lib, ko'pincha ma'lumotlarni turli usullar bilan filtrlash yoki boshqarish uchun ishlatiladi. Ular SELECT, INSERT, UPDATE va DELETE kabi boshqa SQL iboralari bilan birgalikda ishlatilishi mumkin.

PostgreSQL juda ko'p operatorlarni qo'llab-quvvatlaydi, jumladan:

### Arifmetik operatorlar: Bu operatorlar qoʻshish (+), ayirish (-), koʻpaytirish (`*`), boʻlish (/) va modul (%) kabi asosiy arifmetik amallarni bajarish uchun ishlatiladi.
Misol:
```sql
SELECT 5 + 3; -- Natija: 8
SELECT 7 * 4; -- Natija: 28
```
### Taqqoslash operatorlari:  Bu operatorlar ikkita qiymatni solishtirish va mantiqiy (true/false) qiymatni qaytarish uchun ishlatiladi. Masalan, teng (=), teng emas (<> yoki !=), katta (>), kichik (<), katta yoki teng (>=) va kichik yoki teng (<=).
Misol:
```sql
SELECT * FROM ishchilar WHERE oylik > 5000000;
```
Ushbu misolda ">" operatori ish haqi 5000000 dan ortiq bo'lgan ishchilar jadvalidagi barcha qatorlarni olish uchun ishlatiladi.

### Mantiqiy operatorlar: Bu operatorlar bir nechta mantiqiy ifodalarni birlashtirish va mantiqiy qiymatni qaytarish uchun ishlatiladi. Misollar: AND, OR, va NOT.
Misol:
```sql
SELECT * FROM ishchilar WHERE oylik > 5000000 AND idora = 'Sotuvlar';
```
Ushbu misolda "AND" operatori ish haqi 5000000 dan yuqori bo'lgan va idorasi "Sotuvlar" bo'lgan xodimlar jadvalidan barcha qatorlarni olish uchun ishlatiladi.

### Bit yo'nalishi bo'yicha operatorlar: Bu operatorlar bit yo'nalishi bo'yicha AND (&), bit yo'nalishi bo'yicha OR (|) va bit yo'nalishi bo'yicha NOT (~) kabi ikkilik ma'lumotlarda bit bo'yicha operatsiyalarni bajarish uchun ishlatiladi.
Misol:
```sql
SELECT 8 & 3; -- Natija: 0 
SELECT 8 | 3; -- Natija: 11
```
Ushbu misolda "&" operatori 8 (1000) va 3 (0011) ning ikkilik qiymatlari o'rtasida bit bo'yicha AND operatsiyasini bajaradi, natijada 0000 (o'nlik kasrda 0) qiymati paydo bo'ladi.

### String operatorlari: Bu operatorlar qator qiymatlari ustida amallarni bajarish uchun ishlatiladi, masalan, birlashtirish (||) va pastki qatorni ajratib olish.
Misol:
```sql
SELECT 'Hello' || ' ' || 'World'; -- Natija: "Hello World"    
SELECT SUBSTRING('Hello World', 1, 5); -- Natija: "Hello"
```


PostgreSQL mavjud operatorlardan tashqari boshqa opetaror yaratish imkoniyatini beradi. Maxsus operatorlarni CREATE OPERATOR yordamida yaratish mumkin.

Xulosa qilib aytganda, PostgreSQL ma'lumotlar qiymatlari ustida turli operatsiyalarni bajarish uchun ishlatilishi mumkin bo'lgan keng ko'lamli operatorlarni taqdim etadi. Ushbu operatorlarni tushunish ma'lumotlarni samarali qabul qiluvchi, boshqaradigan va filtrlaydigan SQL so'rovlarini yaratish uchun juda muhimdir.
