# C# / .NET asoslari

1. What is a reference type?(Reference ma’lumot turi nima?)
- Reference turi o’z qiymatini bevosita saqlamaydi. Buning o’rniga u qiymat saqlanadigan 	manzilni           saqlaydi.Reference ma’lumot turi,ikkita o’zgaruvchi bir xil ob’ektga murojaat qilgan bo’lsa, agar siz boshqa o’zgaruvchini o’zgartirsangiz ikkinchi o’zgaruvchi ham o’zgaradi.
Reference turiga class, interface va delegate kiradi.
C# da reference turiga kiradigan bir nechta Data type lar bor ular  dynamic,
object va string.

2. What is a value type? (Value ma’lumot turi nima?)
- Value type qiymat turi bo'lgan o'zgaruvchi to'g'ridan-to'g'ri qiymatni o'z ichiga olishini anglatadi. Demak, agar o'zgaruvchi : int number = 3;
keyin xotiradagi 3 to'g'ridan-to'g'ri number o'zgaruvchisida saqlanadi. Value typedagi o'zgaruvchini metodga o'tkazganingizda yoki uni boshqa o'zgaruvchiga tayinlaganingizda, uning qiymati ko'chiriladi. Bu shuni anglatadiki, bitta o'zgaruvchiga o'zgartirish boshqa o'zgaruvchining qiymatiga ta'sir qilmaydi.. 
Value typega bir nechta misollar bool, int, decimal, double, enum va struct.

3. What is the difference between class and struct?(class va struct ning farqi ?)
- Class reference ma’lumot turi, struct esa value ma’lumot turiga kiradi.Classlar 		inheritance (Meros) ni qo'llab-quvvatlaydi va null bo’la oladi undan tashqari murakkab 	ob'ektlar uchun ishlatilishi kerak.Struct esa inheritance (Meros) ni qo’llab-			quvvatlamaydi va value ma’lumot turi bo’lgani uchun kichikroq ob’ektlar uchun 		ishlatiladi.

4. What is an Interface?(Interface nima?)
- Interface contractni belgilaydi yani shartnomani. Ushbu shartnomani amalga 	                        	         oshiradigan har qanday class yoki struct interfaceda belgilangan methodlarning va  	              	a'zolarning implementation amalga oshirilishini ta'minlashi kerak.

5. How is code compiled in C#? 
- C# ning sourse code c# compiler orqali IL (intermediate Language) ga o’tkiziladi va  assembly file bo’lib saqlanadi ya’ni dll va exe filega. CLR(Common Language Runtime)ning ichida JIT Compiler (Just In Time) bor,JIT  IL ga tarjima qilingan code ni machine code tarjima qiladi va prosessor machine code ni o’qiydi.

6. What is file handling in C#?
- Fayl bilan ishlash fayllarni boshqarishni o'z ichiga oladi. Fayllar nomi va katalog 	  	yo'li bilan diskda saqlanadigan ma'lumotlar to'plamidir. Fayllar mos ravishda 		       	     ma'lumotlarni o'qish va yozish uchun ishlatiladigan kirish va chiqish oqimlarini o'z ichiga 		oladi.


7. What is meant by garbage collection in C#?
- Axlat yig'uvchi (GC) xotirani ajratish va chiqarishni boshqaradi. Axlat yig'uvchi 		     avtomatik xotira boshqaruvchisi bo'lib xizmat qiladi. Xotirani qanday ajratish va 		     bo'shatishni bilishingiz yoki ushbu xotiradan foydalanadigan ob'ektlarning ishlash 		     muddatini boshqarishingiz shart emas.

8. What is a constructor in C#?
- C# da konstruktor classning bir qismini tashkil etuvchi usul turidir. Konstruktorning asosiy maqsadi class fieldlarini ishga tushirishdir. Yangi class ob'ekti yaratilganda ular avtomatik ravishda chaqiriladi.

9. What is a destructor in C#?
- C# da destruktor (yakunlovchi) ob'ekt doirasi tugaganda sinf ob'ektlarini yo'q qilish uchun ishlatiladi. U sinf bilan bir xil nomga ega va tilda bilan boshlanadi.

10. What is a constant in C#?
- Konstantalar kompilyatsiya vaqtida ma'lum bo'lgan va dasturning ishlash muddati davomida o'zgarmaydigan o'zgarmas qiymatlardir. Konstantalar const modifikatori bilan e'lon qilinadi. Faqat C# o'rnatilgan turlari (Tizim. Ob'ektdan tashqari) const deb e'lon qilinishi mumkin
