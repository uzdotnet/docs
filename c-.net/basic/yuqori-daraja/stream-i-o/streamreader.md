---
description: Mamataliyev Diyorbek
---
# StreamReader

Biz matnli faylga ma'lumot yozish uchun **StreamWriter**dan foydalandik. Avvaldan yozilgan ma'lumotni o'qish uchun esa **StreamReader** sinfidan foydalanamiz. **StreamReader** sinfi **System.IO** nomlar makonida joylashgan. 

**StreamReader**dan foydalanish uchun ham avval biror fayl nomini ko'rsatgan holda obyekt olamiz:
```csharp
using System;
using System.IO;
class Program
{
    static void Main(string[] args)
    {
        StreamReader fayltxt = new StreamReader("d:/fayl.txt");
        StreamReader fayldoc = new StreamReader("d:/hujjatlar/hujjat.doc");
        StreamReader fayldocx = new StreamReader("d:/f.docx");
        StreamReader faylxlsx = new StreamReader("c:/f.xlsx");
        StreamReader faylpdf = new StreamReader("f.pdf");
    }
}
```
{% hint style="info" %}
**Yodda tuting!** **StreamReader**da ko'rsatilgan fayl avvaldan ko'rsatilgan manzilda aynan shu nomda mavjud bo'lishi kerak. Aks holda, dastur ishga tushmaydi. Mavjud bo'lmagan faylga murojaat qilinganda kompilyator `System.IO.FileNotFoundExeption` nomli xatolik oynasini ekranga chiqaradi.
Agar fayl biror papka ichida ko'rsatilgan bo'lsayu, bunday nomda papka mavjud bo'lmasa, `System.IO.DirectoryNotFoundExeption` xatoligi yuz beradi.
{% endhint %}
Agar disk nomini yozmay fayl nomining o'zini yozish orqali murojaat qilinsa, kompilyator bu faylni dastur joylashgan **bin** papkasi ichidan qidiradi.

Keling, endi kichik bir dastur tuzib ko'ramiz. Bizning dasturimiz fayldagi birinchi qatordagi ma'lumotlarni o'qib, Console oynasiga chiqarib bersin:
```csharp
using System;
using System.IO;
class Program
{
    static void Main(string[] args)
    {
        StreamReader f = new StreamReader("c:/f.txt");
        string matn = f.ReadLine();
        Console.WriteLine(matn);
        
        Console.ReadKey();
    }
}
```
Yuqoridagi kodni ishlatib ko'rishdan avval c diskda f.txt nomli fayl ochib, unga ixtiyoriy matn yozing va saqlang. Keyin dasturni ishlatganingizda u siz yozgan matnning birinchi qatorini Console ga chiqarganiga guvoh bo'lasiz.

Agar faqat bir qator matnni emas, fayldagi barcha ma'lumotni birdaniga o'qib olmoqchi bo'lsakchi? Buning uchun ReadLine() o'rniga ReadToEnd() metodidan foydalanamiz:
```csharp
using System;
using System.IO;
class Program
{
    static void Main(string[] args)
    {
        StreamReader f = new StreamReader("c:/f.txt");
        string matn = f.ReadToEnd();
        Console.WriteLine(matn);
        
        Console.ReadKey();
    }
}
```
Natijada f.txt faylidagi barcha ma'lumotlar Console oynasiga chiqariladi.
