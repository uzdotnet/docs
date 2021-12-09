---
description: Sobirjonov O'tkirbek
---

# static

Static Class va static funksiyalar

Siz C# da dastur yozar ekansiz, **static** kalit so’ziga duch kelishingiz aniq. Ushbu darsda **static** kalit so’zi _class_lar yaratishda qanday ahamiyatga ega ekanligini ko’rib chiqamiz.

_Class_larning oldidan **static** so’zi yozilgan bo’lsa, demak bu _class_ - **static** _class_ degan ma’noni bildiradi. **Static** _class_lar bizga object olmasdan uning maydon, method va property laridan foydalanish imkoniyatini beradi.

`Console.WriteLine(Math.PI);`

Ushbu code dagi **Math.PI**ga e’tibor bering. **Math** class – bu **static** qilib yozib chiqilgan _class_dir.\
Static qilib siz birorta _class_ yaratsangiz undan object olmasdan `ClassName.PropertyName` yoki `ClassName.MethodName` ko’rinishida ishlatish imkoniyati bo’ladi (Class nomi “.” dan keyin ishlatmoqchi bo’lgan maydon va method nomini yozib ishlatib keta olasiz).

**static** _class_ lar qanday yoziladi? Quyidagi namunada **Math** _class_idagi **PI** ni ishlatishni qo’lda yozib chiqsak qanday ko’rinishda bo’lishini ko’rib chiqamiz.

```csharp
using System;  
namespace ConsoleApp1 
{ 
  class Program 
  { 
    static void Main(string[] args) 
    { 
        Console.WriteLine(Numbers.PI); 
    } 
  } 
 
  public static class Numbers 
  { 
    private static double _pi = 3.14; 
 
    public static double PI 
    {  
        get
        { 
            return _pi; 
        }  
    } 
  } 
} 
```

Demak, **static** _class_larni yaratish uchun class nomi va method nomlari oldidan **static** kalit so’zini ishlatgan holatda yarata olar ekanmiz. Static classlarda object olib bo’lmaydi, chunki bu xususiyat object olmasdan ishlatish uchun qo’shilgan. Static classlar va static methodlar haqida quyidagi namudan xulosa olishingiz mumkin.

```csharp
using System;  
namespace ConsoleApp1 
{ 
  class Program 
  { 
    static void Main(string[] args) 
    { 
        int number1 = 2; 
        int number2 = 5; 
        int number3 = 6; 
        int number4 = 7; 
        Console.WriteLine(PrimeNumbers.IsPrime(number1)); 
        Console.WriteLine(PrimeNumbers.IsPrime(number2)); 
        Console.WriteLine(PrimeNumbers.IsPrime(number3)); 
        Console.WriteLine(PrimeNumbers.IsPrime(number4)); 
        Console.ReadKey(); 
      } 
  } 
 
  public static class PrimeNumbers 
  { 
    public static bool IsPrime(int number) 
    { 
        bool isPrime = true; 
        if (number < 2) return false; 
        for (int i = 2; i < Math.Sqrt(number); i++) 
        { 
            if(number % i == 0) 
            { 
                isPrime = false; 
                break; 
            } 
        } 
        return isPrime; 
     } 
  } 
} 
```

Natija :

```
True 
True 
False 
True
```
