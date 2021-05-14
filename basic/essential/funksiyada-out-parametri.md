---
description: Xolbek Xoliyorov
---

# Funksiyada Out parametri

Biz shu vaqtgacha funksiya bilan ishlash davomida bir nechta parametrlar orqali biror qiymatni topish va undan foydalanishni ko’rdik. Lekin biz bitta funksiya bir emas, bir nechta qiymatni aniqlashi kerak bo’lib qolsa nima qilamiz? Misol uchun kvadratning tomoni yordamida uning yuzasini, peremetrini va ichki chizilgan aylana radiusini hisoblaydigan funksiya yaratishimiz kerak. Buni odatiy holda har biri uchun alohida funksiya yozib chiqishimiz kerak. Lekin **out** yordamida buning hammasi oson bo'lib qoladi!!!

### E'lon qilish

Ming marta maqolani o'qigandan ko'ra bir marta dastur kodini ko'rgan yaxshi!:\)\)\)

```csharp
void kvadrat(float a,out float  yuza, out float peremetr, out float radius)
{
    yuza = a * a;
    peremetr = 4 * a;
    radius = a / 2;
}
```

Demak out parametrli o’zgaruvchi oldidan ‘out’ kalit so’zi ishlatiladi.

Yuqoridagi misolda funksiyani chaqirgandan keyin yuza , peremetr va radiusning qiymatidan foydanishimiz mumkin va ular oldindan qiymatga ega bo’lishi shart emas!

### Foydalanish

Endi esa konsol oynada ushbu funksiyani chaqirib ko'ramiz.

```csharp
using System;
namespace function4
{
    class Program
    {  
       static void Main(string[] args)
        {
            float a = 5;
            kvadrad(a, out float yuza1, out float peremetr1, out float radius1);

            Console.WriteLine(yuza1+"  "+peremetr1+" "+radius1);
            Console.ReadKey();
        }
        static void kvadrad(float a,out float  yuza, out float peremetr, out float radius)
        {
            yuza = a * a;
            peremetr = 4 * a;
            radius = a / 2;
        }
    }
}
```

&lt;&lt;output 25    20    2.5

* Ko'rib turganingizdek out parametrlar qiymatga ega emas
* Qiymatga ega bo'lgan o'zgaruvchilarni ham **out** bilan chaqirishimiz mumkin
* **out** parametrli o'zgaruvchi funksiya tashqarisida e'lon qilinmagan, lekin tashqarida foydalanish mumkin
* **out** parametr sifatida oldin funksiya tashqarisida e'lon qilingan o'zgaruvchilardan foydalanishimiz mumkin.

{% hint style="info" %}
Eslatma:

**Funksiyada out parametrli o'zgaruvchi e'lon qilib foydalanmaslik xatolikka olib keladi.**
{% endhint %}

### Xulosa

Funksiyaning out parametri orqali e'lon qilingan o’zgaruvchini funksiya ichida o’zgartirishimiz mumkin va funksiya tashqarisida ham bu o’zgarish saqlanib qoladi. Funksiyada odatiy e'lon qilingan o’zgaruvchilarda esa bu hodisa ro’y bermaydi.

Va shuningdek bu imkoniyatlar **ref** kalit so’zida ham mavjud, lekin unda o’zgaruvchining dastlabki qiymati aniq berilishi shart.



_E'tiboringiz uchun raxmat!!!_

