---
description: (AIJavhar) Javohir Boyaliyev
---

# Update so'rovi

Demaaaaaaaaaaaaaaaaaaaak, Ma’lumotlar Bazasidagi ba’zi ma’lumotlarni o‘zgartirish uchun bizga UPDATE buyrug‘i yordam beradi.
Uning umimiy ko‘rinishi quyidagicha:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ... columnN = valueN
[WHERE update_condition] 
```

Deylik, bizda ilgari yaratilgan va ba‘zi ma‘lumotlar bilan to‘ldirilgan Products nomli jadvalimiz bor:

![](https://user-images.githubusercontent.com/91861166/223743724-2bbfc623-e022-45f2-ba7c-42e2a5031255.png)

Endi esa barcha mahsulotlarning narxini biroz qimmatlashtiramiz:
```sql
UPDATE Products
SET Price = Price + 3000; 
```
 
Shu payti :

![](https://user-images.githubusercontent.com/91861166/223743879-54d31280-3c34-4f0e-9ce6-390fffc6bc8c.png)


Natijada esa quyidagi ma’lumotlarni ko‘rishimiz mumkin:

![](https://user-images.githubusercontent.com/91861166/223743971-fe9325cd-dd45-4e6b-b8f9-2bf6b897f02d.png)

 
Ya’na biroz o‘zgartirish kiritamiz:
```sql
UPDATE Products
SET Price = Price + 2500;

SELECT * FROM Products; 
```

![](https://user-images.githubusercontent.com/91861166/223744571-ff6c68aa-87c4-4d61-8522-a53915d7d2e3.png)

 

Ko‘rinib turibdiki bunday holda, UPDATE barcha ma’lumotlar uchun amal qiladi. **WHERE** kalit so‘zidan foydalanib, siz shartli ravishda UPDATE qilinadigan ma’lumotni tanlab olishimiz mumkin - agar ma’lumot shartga mos kelsa, u UPDATE qilinadi. Misol uchun, Manufacturer nomini "Samsung" dan "Samsung Inc." ga o‘zgartiramiz:
```sql
UPDATE Products
SET Manufacturer = ‘Samsung Inc.’
WHERE Manufacturer = ‘Samsung’;

SELECT * FROM Products; 
```

![](https://user-images.githubusercontent.com/91861166/223746325-28738fc9-7f41-40bf-b84e-465a29767249.png)

 
Va shuningdek, bir nechta ma`lumotlarni ham UPDATE qilish imkoniyati mavjud:
```sql
UPDATE Products
SET Manufacturer = ‘Samsung’
        Product_Count = Product_Count + 3 	
WHERE Manufacturer = ‘Samsung Inc.’;

SELECT * FROM Products; 
```
![](https://user-images.githubusercontent.com/91861166/223746457-ec76e64a-5ed9-447b-97d2-cacfc5073f36.png)
