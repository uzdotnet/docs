---
description: Mamataliyev Diyobek
---
# Exception Handling

Bugun siz bilan xatoliklar(exceptions) haqida gaplashamiz. Bu shunday xatoliklarki, xatolik sababini bartaraf etmaguningizgacha dasturni ishlata olmaysiz. Masalan, murojaat qilingan fayl ko'rsatilgan manzilda mavjud emasligi, nolga bo'lish, massiv elementlariga murojaat qilayotganda massiv chegarasidan chiqib ketish va hokazo. Bunday xatoliklarga duch kelganingizda dastur logikasini o'zgartirib, xatolik yuzaga keltirmaydigan kod yozishingiz yoki xatolik yuzaga kelganda bajariladigan amallarni belgilash uchun try/catch blokidan foydalanishingiz kerak bo'ladi. 

Xatolik(exception)lar yuzaga kelganda, kompilyator har bir xatolik uchun mos bo'lgan alohida xatolik oynasini ekranga chiqaradi:

![](https://user-images.githubusercontent.com/91861166/139944019-846eb307-c9cd-4d75-a4fa-941804064cf7.png)

Yuqoridagi rasmda 7 ni 0 ga bo'lishga urinish tufayli `System.DivideByZeroException` xatoligi yuzaga kelgan.

**try/catch** blokidan foydalanish uchun xatolik sababi va nomini bilishingiz kerak bo'ladi.Endi esa shu kabi xatoliklarni bir-biridan ajratib olish uchun birma-bir tanishib chiqamiz: 

### System.DivideByZeroException
Biror sonni nolga bo'lishga urinish tufayli yuzaga keladi

### System.IO.IOException
Fayl va papkalar bilan ishlaganda yuzaga keladigan xatoliklarni o'z ichiga oladi. 

**System.IO.PathTooLongException** - dastur kodida yangi fayl yoki papka e'lon qilinayotganda unga qo'yilgan nom juda uzun bo'lib ketganda yuzaga keladi. Faylga qo'yiladigan nomning maksimal uzunligi 260 ta belgidan, katalog(papka)ning nomi 248 ta belgidan ortib ketmasligi shart. 

**System.IO.UnauthorizedAccessException** - fayl yoki papka ustida bajarish mumkin bo'lmagan amalni bajarishga uringanda yoki xavfsizlik tufayli kirish taqiqlangan fayl/papkaga kirishga uringanda yuzaga keladi. Masalan, faqat o'qish uchun ochilgan faylga yozishga urinishda shu xatolik oynasi ekranga chiqadi.

**System.IO.FileNotFoundException** - mavjud bo'lmagan faylni dastur kodida yozilganda shu xatolik yuzaga keladi.

**System.IO.DirectoryNotFoundException** - dasturda aslida mavjud bo'lmagan katalog(papka) ko'rsatilishi tufayli yuzaga keladi.

**System.IO.DriveNotFoundException** - mavjud bo'lmagan disk yoki boshqa ulanish orqali murojaat qilinganda yuzaga keladi.

### System.IndexOutOfRangeException
Massiv yoki biror to'plam elementiga indeks orqali murojaat qilinganda massiv chegarasidan kattaroq indeks ishlatilishi tufayli yuzaga keladi. Masalan, elementlari soni 12 ta bo'lgan massivning elementlari tartib raqami 0 dan 11 gacha bo'ladi. Siz 15-elementga murojaat qilsangiz ushbu xatolik bilan to'qnash kelasiz.

### System.OutOfMemoryException
Operativ xotiraning juda ko'p qismidan foydalanilganda yuzaga keladi. 32 bitli sistema uchun tuzilgan dasturlarda xotiradan foydalanishning maksimum chegarasi **2 Gb**ga, 64 bit uchun tuzilganlarda **4 Gb** ga teng. Xotiradan foydalanish bundan ortib ketishi bilan  kompilyator dastur ishlashini to'xtatadi va ushbu xatolik oynasini ekranga chiqaradi.

davomi bor..
