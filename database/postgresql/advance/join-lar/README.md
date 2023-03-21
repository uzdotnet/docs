---
description: Muzaffar Nurillayev
---

# Join lar

JOIN'lar nima uchun kerak?

Relational database'larda ma'lumotlar jadvallarda saqlanadi. Ushbu jadvallarning har bir ustuni uchun aynan bitta tur belgilanadi va faqat o'sha turdagi ma'lumot saqlay olamiz. Lekin dasturlash tillarida bo'lgani kabi o'zimizning tipimizni yarata olmaymiz. Shunaqa paytlarda o'zaro bog'liq bo'lgan tipdagi ma'lumotlar boshqa boshqa jadvallarda saqlanadi va bunaqa paytda ularning o'zaro umumiy bo'lgan ustunlari orqali bog'liqlik yarata olamiz.

Misol uchun, bizda Order degan class'imiz bo'lsin va u Payment va OrderItem turlaridagi ma'lumotlarini o'z ichida saqlaydi. Lekin biz Order'larni saqlaydigan jadvalimizga to'g'ridan-to'g'ri Payment va OrderItem kabi murakkab turlarni ustunlarda saqlay olmaymiz. Ular uchun alohida jadval ochib ularning ma'lum bir ustuni bo'yicha bog'liqlik hosil qilamiz.

Keyinchalik bu jadvallarning hammasini ishtirok ettirib qanaqadir amal bajarmoqchi bo'lsak ularni unikal bitta jadvalga jamlash kerak bo'ladi. Aynan shunaqa vaziyatlarda, ya'ni bitta so'rov orqali bir nechta jadvallardan ma'lumot olish, ularni jamlab qanaqadir statistika yaratish uchun JOIN'lar kerak bo'ladi.

JOIN turlari.
PostgresSQLda 5 xil join turlari bor:

* CROSS JOIN.
* INNER JOIN.
* LEFT JOIN.
* RIGHT JOIN.
* FULL JOIN.
Har bir JOIN turi bo'yicha quyida amaliy misollarda o'rganishingiz mumkin.
