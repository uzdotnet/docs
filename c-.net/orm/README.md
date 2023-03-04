---
description: Muzaffar Nurillayev
---

# ORM nima?

Bu mavzuni o'qiyotgan bo'lsangiz katta ehtimol bilan database bilan ishlashda muhim ko'nikmalarga egasiz.

Yangi texnologiyaning qadrini tushunish uchun undan noqulay, effektivligi past, konsepsiyasi boshqacha texnologiyalardan foydalanib ko'rish kerak. Bunga bir qancha tendensiyalarni keltirib o'tish mumkin. Misol uchun Obyektga yo'naltirilgan dasturlash konsepsiyasining muhumliligini tushunish va qadriga yetish uchun Funksional dasturlash konsepsiyasini tushunib olish kerak yoki aksincha.

Yaratilyotgan dastur ma'lumotlarni bir nechta formatlardan foydalanadigan manbalardan olishi mumkin. Bunga misol qilib CSV, JSON formatlari va turli databaselarni misol keltirish mumkin.

Birinchi 2 ta texnikaning ishlash prinsipi faylga ma'lumotni ma'lum formatda yozish va o'qib olish edi. Lekin, o'qib olayotgan paytda dasturimiz uchun yozilgan ma'lumot biz kutgandek to'g'ridan-to'g'ri tushunarli emas. Endilikda bizning vazifamiz yozilgan ma'lumotni o'zimiz ishlayotgan platforma tushunadigan ma'lumot turiga aylantirishdir.

Ya'ni biz bu paytda ma'lum qoida asosida ma'lumotlarni obyektlarga aylantiradigan (convert) logika yozishimiz yoki shu logikani bajaradigan package o'rnatishimiz kerak (misol: Json serializer & deserializer). Bu narsani ma'lumot saqlaydigan manbamiz va dasturimiz orasidagi ko'prik desak bo'ladi.



Endi asosiy mavzuga qaytadigan bo'lsak ORM (OBJECT RELATIONAL MAPPING) bu OOP tillari va RELATIONAL database'lar orasidagi ana shunday ko'prikni bajaradigan, ikkovini ulab beradigan texnika.

                                            .NET ---> ORM ---> Database

                                            .NET <--- ORM <--- Database

OOP tillaridan foydalangan holda database bilan ishlashda biz undan ma'lumotlarni yaratish, o'qish, yangilash va o'chirish (CRUD) kabi turli xil vazifalarni bajarishimiz kerak bo'ladi. O'zi aslida, bu narsalarni bajarish uchun SQL'dan foydalanishimiz kerak edi va SQL shu uchun ham yaratilgan. Lekin development paytida fokus ikkiga bo'linmasligi uchun ishimizni osonlashtirib berish uchun ORM turli qulayliklarni bizga taqdim etadi. Endilikda qiynalib SQL so'rovlari orqali ma'lumot ustida amal bajarishdan ko'ra xuddi shu so'rovlarning vazifasini bajaradigan lekin bizga sintaksisi qulay bo'lgan metodlardan foydalanishimiz mumkin.



.NET ekosistemasida bir qancha ORM texnologiyalari mavjud. Ulardan mashhurlarini quyida bilib olasiz:

* Entity Framework;
* NHibernate; 
* Dapper;
* BFC

Bulardan tashqari boshqa texnologiyalar ham mavjud va bulardan aynan bittasini kuchli deyish noto'g'ri, chunki texnologiyalar project'ga qulay qilib tanlanadi va har xil project uchun har xil texnologiya mos kelishi mumkin.


ORMning foydali tomonlari:

* Dasturning development vaqtini qisqartiradi;
* Database bilan ishlashdagi mantiqni boshqarishni osonlashtiradi;
* Kamroq va osonroq kod orqali ish bitadi;


ORMning kamchiliklari:
* SQLdan ko'ra sekinroq;
* Kattaroq va murakkabroq so'rovlar bilan ishlashda kamchiliklari seziladi;

Ma'lumot o'rnida muhim bir narsani aytib o'tish kerakki, ORMni o'rganish sizni hech qachon SQLni o'rganishdan to'xtatishi kerak emas. ORM shunchaki sizning ishingizni osonlashtirish uchun yaratilgan. ORM yaratgan qulayliklarni SQLni tushunmasdan o'rganyotgan bo'lsangiz avvalo uni o'rganishingizni tavsiya beraman.

ORMning amaliy qismini platformaning boshqa qismida ko'rishingiz mumkin. Agar tushunishda muammo bo'lyotgan bo'lsa boshqa resurslardan o'qib ko'ring.
