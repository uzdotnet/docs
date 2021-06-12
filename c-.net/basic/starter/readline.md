---
description: Ra'no Norpo'latova
---

# ReadLine

`Console.WriteLine()` malumotlarni chiqarish, chop etish \(output\) uchun foydalaniladi. Endi belgilar oqimini o'qish uchun \(input\) `Console.ReadLine()` dan foydalanamiz. `ReadLine()` metodi \(funksiyasi\) `Console` sinfi ga tegishli.

```csharp
using System;

namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            string Ism;
            Console.WriteLine("Ismingizni kiriting: ");
            //string tipida qiymat qaytadi
            Ism = Console.ReadLine();
        }
    }
}
```

`Console.ReadLine()` bilan ma'lumotlarni faqat string tipida olishimiz mumkin. Masalan int tipida son kiritmoqchi bo'lsak uni string tipidan int tipiga \(o'zgartirishimiz\) konvertatsiya qilishimiz kerak. Bunda `Convert` sinfining `ToInt32()` metodi  yoki `int` sinfining `Parse()`  metodidan foydalanashimiz mumkin!

```csharp
using System;

namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            string Ism;
            int Yosh;
            Console.Write("Ismingizni kiriting: ");
            //string tipidagi qiymat qaytadi
            Ism = Console.ReadLine();

            Console.Write("Yoshingizni kiriting: ");
            //string turidan int turiga aylantiriladi 
            Yosh = Convert.ToInt32(Console.ReadLine());
            //int.Parse yordamida convertatasiya qilamiz
            // Yosh = int.Parse(Console.ReadLine());   
        }
    }
}
```

Convertatsiyani ikki xil usulini ikki sonning yig’indisi \(a+b\)da ko’rib chiqamiz.

```csharp
namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            int a, b;
            a = Convert.ToInt32(Console.ReadLine());
            b = int.Parse(Console.ReadLine());
            Console.WriteLine("Natija: "+(a+b));
        }
    }
}
```

Sonlar ketma-ketligini Consoledan o’qib olishimiz uchun uni string tipida massiv \(massiv haqidagi ma’lumotlarni keyingi bo’limlarimizdan bilib olishingiz mumkin\) shaklida e’lon qilamiz. Massiv ele-mentlarini biror belgi bilan ajratish uchun Split\(\) funksiyasidan foydalanamiz.

```csharp
using System;

namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            string[] son = Console.ReadLine().Split(' ');
            Console.WriteLine(int.Parse(son[0]) + int.Parse(son[1]));
        }
    }
}
```

Split\(\) funksiyasi massiv elemetlarini istalgan char \(belgi\) bilan ajratib beradi\(bu yerda probel bilan ajratilgan\). Massivning har bir elementini int tipiga o’zgartirib amalni bajaramiz.

