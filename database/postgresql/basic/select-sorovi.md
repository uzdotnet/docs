---
description: (AIJavhar) Javohirbek Boyaliyev
---

# Select so'rovi

Ma'lumotlar ba'zasidan ma'lumotlarni olish uchun SELECT buyrug'idan foydalaniladi. Yozish sintaksisi quyidagicha:
```sql
SELECT column1, column2, columnN FROM table_name;
```
Deylik, bizda ilgari yaratilgan va ba'zi ma'lumotlar bilan to'ldirilgan Products nomli jadvalimiz bor:
 
![](https://user-images.githubusercontent.com/91861166/223290431-b58803cc-b05b-4033-bfe2-45a57faa0731.png)

Endi esa bu jadvaldagi barcha ma'lumotlarni qabul qilib olamiz, ya'ni ko'ramiz:
```sql
SELECT * FROM Products
```
 
Bu yerdagi “ * ” belgisi, bizga Products jadvalida mavjud bo'lgan barcha ustunlarni (columns) nazarda tutayotganligimizni bildiradi.
Natija: 

![](https://user-images.githubusercontent.com/91861166/223290566-c4d607e2-6b41-4718-90ac-2ab6d1ef4c55.png)

Ammo, lekin, biroq, * belgisini ishlatish har doim ham to'g'ri emas. Sababi, bizga har vaqt ham hamma ustunlar(column) kerak bo'lmaydi…
(Shu vaqtda yulduzcha belgisi:

![)](https://user-images.githubusercontent.com/91861166/223290659-a63f85b4-480d-4dc0-a5dc-620717e3b8fd.png)

Bu vaziyatda optimal yechim SELECT kalit so'zidan so'ng biz kerak deb bilgan ustunlar (column)ning nomini yozish hisoblanadi.
Demak bu quyidagicha tus oladi:

![](https://user-images.githubusercontent.com/91861166/223290761-306edb2c-8d5f-4fa8-a8be-3f67e867353f.png)

Biz SELECT qabul qilib olayotgan ma'lumotlarga ishlov berib olishning ham imkoni bor. Misol uchun deylik, biz mahsulot adadini (Product_Count), kim tomonidan ishlab chiqilganini (Manufacturer), shuningdek, umimiy mahsulotlar narxini bib olmoqchimiz. 
Bu quyidagicha ko'rinishga ega: 

![](https://user-images.githubusercontent.com/91861166/223290828-f94bb5a8-a050-49f6-9879-b7c56ad22033.png)
