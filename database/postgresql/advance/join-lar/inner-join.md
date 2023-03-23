---
description: Muzaffar Nurillayev
---

# Inner join

Tasavvur qilaylik bizning platformamiz fanlardan olimpiadalarga ro'yxatdan o'tadigan joy. Har bir o'quvchi bir nechta fanlardan ro'yxatdan o'ta oladi va har bir fan uchun topshirgan o'quvchilar ma'lumoti alohida jadvallarda saqlanadi. Endi bizning oldimizda qaysi o'quvchilar matematikadan ham, ona tilidan ham ro'yxatdan o'tgan, qaysilari boshqa ikkita fandan, qaysilari uchtadan ro'yxatdan o'tganini chiqarib berish kerak degan vazifa turibdi.

Bunaqa paytlarda INNER JOIN ishlatamiz. Bu Join vazifasi bir nechta jadvallar orasida umumiy qiymatlarni olib berishdir.

![](https://user-images.githubusercontent.com/91861166/227073378-26736fab-4114-4eb2-b94e-c8b4c5a4529c.png)

Masalan bizda Matematika, InglizTili, Informatika fanlardan qatnashadigan table'lar bo'lsa hammasida o'quvchi ma'lumotlari (Ism, Username, Sinfi, TugilganYili).

Matematika va ingliz tilidan ham qatnashadigan o'quvchilar:
```sql
SELECT * FROM Matematika
INNER JOIN InglizTili
ON Matematika.Username = InglizTili.UserName;
```

Matematika va Informatikadan ham qatnashadigan o'quvchilar:
```sql
SELECT * FROM Matematika
INNER JOIN Informatika
ON Matematika.Username = Informatika.UserName;
```

Uchchovidan ham qatnashadigan o'quvchilar:
```sql
SELECT * FROM Matematika
INNER JOIN Informatika
ON Matematika.Username = Informatika.UserName
INNER JOIN InglizTili
ON Matematika.Username = InglizTili.Username;
```
