---
description: Mamataliyev Diyorbek
---

# StreamWriter

Assalomu alaykum. C# da yozilgan dastur natijasini nafaqat Console oynasiga, biror matnli faylga ham yozib qo'yish imkoniyati mavjud. Buning uchun `System.IO` nomlar makoniga tegishli bo'lgan **StreamWriter** sinfidan foydalanish juda qulay. Ishonavering, buni o'rganish ham oson. Demak boshladik.

**StreamWriter** sinfidan foydalanish uchun eng avvalo `System.IO` nomlar makonini chaqiramiz. So'ng fayl nomini ko'rsatgan holda **StreamWriter** sinfidan obyekt olamiz. Masalan mana bunday:

```csharp
using System;
using System.IO;
class Program
  {
    static void Main(string[] args)
      {
         StreamWriter fayl1 = new StreamWriter("c://papka1/sonlar.txt");
      }
  }
```
Yuqoridagi kodimizda fayl1 - obyekt nomi, endi sonlar.txt fayliga shu nom bilan murojaat qilamiz. Qavs ichidagi nom esa sizga tanish, bu biz yozmoqchi bo'lgan faylning to'liq nomi. Bizning holatda fayl c diskda papka1 nomli papkada joylashgan.

{% hint style="info" %}
**ESLAB QOLING!** fayl nomi ko'rsatilayotganda mavjud bo'lmagan fayl ko'rsatilsa dastur o'zi ko'rsatilgan manzilda huddi shu nomda yangi fayl ochadi. 

Agar to'liq nomi aynan bir xil fayl ko'rsatilsa dastur ishlaganda fayl ichidagi yozuvlar to'la o'chirilib, yangitdan yozish boshlanadi. 

Agar fayl mavjud bo'lmagan papka ichida ko'rsatilsa, dastur ishga tushmaydi. Bu holatda kompilyator `System.IO.DirectoryNotFoundException` nomli xatolik oynasini ekranga chiqaradi
{% endhint %}

Shuningdek, fayl manzilini ko'rsatishda faqatgina fayl nomini yozish ham mumkin:
```csharp
StreamWriter fayl1 = new StreamWriter("sonlar.txt");
```
Bu holatda dasturingiz fayllari joylashgan **bin** nomli papka ichida yangi fayl ochiladi.

Yangi faylni ochdik, endi unga qanday yozamiz?
Sizga eng oson va to'g'ri yo'nalish: Avvalgi dasturlaringizda Console oynasiga ma'lumotni chop etish uchun foydalanilgan  `Console.Write`va `Console.WriteLine` funksiyalaridagi `Console` so'zi o'rniga **StreamWriter**dan olingan obyekt nomini yozsangiz bas. Misol tariqasida c diskning o'zida yangi fayl ochib, unga 1 dan 10 gacha sonlarni yozib ko'ramiz: 
```csharp
using System;
using System.IO;
class Program
{
  static void Main(string[] args)
  {
    StreamWriter new_file = new StreamWriter("c:/new file.txt");
    for (int i = 1; i < 11; i++)
        new_file.WriteLine(i);
    new_file.Close();
    Console.WriteLine("Sonlar faylga yozildi");
  }
}
```
{% hint style="info" %}
**BU MUHIM!** *StreamWriter* sinfi orqali ochilgan faylga yozib bo'lingach, albatta Close() funksiyasi orqali faylni yopish kerak. Aks holda fayldagi ma'lumotlar o'chib ketadi.
{% endhint %}
Yangi faylga matn yozilishini o'zingiz ko'rish uchun yuqoridagi dastur kodini ishlatib ko'ring.

Yana bir foydali ma'lumot: Faylli oqim(StreamWriter)dan foydalanib ma'lumotlarni chop etish matnli oqim(Console)dan ko'ra ancha tez ishlaydi. Bu sizga ko'p ma'lumotlar chop etish kerak bo'lgan masalalarda(berilgan oraliqdagi tub sonlarni topish kabi) ancha qo'l keladi.
