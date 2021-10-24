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

Agar to'liq nomi aynan bir xil fayl ko'rsatilsa dastur ishlagach fayl ichidagi yozuvlar to'la o'chirilib, yangitdan yozish boshlanadi. 

Agar fayl mavjud bo'lmagan papka ichida ko'rsatilsa, dastur ishga tushmaydi. Bu holatda kompilyator `System.IO.DirectoryNotFoundException` nomli xatolik oynasini ekranga chiqaradi
{% endhint %}
