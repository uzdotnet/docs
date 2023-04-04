---
description: Jaloliddin Axmedov
---

# Swagger nima?

Swagger loyihasi 2015-yilda OpenAPI tashabbusiga sovg‘a qilingan va shu vaqtdan boshlab OpenAPI deb nomlanadi. Ikkala ism ham bir-birining o'rnida ishlatiladi. Biroq, "OpenAPI" spetsifikatsiyaga ishora qiladi. "Swagger" SmartBear kompaniyasining OpenAPI spetsifikatsiyasi bilan ishlaydigan ochiq manbali va tijorat mahsulotlari oilasiga ishora qiladi. Keyingi ochiq manbali mahsulotlar, masalan, OpenAPIGenerator , SmartBear tomonidan chiqarilmaganiga qaramay, Swagger familiyasiga ham tegishli.



Qisqasi:

OpenAPI - bu spetsifikatsiya.
Swagger - bu OpenAPI spetsifikatsiyasidan foydalanadigan asbob. Masalan, OpenAPIGenerator va SwaggerUI.

 Swagger-ning asosiy maqsadi odamlar va mashinalar uchun tushunarli bo'lgan hujjatlarni avtomatik ravishda yaratishdir. Shunga ko'ra, u ko'pincha API kodini tez va oson hujjatlashtirish uchun ishlatiladi. Odatda RESTful API arxitekturasi bilan birgalikda ishlatiladi .
 
 **API ishlab chiqish**. Swagger, masalan, ishlab chiquvchi mahsulotni takomillashtirishda hujjatlarga murojaat qilishi kerak bo'lganda yoki uni koddan yaratmoqchi bo'lganda ishlatiladi. Ba'zan teskari jarayon talab qilinadi - Swagger Codegen komponenti tufayli mumkin bo'lgan hujjatlar asosida kod yaratish. Bu haqda quyida gaplashamiz.

 **API o'zaro ta'siri**. Kod yaratish qobiliyati boshqa loyihalarning API bilan o'zaro aloqada bo'lganda ishlatiladi. Swagger Codegen oxirgi mijoz uchun API bilan ishlaydigan kodni yaratishi mumkin - bu vaqtni tejash maqsad bo'lganda qulaydir.

