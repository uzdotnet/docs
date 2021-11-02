---
description: Hamroliyev Ahmadjon
---
# try/catch

C# da istisno holat sintaksisi.[try/catch]  

Istisno holat faqat dastur bajarilish vaqtida sodir bo'ladi. Dastur ishlab turgan vaqtdagi kelib chiqadigan xatoliklarni C# ning istisno holatlarni qayta ishlash tizimidan foydalanib boshqariladigan va tizimli qayta ishlash mumkin.   
Istisno holatlarni qayta ishlashning asosiy afzalligi shundan iboratki, bu sizga kodning ko'p qismini avtomatlashtirishga imkon beradi, ilgari har qanday yirik dasturga xatolarni boshqarish uchun qo'lda kiritilishi kerak edi.  
Shunday qilib, agar dastur dasturlash tilida istisnolardan foydalanmasdan yozilgan bo'lsa, unda xato kodlarini qaytaradigan metodlar muvaffaqiyatsiz bajariladi va siz ularni har bir chaqiruvda ularni qo'lda tekshirishga majbur bolasiz.  

**System.Exception** namespace 
C# dagi barcha istisno holatlar malum bir sinflarni ichida saqlanadi. Barcha istisno holatlar joylashgan sinflar **System** namespace(nomlar fazosi)iga kiruvchi C# da o'rnatilgan **Exception** qismidan kelib chiqadi. Shuning uchun barcha istisnolar **System.Exception**  namespacening qism sinflariga tegishli.  
Istisno holatining eng muhim **Exception**  qism sinfi **System.Exception** namespacega  tegishlidir. C # tizimida ishlash vaqtida kelib chiqadigan barcha istisnolar aynan shu sinfdan kelib chiqadi.  
C # dastur tuzuvchilarga ushbu vaziyatlarni boshqarish imkoniyatini beradi.  
Buning uchun C # da **try…catch…finally** konstruktsiyasi mo'ljallangan  
• **try** bloki – dastur bajarishi lozim bo’lgan kodni inkapsulyatsiya qiladi. Agar ushbu jarayonda xatolik yoki mumkin bo’lmagan hol yuzaga kelsa, xatolik sodir bo’lganda bajariladigan blok chaqiriladi.  
• **сatch** bloki – try blokidan so’ng kelib, xatolik yuz berganda bajariladigan kodni ishga tushiradi.  
• **finally** bloki – doimo bajariluvchi kod, yani try blokidan keyin yoki catch blokidan keyin bajariladi. Ushbu blok  har doim bo’lishi shart emas. Undan  goto operatori orqali chiqish mumkin emas.   
Quyida istisnolardan foydalanish uchun **try/catch/finally** bloklarni aniqlashning umumiy shakli keltirilgan: 
````csahrp
try  
{  
   // Bu yerda tekshiriluvchi kod turadi   
        // Ushbu kod xatolikni hosil qilishi mumkin  
}  
catch (xatolik turi1)  
{  
   // try blokida xatolik yuzaga kelganda   
         // ushbu kod bajariladi   
}  
catch (xatolik turi2)  
{  
   // try blokida xatolik yuzaga kelganda   
         // ushbu kod bajariladi   
}  
  
finally  
{  
       // Ushbu blokdagi kod yuqoridagi bloklar  
      // bajarilgandan so’ng bajariladi   
}  
````

 1-Misol.   
```csharp
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace dotnetuz 
{ 
  class Program 
  { 
    static void Main(string[] args) 
    { 
      double s, a, x; 
      try 
      { 
          Console.Write("a="); 
          a = Double.Parse(Console.ReadLine()); Console.Write("x="); 
          x = Double.Parse(Console.ReadLine()); 
 
          s = (a * a + Math.Exp(2 * a - 6)) / (x * (a + Math.Pow(2, x))); 
          Console.WriteLine("s=" + s); 
      } 
      catch (SystemException ex) 
      { 
          Console.WriteLine("Ifodaning qiymatini hisoblashda" + ex.Message + " xatolik yuz berdi"); 
      } 
      finally 
      { 
          Console.WriteLine("Ifodaning qiymatini hisoblash tugadi"); 
      } 
      Console.ReadLine(); 
    } 
  } 
} 
```

2-Misol.   
```csharp
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace dotnetuz 
{ 
  class Program 
  { 
    static void Main(string[] args) 
    { 
      double[] a = new double[10]; 
      double x, s = 0; 
      Console.Write("x=");
      try 
      { 
          x = Double.Parse(Console.ReadLine()); for (int i = 0; i < 10; i++) 
          { 
              a[i] = Double.Parse(Console.ReadLine()); if (x + i != 0) { s += a[i] / (x + i); } else throw new DivideByZeroException(); 
          } 
          Console.WriteLine("s=" + s); 
      } 
      catch (DivideByZeroException) 
      { 
          Console.WriteLine("Ifodani hisoblashda 0 ga bo'lish uchradi"); 
      } 
      catch (IndexOutOfRangeException) 
      { 
          Console.WriteLine("Massivning indeksi chegaradan tashqariga chiqdi"); 
      } 
      catch (SystemException ex) 
      { 
          Console.WriteLine("Xatolik:" + ex.Message +" yuz berdi"); 
      } 
      finally 
      { 
          Console.WriteLine("Dastur tugadi"); 
      } 
      Console.ReadLine(); 
 
    } 
  } 
}
```
  
![](https://user-images.githubusercontent.com/91861166/139919188-62576945-59c8-44fa-9b13-52386bf257e3.png)

![](https://user-images.githubusercontent.com/91861166/139919605-a4062425-824e-46a8-97ad-95cbb055b0a6.png)

![](https://user-images.githubusercontent.com/91861166/139919631-389eefec-49d6-4fb4-837a-9d62f4bc4c89.png)


![](https://user-images.githubusercontent.com/91861166/139919661-0cd0eddb-da5f-48b5-8d35-735bf400ed61.png)

