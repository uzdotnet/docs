---
description: Abdumannon Shamsiyev
---

# Stream I/O

Bilamizki hozirgi kunda kompyuter va texnologiyalar jadal suratlarda rivojlanib bormoqda. Deyarli har kuni texnologiya olamida yangidan yangi o’zgarishlar, texnologiyalar, interactive dasturiy mahsulotlar yaratilmoqda. Shuni bilishingizni istardimki, bularning barchasining zamirida “Axborot” degan tushuncha bor. Axborot tushunchasiga ta’rif berish yoki uni to’loqonli tushuntirib berish mushkul masala. Shu sababli hamma axborotga nisbatan o’zining hissiyotlari orqali tushuncha oladi. Shu sabab axborot tushunchasini umumiy ifodalashimiz mumkin. Axborot deb insonning borliq bilan ta’sirlashishi(qarashga qarab tabiatning insonga yoki insonning tabiatga) va uni hissiyotlari bilan his qila olish qobiliyati orqali olgan qarashlariga aytiladi. Misol:

Kichkinalik vaqtingizda hali olov nimaligini bilmagan vaqtingizda qo’lingiz yoki biror tana a’zoingiz bilan olovga yaqinlashib ko’rgan vaqtingizni eslang. Aynan o’sha lahzada siz borliq va uning elementi - olov bilan ta’sirlashgansiz. Va shu vaqtda siz taxminan borliqda quyidagicha axborotlarni olgansiz: 

*	Olovning issiq bo’lishi;
*	Kuchli olov insonga nisbatan salbiy ta’sir ko’rsatishi(kuydirishi);
*	Olovni aql bilan ishlatsa inson faoiliyatida katta o’rin egallashi

kabi axborotlarni tanangiz va miyya faoliyatingiz orqali his qilgansiz. Va miyya bu ma’lumotlarni keyingi safar olov bilan qayta ta’sirlanish uchun tajriba ilmi sifatida saqlab qo’ygan. Shu sababdan ham biz olov bilan ehtiyotkor bo’lishga o’rganganmiz.

Aslida axborot mana shu, ya’ni Axborot – insonning ta’biat bilan ta’sirlashuvi demakdir.
Va bu jarayonga "contex" ni yana qaytarmoqchiman. Ya’ni olov bilan sizning ta’sirlashuv jarayoningizga. Sizning ta’na a’zoingiz olovga ya’qinlashgan vaqtda nimani his qilasiz?

Albatta aytish mumkinki, Issiqlik. Ammo uni ko’zingiz bilan ko’rmaysiz. Shunchaki uni his qilasiz. Bu hissiyot esa ta’na a’zoingizning olovga ya’qinlashgan qismida joylashgan hujayralarning signallar hosil qilishi bilan sodir bo’ladi. Hujayralar ham siz bilan birgalikda tabiat bilan ta’sirlashada va signallar chiqaradi. Bu signallar esa nerv tomirlari orqali miyyaga boradi. Va miyya o’sha tana a’zoingizni himoya qilishga buyruq beradi. Qo’polroq qilib tushuntirganda umumiy jarayon shunaqa kechadi. Bu yerda e’tibor berishingizni so’ragan bo’lar edim, ya’ni nerv tomirlari signallarni miyyaga olib o’tish jarayoniga. Bu jarayonda signallar ayni olov ta’sirida bo’lgan hujayralarda hosil bo’ladi, yig’iladi va miyyaga uzatiladi. Mana shu uzatish jarayonini stream deya olamiz. Ya’ni Streamda ham axborot manbai va u uzatiladigan joylar mavjud bo’ladi. Va axborot stream bo’ylab uzatilib turadi. Vaqt o’tishi bilan stream ishini tugatgach u axborot manbai va u yuborilayotgan joy o’rtasida bog'lanish(connection) uziladi. Huddi tana a’zoimizni olovdan olib qochganda tinchlanganimiz kabi stream egallab turgan hajm yo’qotiladi. To’g’ri yuqorida yozganlarim tushunishga qiyin va juda murakkablashib ketgan bo’lishi mumkin. Ammo shu mavzuimiz ning asosi hisoblanadi.

Endi Texnik jihatdan stream larning ishlatilishini kuzatamiz. Demak stream lar ikki 2 qismdan iborat bo’ladi. Ya’ni axborot manbai va bu axborotni qabul qiluvchilar. Axborot manbai bo’lib hozirgi kundagi juda ko’plab qurilmalarni misol qilishimiz mumkin. Misol uchun wifi bilan ishlaydigan sichqoncha, televizor pulti va hokazolar. Qabul qiluvchilar esa mos ravishda kompyuter, TV. Ular o’rtasidagi almashayotgan ma’lumot esa axborot. U har xil ko’rinishda bo’lishi mumkin. Misol uchun 0 va 1 lar ko’rinishida(digital), analog elektr signallari yoki insonning tanasida kechuvchi signallar yoki bo’lmasa yorug’lik kabilar. Umuman olgan da streamning tushunchasi shunaqa.

