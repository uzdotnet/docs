---
description: Nodirbek Abdulaxadov
---

# Anonim metodlar

_Yuqoridagi [Func](https://docs.dot-net.uz/c-.net/basic/yuqori-daraja/delegatlar/func-delegati), [Action](https://docs.dot-net.uz/c-.net/basic/yuqori-daraja/delegatlar/action-delegati) va [Predicate](https://docs.dot-net.uz/c-.net/basic/yuqori-daraja/delegatlar/predicate-delegati) mavzularida ushbu delegatlarning anonim metod bilan qo'llanishini ko'rdik, lekin anonim metod qanday ekanligi haqida endi  gaplashamiz._😊

Nomidan ko'rinib turibdiki, **Anonim metod** - bu ismsiz metod. U metod bo'lsa, delegatlar mavzusida nima qilyapti degan savol tug'ilishi mumkin.  Buning sababi shundaki, **Anonim metod** delegat tushunchasi bilan chambarchas bog'liq va delegatlarni chaqirish uchun ishlatiladi.

{% hint style="info" %}
Qisqacha qilib aytganda metodlarni nima deb nomlashni bilmasdan nom qidirgan paytingizda: _"keling endi shu metodni benom qoldiramiz"_ deb yordamga keladi.
{% endhint %}

**Anonim metod** umumiy ko'rinishi:

![](../../../../.gitbook/assets/anonim11.png)

{% hint style="success" %}
**Anonim metoddan foydalanish uchun quyidagi qadamlarni bajarish yetarli:**
* **Delegat e'lon qilish**
* **Delegatdan obyekt hosil qilish**
* **_delegate_ kalit so'zi yordamida hosil qilingan obyektga mos nomsiz metod yozish**(_bunda metod parametrlari delegat parametrlariga mos bo'lishi kerak_)
* **delegatdan foydalanish**
{% endhint %}

Misol:

```csharp
using System;

namespace Delegates
{
    class Program
    {
        //delegat e'lon qilish
        public delegate void Print(string s);
        static void Main(string[] args)
        {
            //delegatdan obyekt hosil qilib unga anonim metod tayinlash
            Print print;
            print = delegate (string str)
            {
                Console.WriteLine($"Hello {str}");
            };

            //delegatni chaqirish
            print("DOT-NET.UZ");

            Console.ReadKey();
        }
    }
}

//Chiquvchi:
//  Hello DOT-NET.UZ
```

**Anonim metod**lar ichida global o'zgaruvchilardan ham foydalanish mumkin. Quyidagi misolda biror sonning ko'rsatilgan darajasini hisoblovchi dastur ko'rsatilgan(anonim metod ichida 'a' global holatda, 'n' esa 'N' nomi bilan parametr sifatida ishlatilgan):

```csharp
using System;

namespace Delegates
{
    class Program
    {
        //delegat e'lon qilish
        public delegate int Degree(int i);
        static void Main(string[] args)
        {
            //o'zgaruvchilarni kiritish
            Console.Write("Son kiriting: ");
            int a = int.Parse(Console.ReadLine());
            Console.Write("Darajani kiriting: ");
            int n = int.Parse(Console.ReadLine());

            //delegatdan obyekt hosil qilib unga anonim metod tayinlash
            Degree d = delegate (int N)
            {
                return (int)Math.Pow(a, N);
            };

            //delegatni chaqirish
            Console.WriteLine($"\n{a} sonining {n}-darajasi: {d(n)}");

            Console.ReadKey();
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/anonim2.png)

{% hint style="danger" %}
**Anonim metod cheklovlari:**
* **Anonim metod** goto, break va continue o'tish operatorlarini o'z ichiga olmaydi
* **Anonim metod** out va ref parametrlarini ishlata olmaydi
* **Anonim metod** operatorning chap tomonida ishlatilmaydi
{% endhint %}

**delegate** operatoridan foydalanishda parametrlarni tashlab ketish ham mumkin. Bunday holatda siz ixtiyoriy parametrlarni yuborish imkoniyatiga ega bo'lasiz:

```csharp
Action SayHello = delegate { Console.WriteLine("Hello!"); };
    SayHello();

Action<int, double, bool, string> introduce = delegate { Console.WriteLine("This method can be called with any parameters!"); };
    introduce(42, 2.7, 2>4, "Hello");
```

C# 9.0 dan boshlab siz **Anonim metod**lani static holatda e'lon qilishingiz mumkin:

```csharp
Func<int, int, double> degree = static delegate (int a, int b)
    {
        return Math.Pow(a, b);
    };
degree(2, 3);
```

Shuningdek **Anonim metod**lar Event Handler sifatida ham ishlatilishi mumkin:

```csharp
saveButton.Click += delegate(Object o, EventArgs e)
{ 
    //some code for saving
    System.Windows.Forms.MessageBox.Show("Save Successfully!"); 
};
```
