---
description: (AIJavhar) Javohir Boyaliyev
---

# Limit

Endi esa LIMIT operatori haqida gaplashamiz.
LIMIT bizga biz so‘ragan miqdordagi ma’lumotlarni bizga taqdim qilish uchun ishlatiladi.
Deylik, bizda ilgari yaratilgan va ba‘zi ma‘lumotlar bilan to‘ldirilgan Products nomli jadvalimiz bor:

![](https://user-images.githubusercontent.com/91861166/223748351-438749f2-597b-4ed3-98d0-71ab0c6cdc11.png)

Endi esa biz jadvalimizda mavjud bo‘lgan hamma ma’lumotlarni emas, istaganimizchanisinni chiqarishni harakat qilib ko‘ramiz. Bunda bizga LIMIT yordamga keladi :)
Bizda mavjud bo‘lgan ma’lumotlarning ro‘yxat boshidan 3 ta donasini chiqarishni istadik:
```sql
SELECT * FROM Products
ORDER BY ProductName
LIMIT 3; 
```  
![](https://user-images.githubusercontent.com/91861166/223748653-8016045c-5c45-469f-99a3-c786314764a9.png)
 
Endi masalaga boshqacha yondashib ko‘rsak. Bizga ro‘yxat boshidan emas aniq bir pozitsiyasidan keyin bir qancha ma’lumotlar kerak bo‘lib qoldi desak. Bu yo‘sinda masalaning yechimi **OFFSET** operatori hisoblanadi.

{% hint style="info" %}
**OFFSET** – qaysi o‘rindan boshlab SELECT qilishni ko‘rsatish uchun foydalaniladi!  (yoki LIMIT)
{% endhint %} 

Demak, ro‘yxatimizning birorta o‘rnidan boshlab biz so‘raganchalik ma’lumotlarni chiqarishni ko‘ramiz: 
```sql
SELECT * FROM Products
LIMIT 3 OFFSET 2;
```

![](https://user-images.githubusercontent.com/91861166/223748804-dff460dc-1930-47f4-8bd6-495e1cd70f66.png)

Agar bizga ma’lum miqdordagi ma’lumotlar emas, balki o‘sha o‘rindan boshlab ro‘yxat oxirigacham ma’lumotlar kerak bo‘lsa, u holda:
```sql
SELECT * FROM Products
ORDER BY ProductName
OFFSET 2; 
```
Yoki, LIMIT dan keyin ALL kalit so‘zi yozish orqali amalga oshadi:
```sql
SELECT * FROM Products
ORDER BY ProductName
LIMIT ALL OFFSET 2; 
```
![](https://user-images.githubusercontent.com/91861166/223748933-d52c7576-036b-4d50-9b52-ee5110b1b8c0.png)
