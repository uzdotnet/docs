---
description: Rahmonberdiyev Botirali
---

# C# / .NET asoslari

### What is a reference type?(Reference ma’lumot turi nima?)
- Reference turi o’z qiymatini bevosita saqlamaydi. Buning o’rniga u xotiradagi qiymat saqlanadigan manzilni saqlaydi. Reference ma’lumot turidan foydalanilganda ikkita o’zgaruvchi bir xil ob’ektga murojaat qilgan bo’lsa, agar siz boshqa o’zgaruvchini o’zgartirsangiz ikkinchi o’zgaruvchining qiymati ham o’zgaradi. Reference turiga class, interface va delegate kiradi.
C# da reference turiga kiradigan bir nechta Data type lar bor. Ular:  **dynamic**, **object** va **string**.

### What is a value type? (Value ma’lumot turi nima?)
- Value type qiymat turi bo'lgan o'zgaruvchi to'g'ridan-to'g'ri qiymatni o'z ichiga olishini anglatadi. Demak, agar o'zgaruvchi : int number = 3; ko'rinishida e'lon qilinsa, xotiradagi 3 qiymati to'g'ridan-to'g'ri number o'zgaruvchisida saqlanadi. Value typedagi o'zgaruvchini metodga o'tkazganingizda yoki uni boshqa o'zgaruvchiga tayinlaganingizda, uning qiymati ham birga ko'chiriladi. Bu shuni anglatadiki, bitta o'zgaruvchiga o'zgartirish boshqa o'zgaruvchining qiymatiga ta'sir qilmaydi.
Value typega bir nechta misollar: **bool**, **int**, **decimal**, **double**, **enum** va **struct**.

### What is the difference between class and struct?(class va struct ning farqi ?)
- Class reference ma’lumot turi, struct esa value ma’lumot turiga kiradi. Classlar inheritance (Meros) ni qo'llab-quvvatlaydi va null bo’la oladi. Bundan tashqari murakkab ob'ektlar uchun ishlatiladi. Struct esa inheritance (Meros) ni qo’llab-quvvatlamaydi va value ma’lumot turi bo’lgani uchun kichikroq ob’ektlar uchun ishlatiladi.

### What is an Interface? (Interface nima?)
- Interfeys sinfning ichida qaysi metodlar bo‘lishini avvaldan rejalashtirish uchun ishlatiladi. Interfeysda e‘lon qilingan metodlarning faqat nomi yoziladi,  metod tanasi yozilmaydi.  Interfeyslar classdan farqli ravishda ko‘p meroslilikni qo‘llab-quvvatlaydi.

### How is code compiled in C#?  (C# da yozilgan kod qanday kompilyatsiya qilinadi?)
- C# ning sourse code c# compiler orqali IL (intermediate Language) ga o’tkiziladi va  assembly file bo’lib saqlanadi ya’ni dll va exe filega. CLR(Common Language Runtime)ning ichida JIT Compiler (Just In Time) bor,JIT  IL ga tarjima qilingan code ni machine code tarjima qiladi va prosessor machine code ni o’qiydi.

### What is file handling in C#?
- Fayl bilan ishlash fayllarni boshqarishni o'z ichiga oladi. Fayllar nomi va katalog yo'li bilan diskda saqlanadigan ma'lumotlar to'plamidir. Fayllar mos ravishda ma'lumotlarni o'qish va yozish uchun ishlatiladigan kirish va chiqish oqimlarini o'z ichiga oladi.

### What is meant by garbage collection in C#?
- Axlat yig'uvchi (GC) xotirani ajratish va chiqarishni boshqaradi. Axlat yig'uvchi avtomatik xotira boshqaruvchisi bo'lib xizmat qiladi. Xotirani qanday ajratish va bo'shatishni bilishingiz yoki ushbu xotiradan foydalanadigan ob'ektlarning ishlash muddatini boshqarishingiz shart emas.

### What is a constructor in C#? Konstruktor nima?
- C# da konstruktor classning bir qismini tashkil etuvchi metod turidir. Konstruktor classdan obyekt olinganda birinchi bo'lib ishga tushuvchi metod hisoblanadi. Uning nomi har doim class nomi bilan bir xil bo'ladi. Konstruktorning asosiy maqsadi class fieldlarini ishga tushirishdir. Yangi class ob'ekti yaratilganda ular avtomatik ravishda chaqiriladi.

### What is a destructor in C#? Destruktor nima?
- C# da destruktor (yakunlovchi) sinfdan olingan ob'ekt ishini bajarib bo'lgan sinf ob'ektlarini xotiradan o'chirib yuborib yo'q qilish uchun ishlatiladi. U sinf bilan bir xil nomga ega va tilda (~) bilan boshlanadi.

### What is a constant in C#? Konstanta nima?
- Konstantalar kompilyatsiya vaqtida ma'lum bo'lgan va dasturning ishlash muddati davomida o'zgarmaydigan o'zgarmas qiymatlardir. Konstantalar **const** modifikatori bilan e'lon qilinadi. Faqat C# o'rnatilgan turlari (System Ob'ektdan tashqari) const deb e'lon qilinishi mumkin. Masalan, `const int i=1;`
