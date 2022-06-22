---
description: Samid Dastanbayev
---
# Select Database

Ushbu bo'limda bizda mavjud bo'lgan database'ga ulanish(tanlash) ni ko'rib chiqamiz.

PostgreSQL'da database'ga ulanishni 2 xil usuli mavjud:

* pgAdmin yordamida ulanish
* SQL terminali yordamida ulanish

#### Keling, birinchi pgAdmin orqali bizda mavjud bo'lgan database'ga ulanishni ko'rib chiqamiz:

![](https://user-images.githubusercontent.com/91861166/175083286-aad2f3e4-2c80-4636-909d-708ab25f3e88.png)


Yuqoridagi ketma-ketlikni bajarganingizdan so'ng, siz o'zingiz tanlagan database'ga ulanasiz.

Ulanishingiz bilan sizga yangi oyna paydo bo'ladi va bu yerda siz SQL querylarini yozishingiz mumkin.

![](https://user-images.githubusercontent.com/91861166/175083756-6aba18b6-6ef8-4071-80e0-98143a525979.png)

#### Endi esa ikkinchi yo'l, SQL terminali orqali database'ga ulanishni ko'rib chiqamiz:

SQL terminalini ochamiz va unga '\l' buyrug'ini kiritish orqali bizda mavjud database'lar ro'yxati ko'rishimiz mumkin:

![](https://user-images.githubusercontent.com/91861166/175084272-9b09d493-3212-43af-b52d-552066c3bc0b.png)

Database'ga ulanish uchun '\c' buyrug'idan foydalanamiz:

Quyida biz 'dotnetuz' database'ga ulanamiz.

postgres=# \c dotnetuz

![](https://user-images.githubusercontent.com/91861166/175084511-094d930b-afc1-45f6-998b-0182165410bb.png)
