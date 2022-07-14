---
description: Samid Dastanbayev
---
# Insert so'rovi

PostreSQL da INSERT buyrug'i table'ga yangi qator qo'shish uchun ishlatiladi. Biz bir vaqtda bitta yoki bir nechta yangi qatorlar qiymatlarini qo'shishimiz mumkin.


## Sintaksis

Bitta qator qo'shish:
```sql
INSERT INTO table_name   
(column1,   
column2,   
column3, ……columnN)    
VALUES (value1, value2, value3, ….. valueN); 
```

Birdaniga bir nechta qator qo'shish:
```sql
INSERT INTO table_name  
(column1,
column2,
column3, ……columnN)
VALUES (value1, value2, value3, ….. valueN), (value1, value2, value3, ….. valueN), (value1, value2, value3, ….. valueN)...;
```

Bundan tashqari, boshqa bir table'dagi ma'lumotlarni tanlab olib qo'shishimiz ham mumkin. Uning sintaksisi quyidagicha:

![](https://user-images.githubusercontent.com/91861166/178907735-65944d88-2829-415e-b7e5-f9c13ac00f2d.png)

Yuqorida 2 ta 'users' va 'employees' table'lari yaratilib, 'users' table'ga 4 ta foydalanuvchi ism-familiyasi qo'shildi.
'employees' table'ga users table'dan malumotlarni tanlab olib, to'g'ridan-to'g'ri 'employees' table'ga INSERT INTO buyrug'i orqali qo'shib qo'yilyapti
va so'ngida 'employees' table'ni SELECT qilsak 'users' dan tanlab olgan ma'lumotlarning barchasi qo'shib qo'yilganini ko'rishimiz mumkin.

{% hint style="info" %}
  Note:
* Agar table'ning barcha ustunlariga qiymat kiritishimiz kerak bo'lsa, ustun nomlarini yozishimiz shart emas.
* Ma'lum tablening tanlangan ustunlariga qiymat berishimiz shart.
* Kiritilayotgan ma'lumot ustun tiplariga va cheklovlariga mos tushishligi kerak.
* Agar INSERT qilyotgan paytimizda table ustuni NULL qiymatni qabul qilmaydigan bo'lsa, o'sha ustunga ma'lumotni qo'shishimiz kerak bo'ladi.
* Agar ustun NULL qiymatni qabul qilsa, ustun uchun ma'lumotni e'tiborsiz qoldirishimiz mumkin.
{% endhint %}
