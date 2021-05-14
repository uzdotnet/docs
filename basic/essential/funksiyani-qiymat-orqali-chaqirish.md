---
description: Xolbek Xoliyorov
---

# Funksiyani qiymat orqali chaqirish

Funksiya larni qiymat orqali chaqirish nima biz bu tushunchani tushunish uchun hayotiy misol ko’rib o’tamiz. Tasavvur qilamiz biz muzqaymoq sotishni rejalashtirmoqdamiz. Biz shokoladli, mevali va qaymoqli muzqaymoq yaratmoqchimiz ,endi qilamiz har biri uchun alohida qurilma sotib olamizmi yoki ichiga soladigan maxsulotga qarab har xil musqaymoq chiqadigan bitta qurilma sotib olamizmi, albatta sizga ham ikkinchi variant maqul chunki bu biz uchun juda qulay va ortiqcha harajatdan ozod qiladi.

**Nega kerak?**

Endi funksiyaga qaytsak funksiyada ham deyarli shunday vaziyat. Ba’zan biz bitta funksiya orqali har xil qiymat olishga ehtiyoj sezamiz. Masalan ikki sondan kattasini topadigan funksiya yaratdik deylik uni biz int turidagi qiymat qaytaradigan qilib yaratdik , va float parametr kiritib ishlatganimizda bizga bu xatolik olib keldi nima endi float uchun alohida funksiya yozishimiz kerakmi , yo’q albatta funksiyani qiymatini chaqirish orqali bu muammoni yechamiz.

**Yaratish**

Demak bu yerda bir xil nomga ega va bir biridan parametr orqali \(ya'ni parametrlar soni yoki parametr turi\) farq qiluvchi funksiyalar yoziladi.

```csharp
int max(int a, int b)
{
    int max;
    if (a > b)
        max = a;
    else
        max = b;
    return max;
}
```

```csharp
float max(float a, float b)
{
    float max;
    if (a > b)
       max = a;
    else
       max = b;
    return max;
}
```

Ko’rib turganingizdek biz max funksiyasini chaqirsak qaysi ishlaydi degan savol tug’iladi albatta. Bu yerda kiritilgan parametr orqali funksiya chaqiriladi.

Misol uchun:

max\(1.5 , 9.6\) ko’rinishida funksiyani chaqirsak demak 2-funksiya chaqiriladi. max\(5 , 9\)  ko’rinishda chaqirganimizda esa 1-funksiya chaqiriladi.

**Dasturda Foydalanish**

Endi esa ushbu misolni Console oynada ko'rib chiqamiz:

```csharp
using System;
namespace function2
{
    class Program
    {  
        static void Main(string[] args)
        {
            Console.WriteLine(max(11, 5));
            Console.WriteLine(max(1.4f, 5.4f));

            Console.ReadKey();
        }
        static int max(int a, int b)
        {
            int max;
            if (a > b)
                max = a;
            else
                max = b;
            return max;
        }
        static float max(float a, float b)
        {
            float max;
            if (a > b)
                max = a;
            else
                max = b;
            return max;
        } 
    }
}

```

* &lt;&lt; output 
* 11
* 5.4

Xulosa qilib aytganda funksiyalarni qiymati orqali chaqirish imkoniyati bizga bitta ovqatning turli xil variantini taklif etatayotgan oshpazga o'xshaydi, hamma o'ziga ma'qulini tanlashi mumkin!

