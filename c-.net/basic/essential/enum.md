---
description: Xakimbekov Doniyorbek, Hikmatullayev Saidrahmatulloh
---

# Enum

**enum** - bu o’zgarmaslarni ifodalovchi maxsus “sinf” (qiymati **o’zgarmaydigan** yoki bir so’z bilan aytganda **read-only** o’zgaruvchilar).
**enum** ni yaratish uchun __enum__ kalit so’zidan foydalanamiz (interfeys yoki sinf o’rniga) va enum elementlari vergul bilan ajratib yoziladi: 

**Misol uchun:**

```csharp
using System;
namespace NewApplication
{
    enum Level 
    {
      Low,
      Medium,
      High
    }
}
```

**enum** elementlariga nuqta sintaksisi bilan kirishingiz mumkin:
```csharp
Level myVar = Level.Medium;
Console.WriteLine(myVar);
```
{% hint style="info" %}
*enum* so’zi bu “*enumerations*” qisqartmasi bo’lib “maxsus sanab o’tilgan” degan ma’noni anglatadi.
{% endhint %}

Siz **enum** kalit so'zidan Class ichida ham foydalana olasiz:
Misol uchun:
```csharp
classProgram
{
  enumLevel
  {
    Low,
    Medium,
    High
  }
static void Main(string[] args)
{
  Level myVar =Level.Medium;
  Console.WriteLine(myVar);
}
```
Console:  `Medium`

**enum** qiymatlari:
Odatda, **enum** ning birinchi qiymati doim “0” dan boshlanadi va shu tariqa ikkinchisi “1” bo’lib davom etadi…

Elementdan butun qiymat olish uchun elementni *int* ga o’zgartirishimiz (convert) kerak:
Misol uchun
```csharp
enumMonths
{
  January,// 0
  February,// 1
  March,// 2
  April,// 3
  May,// 4
  June,// 5
  July// 6}
static void Main(string[] args)
{
  int myNum =(int)Months.April;
  Console.WriteLine(myNum);
}
```
 Console: `3`
 
 
Shuningdek, siz o’zingizni enum qiymatlaringizni belgilashingiz ham mumkin va keyingi elementlar raqamni mos ravishda yangilaydi. Misol uchun:
```csharp
enumMonths
{
  January,// 0
  February,// 1
  March=6,// 6
  April,// 7
  May,// 8
  June,// 9
  July// 10}
staticvoidMain(string[] args)
{
  int myNum =(int)Months.April;
  Console.WriteLine(myNum);
}
```
Console: `7`

**enum** ko’pincha mos qiymatlarni tekshirish uchun switch ichida foydalaniladi. Misol uchun
```csharp
enumLevel
{
  Low,
  Medium,
  High
}
static void Main(string[] args){
Level myVar =Level.Medium;
switch(myVar)
{
  caseLevel.Low:
  Console.WriteLine("Low level");
  break;
  caseLevel.Medium:
  Console.WriteLine("Medium level");
  break;
  caseLevel.High:
  Console.WriteLine("High level");
  break;
}
```
Console:
`Medium level`

**enum** nima uchun va qachon ishlatiladi?

Oy kunlari, kunlar, ranglar, kartalar toʻplami va h.k. kabi oʻzgarmas qiymatlarga ega boʻlganingizda enum dan foydalaning.


**Enum** ni tushinish uchun quyidagi misolda ko'raylik
Misol: Bizga hafta kunlari (1,2…7)gacha raqamlar bilan raqamlab berilgan 
bo'lsin  bizga hafta raqami berilsa hafta kunini chiqaradigan dastur qilishimiz kerak. 
Bu masalani  birinchi biz bilgan switch case da hal  qilib ko'raylik.

```csharp
using System;
namespace switch_case
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hafta raqamini kiriting :");
            int n=int.Parse(Console.ReadLine());
            switch(n)
            {
                case 1:Console.WriteLine($"Dushanba");break;
                case 2:Console.WriteLine($"Seshanba");break;
                case 3:Console.WriteLine($"Chorshanba");break;
                case 4:Console.WriteLine($"Payshanba");break;
                case 5:Console.WriteLine($"Juma");break;
                case 6:Console.WriteLine($"Shanba");break;
                case 7:Console.WriteLine($"Yakshanba");break;
            }
        }
    }
}
```

Endi bu masalani **enum** bilan hal qilib ko'ramiz

```csharp
using System;
namespace enum1
{
    class Program
    {
        public enum Kun
        {
            Dushanba=1, Seshanba=2, Chorshanba=3,Payshanba=4, Juma=5, Shanba=6, Yakshanba=7
        };
        static void Main()
        {
            Console.WriteLine("Kun raqamini kiriting =>");
            
            int n= int.Parse(Console.ReadLine());
            
            System.Console.WriteLine(Enum.GetName(typeof(Kun),n));
            
        }
    }
}
```

**Enum** orqali kodni uzunligi ancha qisqardi.

Quyidagi hollarda **enum** elementlarga avtomatik qiymat beradi.

```csharp
using System;
namespace _enum
{
    class Program
    {
        public enum ranglar
        {
            qizil,  //0
            sariq,  //1
            yashil = 4,
            kok,    //5
            qora    //6
        };
        static void Main(string[] args)
        {
            string[] rang = Enum.GetNames(typeof(ranglar));
            foreach(var r in rang)  // bu yerda ranglar nomi chop etilmoqda
            {
                Console.WriteLine(r);
            }
            int[] values =(int[]) Enum.GetValues(typeof(ranglar));
            foreach(var m in values) //bu yerda esa qiymati
            {
                Console.WriteLine(m);
            }
        }
    }
}
```

Qora oynada quyidagicha natija chiqadi.
```
qizil
sariq
yashil
kok
qora
0
1
4
5
6
```
Biz **enum** dan foydalanib avtomobillar narxi chiqaruvchi dastur tuzib ko'rayik.

```csharp
using System;
namespace car
{
    class Program
    {
        enum mashinalar
        {
            Nexia3 = 87000000,
            Gentira = 100000000,
            Cobalt = 97000000,
            Spark=76000000,
            Damas=66000000,
            Malibu=275000000,
            Kaptiva=260000000,
        }
        static void Main(string[] args)
        {
            Console.WriteLine(mashinalar.Malibu+"ning narxi");
            int narxi = (int)mashinalar.Malibu;
            Console.WriteLine(narxi + " so'm");
        }
    }
}
```
Qora oynadagi natija:
```
Malibuning narxi
275000000 so'm
```

**Enum** elementlarini qiymatiga qarab jop etish.
```csharp
using System;
namespace dasturlash
{
    class Program
    {
        enum dasturlash_tillari
        {
            Csharp=1,
            C,          //2
            Cplasplas,  //3
            Go,         //4
            Python,     //5
            Java,       //6
            JavaScript, //7
            Kotlin,      //8        
        }
        static void Main(string[] args)
        {
            int i = 1, j = 4, k = 5, f = 8;
            dasturlash_tillari a1, b1, c1, d1;
            a1 = (dasturlash_tillari)i;
            b1 = (dasturlash_tillari)j;
            c1 = (dasturlash_tillari)k;
            d1 = (dasturlash_tillari)f;
            Console.WriteLine(a1);
            Console.WriteLine(b1);
            Console.WriteLine(c1);
            Console.WriteLine(d1);
        }
    }
}
```

Qora oynadagi natija
```
Csharp
Go
Python
Kotlin
```
