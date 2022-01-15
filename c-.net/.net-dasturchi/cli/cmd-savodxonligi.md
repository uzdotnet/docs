---
description: Ilhomjon Abdusaminov
---
# CMD savodxonligi
 
Hamon-ki Windows ishlatayotgan ekansiz, Windows operatsion tizimining terminali CMD ni bilishinigiz kerak. CMD ni ochish uchun klaviaturadagi “Pusk” + “R” tugmalarini qo’shib bosib, burchakda chiqqan kichik oynachaga **cmd** buyrug'ini kiritib, Enter klavishini bosasiz. Buyruqlarga o'tishimizdan avval siz uchun bitta foydali ma'lumot: pastda keltirilgan buyruqlarni bosh harfda yozsangiz ham, kichik harflarda yozsangiz ham, hatto bularni aralashtirib yozsangiz ham ishlayveradi (qaysi registrda yozishning farqi yo'q)

## Demak komandalar haqida ma’lumotlar:

Avval o’zingizga kerakli papkaga kirib olishingiz lozim:

![Menda hozir C:\Users\user> papkada ekan](https://user-images.githubusercontent.com/91861166/148175675-7086ec54-1cd8-46b9-b7be-726f1f970c36.png)

Agar siz boshqa path dagi filelar bilan ishlamoqchi bo’lsangiz. **cd** kalit so’zi bilan file joylashuvini yozasiz. Masalan: 

![Katalog(papka) ga kirish uchun ham “cd” dan keyin papka lokatsiyasini to’liq berish lozim](https://user-images.githubusercontent.com/91861166/148175831-c5a09c02-ffc9-42f0-b97f-b71f2c378148.png)

• **cd ..** buyrug’I bilan bittadan directory(papka) ortga qaytaradi: 

![](https://user-images.githubusercontent.com/91861166/148175783-2519e3e5-3b3f-4cec-b7a1-3a7ce0125ebb.png)

  		    

### CMD ning oddiy foydalanuvchi uchun kodlari:

• **Color all**  -  cmd textini rangini o’zgartiradi.

•	**Shutdown –s –f –t 100**  -  Kompyuteringizni 100 sekundan keyin o’chiradi.

•	**Shutdown – a**  -  o’chirish buyrug’ini bekor qiladi.

•	**Help**  -  sizga asosiy kodlarni ta’rifi bilan chiqarib beradi.

•	**Explorer**  -  Yo'lboshlovchi (проводник) oynasini ochib beradi.

•	**Tree**  -  kataloglarni grafik ko'rinishda ko'rsatish imkoniyatini beradi. Odatiy bo'lib, displey psevdo-grafika orqali amalga oshiriladi.

•	**Ver**  -  operatsion sistemangizning versiyasini ko’rsatadi.

• **Systeminfo**  -  ushbu buyruq sizga kompyuteringiz konfiguratsiyasi haqida batafsil ma’lumot beradi. Ro’yxat operatsion tizimingiz va uskunangizni mutlaqo qamrab oladi. Masalan “Windows” ning o’rnatilgan sanasi, oxirgi yuklash vaqti, BIOS versiya, umumiy va mavjud xotira, o'rnatilgan tuzatishlar, tarmoq kartasi konfiguratsiyasi va boshqalarni qidirishingiz mumkin.

•	**MD**  -  bu buyruq bilan siz yangi papka(katalog) yoki yangi fayl ochishingiz mumkin:

![](https://user-images.githubusercontent.com/91861166/148176372-433b740e-4d05-49ad-939f-6e403d090a59.jpg)

Albatta cmd dagi path (manzilingizni o’zgartirib o’zingizga kerakli joyga ochishingiz lozim), aks holda default o’zi turgan joyga ochib qo’yadi. 

![Masalan menda shunaqa manzilga ochiladi](https://user-images.githubusercontent.com/91861166/148176514-f4479e59-b1d3-4ac2-8919-44430185f23a.png)

•	 **Date** va **Time**  -  bu buyruqlarni alohida yozmadim. Date buyrugida siz hozirgi sanani ko’rish va o’zgartirish imkoniga ega bo’lasiz, Time komandasida esa hozirgi soat, minut va sekunni o’zgartishingiz mumkin bo’ladi.

•	 **Exit**  -  Ushbu buyruq sizga ommaviy ma'lumotlarni yopish yoki hatto buyruq qatorini yopish imkonini beradi. (Cmd dan ham chiqib ketishi mumkin).

•	 **Title**  -  ya’ni sarlavha bu bilan siz cmd oynasining nomini o’zgartirishingiz mumkin.

•  **Prompt**  -  Bu ham juda ham qiziqarli buyruqlardan biri. har safar buyruq oldidan chiqib turadigan so'zlarni o'zimizga belgilash imkoniyatini beradi. Bu rejimdan chiqib ketish uchun qaytadan **prompt** buyrug'ini kiritishingiz kerak.
 
![](https://user-images.githubusercontent.com/91861166/148176625-314d8d5f-319e-4821-9a61-97ae51baf605.png)
 
•	**Echo**  -  bunda siz huddi **prompt**dagidek, lekin **echo off** yozsangiz umuman bo’sh oynada buyruq yozish imkonini beradi keyin, **echo on** buyrug’i bilan yana tiklashingiz mumkin kerak bo’lganda.

•	 **Mode**  -  Tizim qurilmalarini sozlashda yoki ko’rishni imkonini beradi.

•	**Start**  -  Alohida oynada dastur yoki buyruqlarni ishga tushiradi. Masalan, **start mspaint** deb yozsangiz paint ishga tushadi.

### Endi Wi-fi va IP da kerak bo’ladigan buyruqlarga kelsak:

Bunda sizga wi-fi ni parolini o’zgartirish va IP bilan bog’liq qiziqarli ma’lumotlar bermoqchimiz. O’qib chiqib foydali ma’lumotlarga ega bo’ling)

•	**netsh wlan show profiles**  -  bunda siz oldin ulangan barcha wi-fi tarmoqlarini ko’rishingiz mumkin bo’ladi.

•**Netsh wlan show profiles name=”wi-fi nomi” key=clear**  -  bunda siz shu kiritgan wi-fi tarmog’ining parolini va boshqa ma’lumotlarni bilishingiz mumkin.

•	**Ipconfig**  -  bu buyruqda siz o’z IP parolingizni ko’rishingiz va IP tarmoq sozlamalaringizni ham ko’rsatadi

![Manashu rasmda joylashgan ip sizning “IP” ingiz bo’ladi](https://user-images.githubusercontent.com/91861166/148176678-c3282855-5132-4e9e-80fe-a5b52c9870a7.png)
                         
•	**Ping**  -  tarmoqga ping yuboradi ya’ni biron bir saytga so’rov yuborishingiz mumkin yoki uning ishlayotgan tarzini ko’rishingiz mumkin va yana ba'zan, paketlar ma'lum bir tarmoqqa ulangan qurilmaga ulanadimi yoki yo'qligini bilishingiz kerak. Bu yerda bizga ping yordam beradi.

•	**Arp –a**  -  bizga barcha biz bilan bir tarmoqda bo’lgan foydalanuvchilarning IP larini ko’rsatadi. Albatta bir wi-fi da bo’lsangiz. 


•	**Ipconfig/all**  -  bunda siz ip address, mac address xullas adresslar haqida ko’proq ma’lumotga ega bo’lishingiz mumkin.

•	**Getmac**  -  buyrug’I bizga tarmoq adapterlarining aparat manzillari haqida ma'lumot beradi. Bunday holda siz mahalliy va uzoq manzillarni topishingiz mumkin.

CMD orqa fonini o’zgartirish textni o’zingiz hohlagandek qilish uchun ”Administrator” ustiga sichqonchaning o’ng tomonini bosasiz va eng pastidagi “Properties” tugmasini bosasiz. Hackerlar kinolaridek qilib olishingiz ham mumkin )

![](https://user-images.githubusercontent.com/91861166/148176757-4575c1aa-7a07-4099-ad4f-c899099ea1c8.png)



CMD oynasida har xil kodlar yozib adashib qoldingizmi? Yoki u kodlarni sizga endi keragi yo’qmi? Endi sizga oxirgi eng kerakli(ko’p ishlatiladigan) buyruqni ko’rsatamiz:

• **cls** buyrug'i oynani tozalash uchun ishlatiladi:

![](https://user-images.githubusercontent.com/91861166/148176787-8e44fa40-8141-4b7c-84a2-2b48c4234a4d.png)

Ushbu buyruq oynani tozalash uchun oldingi yozilgan ma’lumotlarni barchasini “delete” qiladi.


Qo’lingizni sichqonchadan oling, CMD bilan kompyuterga yaqinroq bo’ling!
Iloji boricha kirishga yordam berishga harakat qildik, foydasi tekkan bo’lsa xursandmiz. Bu dengizdan tomchi edi, izlaning!


Qo'shimcha o'rganish uchun yana bir manba:

[https://youtu.be/lE2k\_I3E0uI?list=PLFE1Bk1-05Kzzvi-aFGxzek4MG121ZunH](https://youtu.be/lE2k\_I3E0uI?list=PLFE1Bk1-05Kzzvi-aFGxzek4MG121ZunH)
