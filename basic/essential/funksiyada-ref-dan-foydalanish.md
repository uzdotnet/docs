---
description: Xolbek Xoliyorov
---

# Funksiyada Ref kalit so'zidan foydalanish

Biz shu vaqtgacha foydalangan funksiyalarda parametr sifatida berilgan o’zgaruvchilardan ma’lum natija olish uchun foydalandik, lekin biz hali parametrning qiymatini o’zgartirib ko’rmabmiz. Xo’sh parametrning qiymatini o’zgartirib nima qilamiz degan savol tug’ilishi tabiiy. Keling ikki sonni qiymatlarini o’zaro almashtiruvchi ‘swapp’ atalmish funksiya yaratib ko’ramiz.

Bu funksiyani ikki idish usuli \(ya’ni ikkita idishdagi mahsulotlarni o’zaro almashtirish uchun uchinchi idishdan foydalanish \) yordamida tayyorlaymiz.

```csharp
void swapp(int a, int b)
{
    int k = a;
    a = b;
    b = k;
}
```

Va buni dasturda ishlatamiz:

```csharp
using System;
namespace function3
{
    class Program
    {  
        static void Main(string[] args)
        {
            int a = 8, b = 5;
            swapp(a, b);

            Console.WriteLine(a+"  "+b);
            Console.ReadKey();
        }
        static void swapp(int a, int b)
        {
            int k = a;
            a = b;
            b = k;
        }
    }
}
```

&lt;&lt;output: 8    5

  
Afsuski natija biz kutgandek chiqmadi, ikki son o’z o’rnida chunki funksiya parametrlari standart holatda funksiya ichida o’zgarishlari funksiya tashqariga ta’sir qilmaydi. Bu muammoni hal qilish uchun bizga **ref** kalit so’zi yordamga keladi.

Biz yana yuqoridagi algoritm orqali funksiya yaratib olamiz faqat endigi safar ref yordamida.

```csharp
static void swapp(ref int a, ref int b)
{
    int k = a;
    a = b;
    b = k;
}
```

Va yangi funksyiani chaqirishda ham ref dan foydalanamiz.

```csharp
using System;
namespace function3
{
    class Program
    {  
        static void Main(string[] args)
        {
            int a = 8, b = 5;

            swapp(ref a,ref b);

            Console.WriteLine(a+"  "+b);
            Console.ReadKey();
        }
        static void swapp(ref int a,ref int b)
        {
            int k = a;
            a = b;
            b = k;
        }
    }
}
```

&lt;&lt;output : 5    8

Va nihoyat biz kutgan natija ikki sonning o'rni almashmoqda buni **ref** kalit so'zisiz yaratish juda qiyin bo'lardi.

### Xulosa

**ref** kalit so’zi qachonki biz funksiya parametri faqat kerakli natija uchun vosita sifatida emas balki parametrni o’zining qiymatini o’zgartirish ustuvor vazifa bo’lsa biz uchun juda zarur bo’ladi.

