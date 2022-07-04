---
description: Ravshan Sodiqov
---
# Controller dan view ga ma'lumot uzatish

Dinamik sahifalar statik sahifalardan ma’lumot almashinuvlari bilan farqlanadi. MVC strukturasida View ga ma’lumotlar Controllerlar tomonidan uzatiladi. Controller esa ma’lumotlarni bir necha xil usulda uzatishlari mumkin. 

 Faraz qilaylik, «Views» → «Home» manzilida **Index View** mavjud bo’lsin. Ushbu ko’rinish **HomeController** tomonidan brauzerda aks ettiriladi va Index View dagi barcha ma’lumotlar ham ushbu **HomeController** tomonidan uzatiladi. Controllerlar ma’lumotlarni yakka holda yoki model asosida uzatishi mumkin. 

*	**ViewData[<Key>]** va **ViewBag.PropertyName** - bu ma’lumot uzatishning eng sodda usullaridan biri hisoblanadi. Bunda ma’lumot controllerda kalit asosida uzatiladi va view da shu kalit nomi bilan qiymat aniqlab olinadi. ViewBag va ViewData yordamida ma’lumot yuborilganda qiymatning turi faqatgina runtime da aniqlanadi. Shu sababli bu usul biroz xavfli va foydalanish uchun ham noqulay hisoblanadi.

*	**ViewModels** - bu ma’lumotlarni controller tomonidan uzatishning eng xavfsiz va juda qulay usullaridan biri hisoblanadi. Bu usulda ma’lumotlar modellar, ya’ni sinflar ko’rinishida uzatiladi. Sinflar esa o’zida bir necha turga mansub xususiyatlarni o’z ichiga olgan bo’lishi mumkin. Bu usul yordamida hatto bir butun ma’lumotlar bazaning qandaydir qismini yoki butunligicha ham yagona sinf yordamida uzatishimiz mumkin bo’ladi.
