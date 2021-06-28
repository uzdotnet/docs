---
description: Muhammadkarim To'xtaboyev
---

# Web API ga kirish

### Kirish

Assalomu alaykum .NET ahli, ushbu bo'limni ham mana yozishga qaror qildik! Web API nimaligini tushintirishdan avval sizlarga nimalar o'rganishimiz haqida so'zlab o'tsam:

* Fundament \(asos, boshlang'ich\)
* RESTful API
* Middleware
* Dependency Injection
* Routing
* Format Response
* Model Binder
* Kitob magazini sayti
* Entity Framework Core 5.0
* Angular da API dan foydalanish
* JWT orqali kirish va ro'yxatdan o'tish

Bular haqida batafsilroq o'rganasiz albatta. Hozir esa web api nimaligini o'rganing!

### Web API nima?

API so'zi shunchaki qisqartma bo'lib, aslida **Application Programming Interface** degan ma'noni anglatadi. Ushbu tehnologiyaning afzalliklari judayam ko'p. Men sizlarga anavi kitoblardagidek yoki youtube da ko'rgan videolaringizdek emas, oddiy dehqonchasiga tushuntiraman. API shunchaki qaysidir joyga borish uchun ochiq yo'l. Backend va Frontend chilarni bog'lab turuvchi bir rishta :\) Habaringiz bor yoki ushbu maqolani o'qishdan avval kamida bir marta ASP.NET Core Web MVC ga qiziqib ko'rgansiz. Gapni ko'p aylantirmay, hamma yangi dasturchilar, bitta saytni p'zi noldan ko'tarmoqchi \(yasamoqchi bo'ladi\). Yasasa bo'ladi albatta, u insonni fullstack \(hoji aka\) deb atashadi. Ya'ni Frontend ni ham Backend ni ham birgalikda o'zi yozadi kodini. Hozirda zamon shunday zivojlanyaptiki, bu narsalarga alohida alohida dasturchilar biriktirilyapti. Sababi hamma o'zini ishini qilsa, keyin o'zish bo'ladi jamiyatda. Backend chilar faqat saytni orqasini qiladigan, service yozadi... Frontend chilar esa sayt ustini chiroyli qilib shakllantirib, Backendchi bergan API lar orqali bazaga borib ma'lumotlarni oladi. Ya'niki, shu muammolarda qutilish uchun Web API ni ishlab chiqdilar. Backend dasturchisi asosan ma'lumotlar bazasi bilan ishlaydi va websaytga bog'laydi. Qandaydir hizmat yaratadi. Keyin o'sha hizmatdan foydalanish uchun rasmiy tarzda API lar yaratib beradi \(yo'llar - frontend chi backendchining eshigidan kirib kelishi uchun\). Asosan API lar URL ko'rinishida bo'ladi. Hullas Frontendchi API ga so'rov yuborsa \(ma'lumot olib kelish uchun elchi\), Backendchi uni kutib olib, agar kelisha olsalar, so'ragan ma'lumotlarni [JSON](https://docs.dot-net.uz/c-.net/.net-dasturchi/api-dan-foydalanish) \(JavaScript Object Notation\) nomli idishga qadoqlab solib beradi, ushla olib ket deb. Keyin Frontendchiga javob yuboradi, Frontchi esa uni qabul qilib, JSON nomli idishdan chiqarib oladi, so'ngra uni foydalanuvchiga chiroyli qilib chiqarish maqsadida har xil komponentlardan foydalanadi. 

![Idish - JSON, ichidagi narsa ma&apos;lumot, qo&apos;llar esa backend va frontend](../../../.gitbook/assets/image%20%2891%29.png)

![Frontend / Backend](../../../.gitbook/assets/image%20%287%29.png)

Frontend bir necha xil platformada bo'lishi mumkin, lekin backend bitta bo'ladi. Ya'ni Desktop \(kompyuter dasturi\), Mobil \(mobil dastur\), Web front \(websayt\) ko'rinishida bo'lishi mumkin frontend. Masalan Telegramni olaylik, uning kompyuter uchun ham, mobil uchun ham, websayt uchun ham frontend dasturlari bor va ular faqat bitta backend hizmatidan foydalanishadi. Buni bilish qiyin emas. Telefoningizdagi telegramdan do'stingizga nimadir habar yuborsangiz, kompyuterda ham yuborilgani ko'rinadi. Demak ularning manbaasi bir joyda. O'sha manbaa backend deb ataladi....

