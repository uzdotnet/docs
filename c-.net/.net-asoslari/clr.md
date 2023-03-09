---
description: Kanalbekov Umarbek
---

# CLR

Common Language Runtime(CLR) .NET dasturlarining ishlash jarayonini  boshqaradi. O'z vaqtida kompilyator kompilyatsiya qilingan codeni yani (MSIL) codeni mashina codega ( 0 va 1 larga)  kompilyatsiya qiladi. 

CLR tomonidan taqdim etiladigan xizmatlar xotirani boshqarish, xatoliklar bilan ishlash, xavfsizlik va boshqalarni o'z ichiga oladi.


### Common Language Runtime(CLR)ni to’liqroq tushuntiradigan bo’lsam:
CLR .NET ning asosiy komponentidir. Bu codelarni boshqaradigan va turli xizmatlarni taqdim etish orqali ishlab chiqish jarayonini osonlashtirishga yordam beradigan .NET runtime muhitidir. Asosan, u har qanday .NET dasturlash tilidan qat'iy nazar .NET dasturlari bajarilishini boshqarish uchun javobgardir. Common Language Runtime ostida ishlaydigan code boshqariladigan code deb ataladi. Boshqacha qilib aytganda, CLR .NET uchun boshqariladigan runtime muhitini ta'minlaydi, deb ayta olamiz.

![](https://user-images.githubusercontent.com/91861166/223932932-6b84b63b-51d9-43a9-be46-db35b6e46da1.png)

### C# dasturini Run qilishda CLR ning roli.
Faraz qilaylik, siz C# dasturini yozdingiz va uni program deb nomlanuvchi faylga saqladingiz.
Tilga xos kompilyator manba codeini metama'lumotlari bilan birga CIL (Common Intermediate Language) yoki IL (Intermediate Language) deb ham ataladigan MSIL (Microsoft Intermediate Language) ga kompilyatsiya qiladi. 

Endi CLR ning navbati. CLR MSIL codega xizmatlar va runtime ish muhitini taqdim etadi. Ichki CLR MSIL codeni keyinchalik protsessor tomonidan bajariladigan mashina codega aylantiruvchi JIT (Just-In-Time) kompilyatorini o'z ichiga oladi. CLR MSIL codeini boshqaradigan dasturlash tili, muhiti, versiyasi va classlari haqida ma'lumot beradi. CLR keng tarqalgan bo'lgani uchun u boshqa tilda yozilgan classga boshqa tilda yozilgan classni ulash imkonini beradi.

### Garbage Collection (GC)
Do’stlar, bir asosiy narsani, CLR ning asosiy terminlaridan biri Garbage Collection (GC) keling uni ham bir ko’rib chiqsak.

Garbage Collection (GC) - bu .NET va boshqa ko'plab dasturlash tillarida qo'llaniladigan xotirani boshqarish usuli. C# da Garbage Collection(GC)  xotirani boshqarish va ilova tomonidan foydalanilmayotgan xotirani avtomatik ravishda bo'shatish uchun javobgardir.
Garbage Collection (GC) dastur xotirasini vaqti-vaqti bilan skanerlash orqali ishlaydi va qaysi ob'ektlar hali ham foydalanilayotganligini va qaysi biri kerak emasligini aniqlaydi. Endi foydalanilmayotgan ob'ektlar belgilanadi va ular band qilib turgan xotira joyi Garbage Collection(GC) tomonidan avtomatik ravishda bo'shatiladi.

Garbage Collection(GC) asosiy xususiyatlaridan ba'zilari:
Avtomatik xotirani boshqarish: Garbage Collection(GC) bilan ishlab chiquvchilar xotirani qo'lda ajratish yoki bo'shatish haqida tashvishlanishlari shart emas. Garbage Collection(GC) avtomatik ravishda xotirani boshqarishga yordam qiladi, bu esa oshiqcha ma’lumotlar bilan  xotira to’lish xavfini va boshqa muammolarni bartaraf etishga yordam beradi.
Ilova ishlashiga kam ta'sir etadi: Garbage Collection(GC) orqada ishlaydi va odatda dastur ishlashiga kam ta'sir qiladi. Biroq, ba'zi hollarda, keraksiz ma’lumotlarni yig’ish ko’proq vaqit olishi mumkin, ayniqsa, bir vaqtning o'zida katta hajmdagi xotirani bo'shatish kerak bo'lganda, dasturda qisqa pauza yoki tezlikga biroz ta’sir etishi mumkin.
Avlodga asoslangan yig'ish: Garbage Collection(GC) xotirani boshqarishda avlodga asoslangan yondashuvdan foydalanadi. Ob'ektlar dastlab "yosh" avlodda taqsimlanadi va agar ular bir nechta tekshiruv  davrlarida omon qolsa, "eski" avlodga o'tkaziladi. Ushbu yondashuv ishlatilmayotgan ma’lumotlarni yig’ib olish uchun zarur bo'lgan vaqtni qisqartirishga yordam beradi, chunki ko'pchilik ob'ektlar yosh avlodda yig'iladi.
Yakunlash: Garbage Collection(GC) ob'ektlarni yo'q qilishdan oldin tozalash vazifalarini bajarishga imkon beruvchi jarayon bo'lgan yakunlashni qo'llab-quvvatlaydi. Yakunlovchilari bo'lgan ob'ektlar boshqa barcha ob'ektlar yig'ilgandan so'ng, Garbage Collection(GC) tomonidan qayta ishlanadigan alohida yakunlash navbatiga o'tkaziladi.


### Boshqariladigan code va boshqarilmaydigan code
Keling boshqariladigan code va boshqarilmaydigan code haqida gaplashsak.
Boshqariladigan code  CLR (Common Language Runtime) tomonidan boshqariladigan code . Boshqarilmaydigan code esa to'g'ridan-to'g'ri operatsion tizim tomonidan bajariladigan code. Quyida boshqariladigan code va boshqarilmaydigan code o'rtasidagi muhim farqlar keltirilgan:


Boshqariladigan code |	Boshqarilmaydigan code
---------------------|------------------------
CLR tomonidan boshqariladi.	| U to'g'ridan-to'g'ri operatsion tizim tomonidan o’qiladi.
Yozilgan dastur xavfsizligini ta'minlaydi.	| Bu ilova uchun hech qanday xavfsizlikni ta'minlamaydi.
Xotira buferining to'lib ketishi sodir bo'lmaydi.	| Xotira buferi to'lib ketishi mumkin.
U axlat yig'ish, xatoliklarni qayta ishlash va boshqa runtime xizmatlarini taqdim etadi.	| U axlat yig'ish, xatoliklarni qayta ishlash va boshqa runtime xizmatlarini taqdim etmaydi.
Manba codei IL yoki MSIL yoki CIL oraliq tilda tuzilgan . | 	Manba codei to'g'ridan-to'g'ri 0 va 1 larga kompilyatsiya qilinadi.



