---
description: Sariboyev Jasur
---

# MemoryStream

Xo'sh do'stlar mana o'tgan darslarda turli xildagi fayllarga ma'lumotlarni yozishni, o'qishni va saqlashni ko'rdingiz, keling endi bizdagi ma'lumotlarni fayllarga emas balki kompyuterimiz xotirasiga saqlashni ko'rib chiqamiz.

MemoryStream ham "Stream" sinf(class)laridan biri bo'lib, bu sinf(class) ham System.IO nomlar makoni(namespace)da joylashgan.
Uning koddagi ko'rinishi(syntax) MemoryStream ni  undan obyekt olib ishlatamiz :
```csharp
MemoryStream memStream = new MemoryStream();
```
Nomidan ham ko'rinib turibdiki, u to'g'ridan-to'g'ri xotiradagi ma'lumotlar bilan shug'ullanadi, ya'ni ma'lumotlarimizni kompyuterning tezkor xotirasi(RAM)da vaqtinchalik saqlab turadi. Uning ustunligi tezkorligidadir. Agar biz ma'lumotlarga ko'plab murojaat qiladigan bo'lsak MemoryStream dan foydalanish afzaldir chunki, MemoryStreamdagi baytlar diskda emas, balki xotirada saqlanadi.
Keling bir misolda ko'rib chiqamiz.  O'zimiz bilgan StreamWriter orqali oddiy matn fayliga "Salom, Dunyo !!!" deb yozamiz va uning barcha baytlarni byte array orqali o'qiymiz. Keyin biz ushbu saqlangan baytlar bilan MemoryStream yaratamiz va MemoryStream dan barcha satrlarni o'qiy oladigan o'zimiz bilgan StreamReader yaratamiz. 
```csharp
using System;
using System.IO;
using System.Text;

class MemStream
{
    static void Main()
    {
        StreamWriter writer = new StreamWriter("biror.txt");
        writer.WriteLine("Salom, Dunyo !!!");
        writer.Close();
        
        byte[] bytesAll = File.ReadAllBytes("biror.txt");

        MemoryStream memoryStream = new MemoryStream(bytesAll);

        StreamReader stream = new StreamReader(memoryStream);  
     
                string line;
                while ((line = stream.ReadLine()) != null)
                    Console.WriteLine(line);
            stream.Close();
        
        memoryStream.Close();
    }
}
```
Output:`Salom, Dunyo !!!`
	
Har bir stream ni tugatish uchun "close" ning o'rniga "using" kalit so'zi bilan blokdan foydalanishingiz mumkin (1=2).

1. 
```csharp
MemoryStream memoryStream = new MemoryStream();
...... 

memoryStream.Close();
```
2. 
```csharp
using(MemoryStream memoryStream = new MemoryStream())
{
......
}
```
{% hint style="info" %}
MUHIM! MemoryStream dan har doim ham foydalanish tavsiya berilmaydi, chunki :
1. Ma'lumotlar hajmi katta bo'lsa RAM ga sig'may qolishi mumkin;
2. MemoryStreamda saqlagan ma'lumotlar dastur yopilganda yoki kompyuter o'chiib yoqilishi kabi holatlarda yo'qolib qolishi ya'ni xotiradan o'chib ketishi mumkin.
{% endhint %}
