---
description: Nodirbek Abdulaxadov
---

# Delegatlar

_Agar funksiyani parametr sifatida uzatishni xohlasak nima bo'ladi?
Qanday qilib C# callback funksiyalari yoki event larni boshqaradi?_

Javob: **Delegat**

**Delegat** - bu metod imzosini belgilaydigan ma'lumot turi. Siz boshqa ma'lumotlar turi kabi delegatning o'zgaruvchilarini yaratishingiz mumkin va ular yordamida delegat bilan bir xil parametrga ega har qanday metodga murojaat qilishingiz mumkin.

Delegatlar bilan ishlashda uchta bosqich mavjud:

1. Delegatni e'lon qiling

2. Kerakli metodni o'rnating

3. Delegatni chaqiring

Delegat quyida ko'rsatilgandek , **_delegate_** kalit so'zdan keyin funksiya imzosi yordamida e'lon qilinishi mumkin:

```csharp
[ruxsat modifikatori] delegate [qaytariluvchi tip] [delegat nomi]([parameterlar])
```

Quyida **MyDelegate** deb nomlangan delegat e'lon qilingan:

```csharp
public delegate void MyDelegate(string msg);
```
Yuqorida biz void tipidagi va string parametrli MyDelegate delegatini e'lon qildik. Delegat sinfdan tashqarida yoki sinf ichida e'lon qilinishi mumkin. Quyidagi misolda, bu sinfdan tashqarida e'lon qilamiz.

```csharp
using System;
namespace Delegate
{
    class Program
    {
        // delegat e'lon qilish
        public delegate void MyDelegate(string msg); 
        
        public static void Main(string[] args)
        {
            // delegat obyektiga metod tayinlash
            MyDelegate del1 = new MyDelegate(MethodA);

            // delegat obyektiga metod tayinlash
            MyDelegate del2 = MethodA;
        
            //lyambda ifodadan foydalanish
            MyDelegate del3 = (string msg) => Console.WriteLine(msg);
            
            Console.ReadKey();
        }
        
        //metodni e'lon qilish
        static void MethodA(string message)
        {
            Console.WriteLine(message);
        }
    }
}
```

Kerakli metodni o'rnatgandan so'ng, Invoke() metodi yordamida yoki () operator yordamida delegat chaqirilishi mumkin.

```csharp
del.Invoke("Hello World!");
// or 
del("Hello World!");
```

Quyida delegat qo'llanishining to'liq namunasi keltirilgan:

```csharp
using System;
namespace Delegate
{
    public delegate void MyDelegate(string msg);

    class Program
    {
        static void Main(string[] args)
        {
            MyDelegate del = ClassA.MethodA;
            del("Hello World");

            del = ClassB.MethodB;
            del("Hello World");

            del = (string msg) => Console.WriteLine("lambda ifoda ishlatilishi: " + msg);
            del("Hello World");

            Console.ReadKey();
        }
    }
    class ClassA
    {
        public static void MethodA(string message)
        {
            Console.WriteLine("ClassA.MethodA() metodi chaqirildi: " + message);
        }
    }
    class ClassB
    {
        public static void MethodB(string message)
        {
            Console.WriteLine("ClassB.MethodB() metodi chaqirildi: " + message);
        }
    }
}
```
**Natija:**

![](../../../../.gitbook/assets/delegat1.jpg)

**...Information not finished yet!...**
