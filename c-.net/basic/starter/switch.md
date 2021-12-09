---
description: Suxrob Xayitmurodov
---

# Switch

## Tanlash Operatori

Bu maqolamda men sizga tanlash operatorini tushuntirib beraman!

Tanlash operatori bizga bir nechta qiymatlardan, o’zgaruvchilarga to’g’ri keluvchi qiymatni tanlashda va uni ishga tushirishda ishlatiladi. Misol uchun hafta kunlarini raqamidan topish topshiriq sifatida berildi. Ularni bemalol topishimiz mumkin, lekin kompyuterga uni qanday tushuntiramiz? Buni bilish uchun ushbu maqolamni o’qib chiqishingizni tavsiya qilaman

### Sintaksis

```csharp
switch (<o'zgaruvchi>)
{
    case <o'zgarmas ifoda1> : <operator 1>; break;
    case <o'zgarmas ifoda2> : <operator 2>; break;
    ...
    case <o'zgarmas ifodaN> : <operator N>; break;
    default : operator N + 1; break;
}
```

**switch** kalit so’zini yozganimizdan so’ng qavslar ichiga biror-bir o’zgaruvchini kiritishimiz zarur shundan so’ng jingalak qavslar ochamiz va tanlash maqsadida **case** kalit so’zlarini kiritamiz va undan so’ng ifodamizni kiritamiz va uni nima vazifa bajarishini operatorlar yordamida yozishimiz kerak bo’ladi, bir nechta (siz xohlagancha) qiymatlar berilgandan so’ng o’zgaruvchiga to’g’ri kelmaydigan qiymat lar ham berilishi mumkin, bunday holatlarda **default** kalit so’zidan foydalangan holda operatorlarni kiritib tanlash operatorimizga yakun yasaymiz!!!

### Masala

\
Har bir hafta kunlarining raqamiga moslab ularni biriktirib qo’ying, aks holda “Bugun ahvollar joyidami og’ayni???” degan javob qaytarilsin.

```csharp
int n;

Console.Write("Hafta kunini kiriting = ");

n = int.Parse(Console.ReadLine());

switch (n)
{
    case 1: 
      Console.WriteLine("Dushanba"); break;
    case 2: 
      Console.WriteLine("Seshanba"); break;
    case 3: 
      Console.WriteLine("Chorshanba"); break;
    case 4: 
      Console.WriteLine("Payshanba"); break;
    case 5: 
      Console.WriteLine("Juma"); break;
    case 6: 
      Console.WriteLine("Shanba"); break;
    case 7: 
      Console.WriteLine("Yakshanba"); break;
    default: 
      Console.WriteLine("Bugun ahvollar joyidami og'ayni???"); 		  break;
}
```

**default** - Odatda case ichida e'lon qilinmagan ifodaga nisbatan qo'llaniladi. Ya'ni agarda case ichidagi ifoda uchun mos kelmasa, C# odatiy operatorlarni ishga tushiradi. (Xullas kiritilgan qiymatlardan bittasi ham to'g'ri kelmasa, default da berilgan qiymatni qabul qiladi)

**break** - Ma'lum bir ifodaga tegishli operatordan keyin qo'yiladigan kalit so'z. C# tili e'lon qilingan operatorni ishga tushirgandan so'ng, u ushbu so'zni o'qiydi va kodni to'xtatadi. Agarda u mavjud bo'lmasa, undan keyingi operatorni ham bajarib logik xatolikka yo'l qo'yishi mumkin!

{% hint style="info" %}
Boshqa dasturlash tillaridan farqli ularoq, C# tilida **default** operatoridan so'ng ham **break** ishlatishimiz lozim!!!
{% endhint %}
