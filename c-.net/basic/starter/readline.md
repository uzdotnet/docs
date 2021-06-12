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
            //Yosh = int.Parse(Console.ReadLine());   
        }
    }
}
```

Convertatsiyani ikki xil usulini ikki sonning yig’indisi \(a+b\) da ko’rib chiqamiz.

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
            Console.WriteLine("Natija: " + (a + b));
        }
    }
} 
```

`Parse()` metodidan foydalanishni maslahat beramiz. Har bir tur \(int, long, double...\) ushbu metodni o'z ichiga oladi. Ya'ni string turidan o'sha joriy turga o'girish uchun foydalaniladi

{% hint style="info" %}
Ma'lumot o'rnida aytib o'tish lozimki, `Console` sinfi, ekrandan ma'lumot o'qib oladigan 3 ta metodni o'z ichiga oladi.`Read(), ReadLine(), ReadKey()` 
{% endhint %}

* ReadKey\(\) - Biror klavish bosilishini kutadi va uning kodini qaytaradi \(ConsoleKeyInfo turida\)
* Read\(\) - Bir belgi kiritilishi kutiladi va o'sha belgining ASCII kodi qaytariladi \(int turida\) 
* ReadLine\(\) - Satr kiritilishi kutiladi va string turida qaytaradi.

**Boshida ozroq tushinarsiz bo'lishligi mumkin, lekin tezda o'rganib ketasiz :\)**