![API uchun Swagger spetsifikatsiyasini qo'lda yozishingiz yoki uni manba kodingizdagi izohlardan avtomatik ravishda yaratishingiz mumkin. ](https://user-images.githubusercontent.com/91861166/229706799-30007bf8-a116-492b-8720-223c24de1e06.png)


**Shunday qilib, API uchun Swagger spetsifikatsiyasi bor.**

Swagger API rivojlanishini yanada rivojlantirishga yordam beradigan bir necha usullar mavjud:

*	Birinchi dizayn foydalanuvchilari: API uchun server stubini yaratish uchun Swagger Codegen- dan foydalaning. Faqatgina server mantiqini amalga oshirish qoladi - va sizning API jonli ishlashga tayyor!

*	API uchun 40 dan ortiq tillarda mijozlar kutubxonalarini yaratish uchun Swagger Codegen- dan foydalaning .

*	Interfaol API hujjatlarini yaratish uchun Swagger UI dan foydalaning , bu foydalanuvchilarga API qo‘ng‘iroqlarini bevosita brauzerda sinab ko‘rish imkonini beradi.

*	API bilan bog'liq vositalarni API-ga ulash uchun spetsifikatsiyadan foydalaning. Masalan, API uchun avtomatlashtirilgan testlarni yaratish uchun spetsifikatsiyani SoapUI -ga import qiling.

*	Va yana! Swagger bilan integratsiyalashgan ochiq manbali va tijorat vositalarini ko'rib chiqing .
 
![](https://user-images.githubusercontent.com/91861166/229706914-5a10ecda-b151-4101-b457-0c3c217afe17.png)

![](https://user-images.githubusercontent.com/91861166/229707000-5f16148e-22b9-43de-9d10-8bd2f72a7aa7.png)


## Swagger-dan kim foydalanadi
*	Loyihaning API-ni tezda hujjatlashtirishni xohlaydigan va hujjatlarni noldan yozishga vaqt ajrata olmaydigan dasturchilar.
*	Uchinchi tomon dasturiy mahsulotining API-ni joriy qilmoqchi bo'lgan ishlab chiquvchilar - ular hujjatlardan, shu jumladan Swagger-da yaratilganlardan foydalanadilar.
*	Loyihalar uchun hujjatlarni yaratishda texnik yozuvchilar - asosiy yoki yordamchi vosita sifatida.

## Spetsifikatsiya qanday ishlaydi
Ob'ekt, foydalanuvchi nomi, modul nomi, havola yoki boshqa narsa bo'lishi mumkin. Sakkizta asosiy ob'ekt mavjud; qolganlari ular ichida joylashgan:
*	openapi. Uning qiymati loyihada ishlatiladigan OpenAPI versiyasidir;
*	ma'lumot. API haqida asosiy ma'lumotlarni o'z ichiga olgan ichki o'rnatilgan ob'ektlarni o'z ichiga oladi: ism, tavsif, litsenziya, ishlab chiquvchi kontaktlari va boshqalar;
*	serverlar. Serverlarga olib boradigan havolalarni o'z ichiga oladi - so'nggi nuqtalardan qat'iy nazar tashqaridan kirish uchun asosiy yo'llar;
*	yo'llar. Yakuniy nuqtalarni yoki so'nggi nuqtalarni (oxirgi nuqtalarni) tavsiflaydi - ma'lum bir ob'ektga boradigan yo'lning oxiri. Har bir so'nggi nuqta uchun GET, POST, DELETE va PUT so'rovlari yoziladi - ob'ekt bilan o'zaro aloqa qilish operatsiyalari;
*	komponentlar. U hujjatlarning turli joylarida ishlatilishi mumkin bo'lgan sxemalarni saqlaydi. Masalan, "Ism", "Manzil" va boshqalar maydonlari bilan "Foydalanuvchi" sxemasini yaratishingiz mumkin. Komponentlarda tavsiflanganidan so'ng, sxema hujjatlar kodida qo'shimcha ravishda ishlatilishi mumkin;
*	teglar. Teg metama'lumotlarini saqlaydi: sarlavha, tavsif va boshqalar. Nima bo'layotganini batafsilroq tasvirlashga yordam beradi;
*	xavfsizlik. API bilan ishlatilishi mumkin bo'lgan xavfsizlik usullarini tavsiflaydi;
*	externalDocs. Odatda qo'shimcha ma'lumotlarga ega bo'lgan tashqi hujjatlarga havolalarni o'z ichiga oladi. Masalan, bu kodda ishlatiladigan uchinchi tomon vositalarining hujjatlari bo'lishi mumkin.

## Swagger-dan foydalanishning afzalliklari
*	Swagger hujjatlarni yozishni soddalashtiradi va tezlashtiradi, ishlab chiquvchilar va texnik yozuvchilar uchun vaqtni tejaydi.
*	Siz uy ishlarini qisqartirishingiz va Swagger Codegen-ni ishlab chiqarishga ruxsat berishingiz mumkin: bu yana vaqtni tejaydi.
*	Hujjatlar barcha toifadagi o'quvchilar uchun batafsil va tushunarli: texnik mutaxassislar, oddiy foydalanuvchilar va robotlar.
*	Siz Swagger-dan juda moslashuvchan foydalanishingiz mumkin: kod yoki o'zingizga asoslangan hujjatlarni yarating, sinov va tezkor navigatsiya uchun vizual interfeys imkoniyatlaridan foydalaning.
*	Swagger bilan yozilgan hujjatlar veb-sayt sahifasi yoki ilovasiga osongina joylashtirilishi mumkin va interaktiv va to'liq ishlaydi. Ammo displeyning o'z versiyasini yaratish yaxshiroqdir - standart interfeys haqiqiy saytlarning dizayniga unchalik mos kelmaydi.

