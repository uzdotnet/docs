---
description: Sobirjonov O'tkirbek
---

# Goto

Siz tuynuklar haqida eshitganmisiz? Dasturlashda ham xuddi shunday tuynuklar bor. Bu tuynukardan qanday foydalanamiz deysizmi!?

Avval tuynukni qayerga olib borishi uchun uning chiqish joyini Aniqlab olishimiz kerak.

![Aniqlab olamiz va kerakli joydan turib shu yerga hech qanday shartsiz o&#x2019;tish mumkin . Ya&#x2019;ni avvalgi belgilagan tuynuk uchida chiqib kelinadi.](../../../.gitbook/assets/photo_2020-11-14_22-02-55.jpg)

![Demak tushuncha oldingizmi Dasturda shuni bir ko&#x2019;rmaymizni nima dedingiz?](../../../.gitbook/assets/photo_2020-11-14_22-02-57.jpg)

## Demak boshladik. 1-misol

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            bool active = false;
            string say = "Salom";
            key:
            if (active)
            {
                Console.WriteLine(say);
            }
            if(active == false)
            {
                active = true;
                goto key;
            }
            Console.ReadKey();
        }
    }
}
```

Bu dasturda biz avval “key” nomli kalitni belgilab oldik.va kalit so’zdan keyin ‘:’ qo’yamiz. Dasturda shu qismga o’tib olishimiz uchun. 

Bu qismda dasturda active false qiymat olgan va 1- if shart bajarilmaydi.

Keyin 2-if shartini active qanoatlantirgani uchun  active  true qiymat oladi goto key buyrugi orqali key: deb boshlangan qismga o’tib ketadi. Va Consolega “Salom” deb chiqaradi. Va 2-if shartiga o’tadi bu qismda esa active true qiymatga ega bo’lgan edi. Va dastur bu safar 2-if shartini qanoatlantirmadi va dastur tugadi.

## 2-misol

```csharp
using System;
namespace GotoShartOperatori
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = 0;
            if (n == 0) {
                while (true)
                {
                    if (n == 10)
                    {
                        goto key;
                    }
                    n += 2;
                }
            }
            Console.WriteLine("Asosiy");
            while (true)
            {
                Console.WriteLine("Salom");
            }
            key:
            Console.WriteLine("Qalaysiz!");
            Console.ReadKey();
        }
    }
}
```

  
Bu dasturda n==0 shart tekshiriladi va while sikliga tushib qoladi va n=10 bo’lganida bu sikladan chiqib ketadi va xatto undan keyin turgan

```csharp
while (true)
    {
        Console.WriteLine("Salom");
    }
```

Cheksiz Siklga tushib qolgan key: bilan boshlanuvchi qismga o’tib ketadi!

Demak tushunganday bo’ldingizmi . Ya’ni siz dasturda ixtiyoriy Qismga o’tish uchun avval bir kalit so’z belgilab olasiz. Va dasturda ixtiyoriy qismda “goto”

So’zidan keyin siz o’ziz belgilagan kalit so’zni yozib qoyasiz. Dastur sizni kodlaringizni o’qiyotganda. “Goto” kalit so’zni o’qiganda siz yozgan kalit qismga o’tib ketadi. Demak tushunarli “Avval qayerligini aniqlab olmiz va shu joyga kalit so’z yozib ketamiz, va dasturni ixtiyoriy joyidan shu yerga goto deb so’zidan keyin kalitni yozib o’tib olasiz”!!!

