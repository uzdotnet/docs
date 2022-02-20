---
description: Hamroliyev Ahmadjon
---
# Parametrlar

Biz ko’pincha metodlarda cheklangan miqdordagi argumentlardan foydalanamiz . Agar dasturdagi metodda argumentlar soni kopaysa kodning korinishini xiralashadi yani xunuklashadi. params kalit so’zi orqali biz cheksiz argumentlarni massiv korinishida kirgazishimiz va kodni ancha ixchamlashtirishimiz mumkin.
params Parametrli metodlarni chaqirganimizda , biz quyidagilarni kiritishimiz mumkin:

•	Massiv elementlari turiga oid argumentlarning vergul bilan ajratilgan ro'yxati:
```csharp
int yigindi = Sum(19, 9, 7, 17, 39, 47);
```

•	Belgilangan turdagi argumentlar massivi:
```csharp
object[] obj = new object[] { "hamroliyev", 'a', 19, 9, 12.8 };
//Add metodini chaqiramiz.
Add(obj);
```
•	Hech qanday argumentsiz. Hech qanday argument yubormasak, params ro'yxati uzunligi nolga teng boladi.
```csharp
Sum();
```

**params** kalit so’zi dasturchi metodda foydalaniladigan parametrlar soni haqida oldindan ma'lumotga ega bo'lmagan hollarda foydali bo'ladi. Metod konstruktorida params kalit sozidan faqat bir marta foydalanishimiz mumkin. params ga tegishli argumentdan keyin qoshimcha argument berish mumkin emas. 

params kalit so’zidan foydalanishga oddiy misol:
```csharp
using System;
namespace dot_net_uz
{
    class Program
    {
        // params parametrni o'z ichiga olgan metod
        public static int Sum(params int[] sonlarRoyxati)
        {
            int sum = 0;
            foreach (int i in sonlarRoyxati)
            {
                sum += i;
            }
            return sum;
        }
        static void Main(string[] args)
        {
            //Sum metodini chaqiramiz.
            int yigindi = Sum(19, 9, 7, 17, 39, 47);
            Console.WriteLine($"yigindi : {yigindi}");
            Console.ReadKey();
        }        
    }
}
```
Output:  **yigindi : 138**

Sizda "**params** kalit so'zidan foydalanmasdan ham metodlarda massivdan foydalanish mumkinku, **params** ni nima keragi bor?" degan savol tug'ilishi mumkin. Javob shunday: **params** kalit so'zi metoddan foydalanishni ancha qulaylashtiradi:
```csharp
using System;
namespace dot_net_uz
{
    class Program
    {
        // params parametrni o'z ichiga olgan metod
        public static int Sum(params int[] sonlarRoyxati)
        {
            int sum = 0;
            foreach (int i in sonlarRoyxati)
            {
                sum += i;
            }
            return sum;
        }
        static void Main(string[] args)
        {
            int a={19, 9, 7, 17, 39, 47};
            int yigindi = Sum(a);     // params ishlatmasdan ham metodni bu usulda chaqirish mumkin edi
            Console.WriteLine($"yigindi : {yigindi}");
            
            // paramsdan foydalangandagina metodni shunday chaqirish mumkin:
            Console.WriteLine($"yigindi : {Sum(19, 9, 7, 17, 39, 47)}");
            
            // Agar paramsdan foydalanmagan bo'lsangiz kodning bu qismida xatolik yuzaga keladi,
            // paramsdan foydalansangiz metodni shu holatda ham chaqirish mumkin
            Console.WriteLine(Sum());
            
            Console.ReadKey();
        }        
    }
}
```

Object turidan va paramsdan foydalanish metodni har qanday turdagi va har qanday miqdordagi qabul qila olishiga imkon beradi:
```csharp
using System;
namespace dot_net_uz
{
    class Program
    {
        // params parametrni o'z ichiga olgan metod
        // object turidagi parametrlardan foydalanilgan funksiya
        public static void Print(params object[] royxat)
        {
            for (int i = 0; i < royxat.Length; i++)
            {
                // Natijalarni chop etish
                Console.WriteLine(royxat[i]);
            }
        }
        static void Main(string[] args)
        {
            object[] obj = new object[] { "hamroliyev", 'a', 19, 9, 12.8 };
            Console.WriteLine("1-usul:");
            //Print metodini chaqiramiz.
            Print(obj);
            Console.WriteLine();
            
            Console.WriteLine("2-usul:");
            //Print metodini chaqiramiz.
            Print(19,"dot-net",20,"Hamroliyev");
            
            Console.WriteLine("3-usul:");
            Print();
            Console.ReadKey();
        }        
    }
}
```
Output:
```
1-usul:
hamroliyev
a
19
9
12,8

2-usul:
19
dot-net
20
Hamroliyev
```
