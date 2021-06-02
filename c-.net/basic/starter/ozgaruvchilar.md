---
description: Abduxoshimov Hondamir
---

# O'zgaruvchilar

Barcha dasturlash tillarida eng ahamiyatli o’rinlardan birida turadigan, hamda ko’pchilikka ilk dasturlashni boshlash chog’larida muammo bo’lishga ulgurgan, ushbu mavzu to’g’risida yaqin daqiqalar ichida tushunmovchiliklarga barham beramiz. Kitobiy gaplardan boshlaganimga e’tibor bermasligingizni so'rayman, kompyuter qarshisida ko’p o’tirishning oqibati shunaqa bo’larkan. Hop endi mavzuga qaytamiz. O’zgaruvchi - bu turli xil ko’rinishdagi ma’lumotlarni o’zida saqlab turuvchi va dastur ishlash davomida qiymati o’zgarib boradigan konteyndir. Tushunish qiyin bo’lganduraa? Kayfiyatni cho’ktirmaymiz. Keling berilgan iboraga, hayotiy misol orqali o’xshatish berib ko’ramiz: Tasavvur qiling sizning uyingizda omborxona bor. Tabiiyki u yerda , kundalik yumushlaringizda foydalanadigan ishchi qurollar \(ketmon, lapatka...\) va oyingiz tayyorlagan kampot-u qiyomlar saqlanadi. Kampot shirin bo’lganidan yozning jazirama issig’ida zo’r ketadi va ombor ham asta-sekinlik bilan bo’shashni boshlaydi. Lekin omborga kirib, uni ochmaguningizgacha qishin – yozin turaveradi. O’zgaruvchilar ham bir ombor hisoblanadi. Ular ham o’zida ma’lum bir toifaga oid qiymatlarni saqlab boradi.

O’zgaruvchilarni e’lon qilish. O’zgaruvchilarni e’lon qilish uchun birinchi navbatda uning qaysi toifaga tegishliligi, uning nomi hamda unga beriladigan qiymatlarni aytib qo’yish talab etiladi.

**Tip o’zgaruvchi\_nomi = qiymati**

Tip deyilganda – int , string , double kabilar nazarda tutildi. O’zgaruvchilarni e’lon qilish to’g’risida gap ochilganda maktablardagi bir holat ko’zimning oldiga kelaveradi: 

Ustoz: - Kimning bolasisan ?   
****O’quvchi: – Direktorni.   
Ustoz: - O’tir bahoying besh!  
Ustoz: - Senchi ?   
O’quvchi: - Kirakashni.   
Ustoz: - O’tir bahoying uch!

**Otaning\_kasbi farzand = baho**

Albatta bu hazil 😊 Quyida bir necha toifaga mansub bo’lgan o’zgaruvchilarni e’lon qilishni ko’rishimiz mumkin: string toifasiga mansub o’zida “Mening Dasturim” satrni saqlab turuvchi project o’zgaruvchisini e’lon qilish:

```csharp
using System;
namespace MyProgram
{
		static void Main(string[] args)
{
		string project = “Mening Dasturim”;		
Console.WriteLine(project);	
}

}
```

Natija: Mening dasturim

int tipiga oid x o’zgaruvchisini e’lon qilish va unga 5 qiymatini o’zlashtirish

```csharp
using System;
namespace MyProgram
{
		static void Main(string[] args)
			{
						int x = 5;
						Console.WriteLine(x);
			}
}
```

Natija: 5

Eslatma: Agarda o’zgaruvchiga yangi qiymat o’zlashtirilsa, uning eski qiymati yo’qolib o’rniga yangi qiymat saqlanadi.



```csharp
namespace MyProgram
{
		static void Main(string[] args)
		{
				int x= 5;
				x = 20; // x dagi qiymat endi 20
				Console.WriteLine(x);
		}
}
```

O’zgaruvchilarni qurishda ingliz alifbosidagi harflar, raqamlar hamda tag chiziqdan foydalanishimiz mumkin \(m.u., myVariable, \_myVariable\).z

Eslatma: O’zgaruvchilarni nomlashda tushunarli va eslab qolish osonroq bo’lgan nomlardan foydalanish tavsiya etiladi.

