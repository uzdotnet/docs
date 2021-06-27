---
description: Xondamir Abduxoshimov
---

# Singleton

**SIngleton** dizayn patterni bilan tanishish orqali Creational DIzayn Patternlar oilasiga yakun yasaymiz.

Singleton dasturlash olamida keng tarqalgan dizayn patternlardan biridir. Pattern bizga, dastur davomida bitta obyektni global olib yurishga imkon yaratadi. Ya'ni, siz har safar singleton sinfiga murojaat qilganingizda u doimo bitta obyektni qaytaradi. Oddiyroq qilib, bitta obyektga ega bo'lgan sinf deyishimiz ham mumkin.

Singletonni implement qilishni bir necha ko'rsatmalari mavjud. Quyida ulardan ba'zilarini keltirishimiz mumkin:

* Parametrga ega bo'lmagan, private konstruktorni yaratish orqali
* Sealed sinf orqali
* Yagona yaratilgan obyektga yo'l ko'rsatuvchi statik o'zgaruvchi orqali

Asosiy 6 ta implement qilish usuli mavjud:

1. No Thread-Safe Singleton
2. Thread-Safety Singleton
3. Double-Check Locking oqali Thread-Safety Singleton hosil qilish
4. Lazy&lt;T&gt; type orqali
5. To'liq lazy instatsiyasi orqali
6. Hech qanday bloklash va lazy instantatsiyasiz Thread-Safe Singleton implementatsiyasi 

Maqolamizda No Thread-Safe Singleton implementatsiyasi qanday amalga oshirilishini ko'rib o'tamiz.

### No Thread - Safe implementatsiyasi

```csharp
using System;

namespace SingletonDesignPattern
{
    class Singleton
    {
        private Singleton() { }
        
        private static Singleton _instance;
        
        public static Singleton ObyektOlish()
        {
            if (_instance == null)
                _instance = new Singleton();
        
            return _instance;
        }
    }
    
    class Program
    {
        static void Main(string[] args)
        {
            Singleton birinchiObyekt = Singleton.ObyektOlish();
        
            Singleton ikkinchiObyekt = Singleton.ObyektOlish();
        
            if (birinchiObyekt.Equals(ikkinchiObyekt))
                Console.WriteLine("Akasi, ikalasi bitta obyekt");
        
            else
                Console.WriteLine("Singleton ishlashida kamchilik sezildi");
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2878%29.png)

{% hint style="info" %}
Ushbu implementatsiya usuli multithreading bilan ishlashda xatoliklarga olib kelishi mumkin. Ushbu holatda boshqa holatlar yaxshiroq yechim bo'ladi oladi.
{% endhint %}

Ko'rib tuganingizdek ushbu Singleton paterndan foydalanishni tushunish unchalik qiyin emas. Umid qilamanki, siz allaqachon anglab yetdingiz. Qolgan holatlarni esa, o'zingizga havola etamiz.