Endi streamlarni dasturlash da qanday foydalanilishi ko’rib chiqamiz. Bu jarayonni C# dasturlash tilida .Net SDK sidan foydalangan holda amalga oshiramiz.
Quyida ko’rib turganingiz .NET dagi System.Stream class. Bu class ning modeli yuqorida aytib o’tgan mulohazalarimiz asosida tuzilgan.
 
![](https://user-images.githubusercontent.com/91861166/223753297-cfd64236-f175-4eea-9003-d553a4b632a3.png) 
 
Yuqoridagi Stream klassi va uning ichidagi barcha method va propertylarni ko’rishingiz mumkin. Bu yerda avval boshida aytib o’tgan mulohazalar dasturchiga oson bo’lguncha abstractionga aylantirilgan. Ammo e’tibor bilan bu klassni o’rganishga harakat qilsak avval boshida aytilgan mulohazalar implememtation qilinganini ko’rishimiz mumkin. Va yana shuni aytishimiz kerakki bu Stream faqat 0 va 1 ko’rinishidagi axborotlar bilan ishlaydi. Sabibi bilamizki bu yerda Stream axborotini qabul qiluvchi qurilma Kompyuter. Kompyuter esa faqat 0 va 1 ko’rinishidagi raqamli signallarni tushunadi. Endi bu method va propertylarning ba’zilari bilan tanishib chiqamiz.

*	Length – bu stream o’zida olib ketayotgan axborotning hajmi demakdir.
*	Position  - bu stream dan ma’lumot o’qilayotganda yoki yozilayotganda aynan nechinchi byte ni yozayotganiga qarab belgilanadigan qiymat.
*	CanRead – bu stream o’qiyotgan manbaning xususiyatlari va kelib chiqish shakliga qarab o’sha manbadan ma’lumot o’qish mumkin yoki mumkin emasligini ifodalaydi.
*	CanSeek – bu stream o’qiyotgan manbaning xususiyatlari va kelib chiqish shakliga qarab o’sha manbadan o’qilayotgan ma’lumot bo’ylab ma’lumotlar ustida “Sakrash” yoki “O’tish” funksiyasini bajara olish mumkinligi yoki mumkin emasligini ifodalaydi.
*	CanWrite – bu stream yozilayotgan yoki ma’lumot yuborilayotgan manbaning xususiyatlari va kelib chiqish shakliga qarab o’sha manbaga ma’lumot o’tkazish yoki yozish mumkin yoki mumkin emasligini ifodalaydi.
*	Close – bu streamni ma’lumot olinayotgan va ma’lumot uzatilayotgan manbalar uchun faoliyatini yopadi. Ya’ni stream kompyuter xotirasidan butunlay o’chirib yuborilmaydi. Shunchaki keyinchalik o’chirilib yuborilish uchun priotite ni o’zgartiradi. Bu amaldan keyin streamdan ma’lumot olib ham ma’lumot uzatib ham bo’lmay qoladi
*	Dispose – bu streamni ma’lumotlari bilan birgalikda xotiradan bo’shatish amali
*	Flush – bu streamning bufferini tozalaydi. Buffer haqida esa keyingi mavzularda gaplashamiz.
*	Read – bu stream olib kelayotgan ma’lumotning o’lchamidan bir birlik olishni anglatadi. Bizning holatda esa ma’lumotning  birligini o’qib oladi.
*	Write – bu streamga 1 birlik ma’lumotni yozadi va u axborotni qabul qiluvchi manbaga uzatiladi.
System.Stream bu C# dagi eng kichik tushuncha. Deyarli Barcha I/O operationlarda Streamning o’rni katta. Streamga aloqador I/O operationni bajarishga yo‘naltirilgan klasslar asosiga yuqorida o’rgangan Sytem.Stream klassini asos qilib oladi. Misol uchun C#(.NET) da tayyorlab qo’yilgan quyidagi klass larni keltishimiz mumkin:
*	InputStream
*	OutputStream
*	Console
*	FileStream
*	StreamReader
*	TextReader
*	BufferStream
*	MemoryStream

va hokazolar.

Shunday qilib streamlar haqida o’rganishimiz kerak bo’lgan boshlang'ich ma’lumotlar shular edi.
