---
description: Og'abek Ochilov
---

# MSIL

Biz sizlar bilan barcha dotnet dasturchilari bilishi lozim bo’lgan mavzu - o’zimiz yozgan kodimizning qanday kompilyatsiya bo’lishini ko’rib chiqamiz.

.Net da MSIL nima?

Dasturni ishlab chiqish jarayonida .Net platformasi turli dasurlash tillari(C#, F#,Visual basic) uchun har birida alohida kompilyatorlardan foydalanadi. Biz yozgan kodimiz kompilyatsiya jarayonidan keyin, har bir .Net kompilyatori kodimizni **intermediate code** (o’rta kod) ga o’girib beradi, va har bir muhit bunda MSIL dan foydalanadi.

Bu bo’limda biz MSIL nima ekanligini batafsil o’rganamiz.

## MSIL nima?

Microsoft Intermediate Language (MSIL) ba’zan Common Intermediate Language (CIL) nomi bilan ham ataladi. U turli kompilyatorlar (C#, VB, .NET va boshqalar) tomonidan ishlab chiqariladi va tillarning xos kompilyatorlaridan mutlaqo turli tushuncha hisoblanadi.

NET Framework SDK (FrameworkSDKBinildasm.exe) tarkibiga kiritilgan ILDasm (Intermediate Language Disassembler) dasturi foydalanuvchilarga MSIL kodini inson o‘qiy oladigan formatda ko‘rish imkonini beradi. Ushbu dastur yordamida biz MSIL kodini istalgan.NET bajariladigan faylida (EXE yoki DLL) ko'rishimiz mumkin.

## Execution (bajarish) jarayoni CLR(Common language runtime) da

Quyidagi jarayonda biz MSIL ishlashi va JIT kompilyatorining MSIL ni mashina kodiga o’girishi ko’rsatib beramiz.

• CLR kompilyatsiya qilish vaqtida tilga xos kompilyator manba kodini MSIL ga o'zgartiradi. MSILga qo'shimcha ravishda, kompilyatsiya paytida metama'lumotlar hosil bo'ladi. Metama’lumot koddagi turlarning ta'rifi, assembly versiyasi, qo’shimcha ulangan tashqi assembly ro’yxati, shuningdek, runtime(ish vaqti) haqidagi ma'lumot kabi elementlarni o'z ichiga oladi.

• MSIL CLI(Common Language Infrastructure ) assembleyida jamlanadi. Bu assembly xavfsizlik, versiyalashtirish, deployment va boshqa maqsadlarda foydalanish uchun qurilgan kodlar kutubxonasi hisoblanadi. U ikki turga bo'linadi: process assembly (EXE) and library assembly (LIB) (DLL).

• Keyin JIT kompilyatori Microsoft Intermediate Language (MSIL) ni o'zi bajarayotgan kompyuter muhiti bilan bog'liq bo'lgan mashina kodiga tarjima qiladi. MSIL kodimizni turli talablar asosida mashina kodiga aylantiriladi, ya'ni JIT kompilyatori butun MSIL emas, balki faqat zarur bo'lgan MSIL ni kompilyatsiya qiladi.

• So’ngra JIT kompilyatori kompyuter protsessorida bajariladigan mashina kodini hosil qiladi.

Umumiy ko’rinishda quyidagi jarayon sodir bo’ladi:

![Execution process in Common Language Runtime (CLR)](https://user-images.githubusercontent.com/91861166/158581645-c6c04764-c958-4048-9af0-bccf3f36d321.png)

**.Net da MSIL ning rollari**

1. **Platform Independence:** - Platforma mustaqilligi bir xil bayt kodli buyruq fayli istalgan platformaga joylashtirilishi mumkinligini anglatadi. Boshqacha qilib aytganda, MSIL ma'lum bir protsessorga bog'liq bo'lmagan portativ ko'rsatmalar to'plamini belgilaydi.
2. **Performance Improvement:** - Bir vaqtning o'zida butun dasturni yaratish o'rniga, JIT kompilyatori kerak bo'lganda kodning har bir qismini kompilyatsiya qiladi. Biz kodni bir marta kompilyatsiya qilganimizda, kompilyatsiya toki application (ilova) yaratgunimizga qadar saqlanib qoladi, shuning uchun biz kodimizni qayta run(yurg’izish) qilishimizga hojat qolmaydi. Bu usul to'liq dastur kodini boshidan kompilyatsiya qilishdan ko'ra tezroq. Bundan tashqari, MSIL kodini ishga tushirish native mashina kodini ishlatish kabi tez ekanligini ko'rsatadi.
3. **Language Interoperability:** - Tilning o’zaro muvofiqligi uning foydalanuvchanligini oshiradi. Bitta tildan MSIL ga kompilyatsiya qilish mumkin va natijada olingan kod boshqa tildagi kodga (MSIL ga kompilyatsiya qilingan) mos keladi. Til tanlash ishlab chiquvchilar tomonidan nazorat qilinmaydi. Osonroq tushuntiradigan bo’lsak bitta dasturda bir nechta tillardan ham foydalanish mumkin. Quyidagi rasmda yanayam tushunarliroq bo’ladi degan umiddaman.

![](https://user-images.githubusercontent.com/91861166/158581997-0982ead2-f485-4f3a-98dc-5deabc007dca.png)

1. **Reducing maintenance headaches:** - CLR MSIL kodini xavfsizlik standartlarga mos kelishini tekshiradi. Build time vaqtida xavfsiz bo’lmagan qismlarni aniqlashi mumkin, bu esa texnik xizmat ko’rsatish bosh og’riqlarini sezilarli darajada kamaytiradi.

Xulosa o’rnida shuni aytishimiz mumkinki, MSIL kodi har bir.NET assemblyning asosidir. MSIL instruksiyalar toʻplamini qanchalik koʻp bilsangiz, mukammal .NET ilovalarini ishlab chiqishni shunchalik yaxshi tushunasiz.
