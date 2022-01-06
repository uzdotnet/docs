---
description: Mamataliyev Diyorbek
---
# Random

Tasodifiy sonlar generatori haqida eshitganmisiz? Eshitmagan bo’lsangiz aytaman, tasodifiy sonlar generatori dastur tomonidan biror oraliqdagi tasodifiy tanlangan (oldindan aniq bo’lmagan) sonni olish uchun ishlatiladi. Biz o’rganayotgan C# dasturlash tilida buning uchun **Random** sinfidan foydalaniladi.

Buning bizga nima keragi bor? 

Misol uchun, siz ko’proq sonlar ustida biror amal bajaruvchi dastur yozdingiz. Dasturingiz to’g’ri ishlayotganini tekshirish uchun ishga tushirganingizda, shuncha sonni yozib chiqishingiz shart emas. Shunchaki bitta massiv olib, **Random** sinfidan foydalanib uni tasodifiy sonlar bilan osongina to’ldirish mumkin. Dastur har safar ishga tushirilganida har xil sonlar tanlab olinadi. Yoki ekranning turli joylarida paydo bo’luvchi shakllar koordinatasini Random orqali olib, takrorlanmas animatsiyalar hosil qilishingiz mumkin va hokazo, boshqa ko’p maqsadlarda ishlatishingiz mumkin.

Endi esa bu sinf metodlaridan qanday foydalanishni ko’rib chiqamiz.

Random sinfi `System` standart kutubxonasida joylashgan. Bu sinfdan foydalanish uchun avval undan obyekt olishimiz kerak :
```csharp
Random rand = new Random();
```

So'ngra quyidagi metodlardan foydalanishimiz mumkin:

•	**Random.Next()** metodi [0;  2 147 483 647) oraliqdan integer tipidagi tasodifiy sonni tanlab beradi. 

•	**Random.Next(int a)** – [0; a) oraliqdagi tasodifiy butun sonni olish uchun ishlatiladi.

•	**Random.Next(int a,int b)** – [a;b) oraliqdagi tasodifiy butun sonni olib  beradi. Int tipida qiymat qaytaradi.

•	**Random.NextBytes(byte [] b)** – byte tipidagi b massivni tasodifiy sonlar bilan to’ldirib beradi.

•	**Random.NextDouble()** – [0;1) oraliqdagi tasodifiy haqiqiy sonni tanlab olish uchun ishlatiladi.

Metodlarni kodda quyidagicha ishlatish mumkin:

```csharp
using System;
class dotnetuz
{
    public static void Main()
    {

        Random tasodifiy = new Random();

        Console.WriteLine("Integer tipidagi 5 ta tasodifiy sonlar:");
        for (int i = 0; i < 5; i++)
        {
            Console.Write(tasodifiy.Next() + " ");
        }
        Console.WriteLine();
        Console.WriteLine();


        Console.WriteLine("0 va 40 orasidagi 7 ta tasodifiy sonlar:");
        for (int i = 0; i < 7; i++)
        {
            Console.Write(tasodifiy.Next(41) + " ");
        }
        Console.WriteLine();
        Console.WriteLine();

        Console.WriteLine("40 va 90 orasidagi 8 ta tasodifiy sonlar:");
        for (int i = 0; i < 8; i++)
        {
            Console.Write(tasodifiy.Next(40, 91) + " ");
        }
        Console.WriteLine();
        Console.WriteLine();

        byte[] massiv = new byte[10];
        tasodifiy.NextBytes(massiv);
        Console.WriteLine("byte tipidagi 10 ta tasodifiy sonlar:");
        foreach (byte item in massiv)
        {
            Console.Write(item + " ");
        }
        Console.WriteLine();
        Console.WriteLine();

        Console.WriteLine("0 va 1 orasidagi 5 ta tasodifiy haqiqiy sonlar:");
        for (int i = 0; i < 5; i++)
        {
            Console.Write(tasodifiy.NextDouble() + " ");
        }
        Console.WriteLine();
        Console.WriteLine();

        Console.WriteLine("0 va 15 orasidagi 5 ta tasodifiy haqiqiy sonni olish ham mumkin:");
        for (int i = 0; i < 5; i++)
        {
            Console.Write(tasodifiy.NextDouble() * 15 + " ");
        }

        Console.ReadKey();
    }
}
```
Output:
```
Integer tipidagi 5 ta tasodifiy sonlar:
19935471 1272063124 1570733439 1326559547 24648986

0 va 40 orasidagi 7 ta tasodifiy sonlar:
25 23 17 6 34 28 25

40 va 90 orasidagi 8 ta tasodifiy sonlar:
66 41 43 61 89 86 83 82

byte tipidagi 10 ta tasodifiy sonlar:
255 115 183 165 216 28 140 222 198 193

0 va 1 orasidagi 5 ta tasodifiy haqiqiy sonlar:
0,151187449764082 0,112327319622192 0,3266392398284 0,509324506628013 0,437839470541961

0 va 15 orasidagi 5 ta tasodifiy haqiqiy sonni olish ham mumkin:
5,39333248994934 2,85994078398679 9,05856904995561 6,59124690647761 11,7725050923287
```

Dastur kodini ishlatib ko’rganingizda sizdagi natija yuqoridagidan farq qilishi tabiiy, dasturni qayta-qayta ishlatganingizda har safar avvalgisidan farqli natijalar olasiz.

Mavzuyimiz hali tugamadi, chunki **Random** sinfining yana bitta konstruktori bor. Sinfdan quyidagicha obyekt olishimiz ham mumkin:
```csharp
Random rand = new Random(int n);
```

Xo’sh, bu konstruktorni avvalgisidan qanday farqi bor?

Agar ikkinchi konstruktor orqali obyekt olgan bo’lsangiz, chegaralar va n ning bir xil qiymatlarida olinadigan natijalar ham aynan bir xil bo’ladi. Dasturni har safar qayta ishga tushirilganda bir xil ketma-ketlik hosil bo’ladi. Konstruktordagi n ning qiymati yoki chegaralar  o’zgartirilsagina natija o’zgaradi. Masalan, quyidagi kodni o’z kompilyatoringizda ishlatib ko’ring:
```csharp
using System;
class Test
{
    public static void Main()
    {

        Random tasodifiy = new Random(2);
        byte[] massiv = new byte[10];
        tasodifiy.NextBytes(massiv);
        foreach (byte item in massiv)
        {
            Console.Write(item + " ");
        }
        
        Console.ReadKey();
    }
}
```

Menda natija quyidagicha bo’ldi:
```
113 147 198 149 36 185 227 111 124 56
```
Shubhasiz, sizda ham shunday natija hosil bo’ladi va dasturni qayta-qayta ishlatsangiz ham natija o’zgarmaydi. Konstruktorda kiritilgan n soni ketma-ketlikning boshlang’ich nuqtasi bo’lib, uning turli qiymatlarida ketma-ketlik turlicha bo’ladi. Xulosa qilib aytadigan bo’lsak, ikkinchi konstruktordan foydalanganingizda ***Tasodiflar  tasodifan bo’lmaydi  ).***
