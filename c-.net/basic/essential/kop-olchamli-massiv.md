---
description: Mirzayev Bahodirjon
---

# Ko'p o'lchamli massiv
Massivlar **daraja** yoki **o'lchovlar soni** kabi tushuncha bilan tavsiflanadi.
Massivlar 1, 2, 3 yoki n o’lchamli bo’lishi mumkin.
Ko’p o’lchmali massivlarni 2 o’lchamli massivlar misolida ko’rib boramiz
Bir o’lchovli massivlarni bitta gorizontal qator kabi tasavvur qilishimiz mumkin, misol uchun:
```csharp
int[] nums1 = new int[] { 0, 1, 2, 3, 4};
```
Vizual ko’rinishda bu massiv:

![image](https://user-images.githubusercontent.com/81855769/123962446-e98ec080-d9ca-11eb-9420-48b1fba3373f.png)

Endi esa 2 o’lchamli massivga misol ko’ramiz:
```csharp
int[,] nums2 = { { 0, 1, 2 }, { 3, 4, 5 } };
```
Vizual ko’rinishda bu massiv:

![image](https://user-images.githubusercontent.com/81855769/123962584-0d520680-d9cb-11eb-9c42-00e565b36a2b.png)

Ko’p o’lchamli massivlarni e’lon qilish uchun kvadrat qavs ichiga vergul qo’yiladi, yani [,] ikki o’lchamli massiv, [,,] uch o’lchamli massiv va hokazo.
```csharp
int[,] arr2d; // ikki o’lchamli massiv
int[,,] arr3d; // uch o’lchamli massiv
int[,,,] arr4d; // to’rt o’lchamli massiv
int[,,,,] arr5d; // besh o’lchamli massiv
```
C# 32 o’lchovgacha bo’lgan massivlarni qo’llab quvvatlaydi. 
32 o’lchovgacha Karl, 32!
Odatda 1,2 yoki 3 o’lchamli massivlar ko’p ishlatiladi. 2 o’lchamli massivlar shuningdek matritsa deb ham ataladi.
Ko’p o’lchamli massivlarni ham bir o’lchamli massivlar kabi turli hil yo’l bilan e’lon qilishimiz mumkin:
```csharp
int[,] nums1;
int[,] nums2 = new int[2, 3];
int[,] nums3 = new int[2, 3] { { 0, 1, 2 }, { 3, 4, 5 } };
int[,] nums4 = new int[,] { { 0, 1, 2 }, { 3, 4, 5 } };
int[,] nums5 = new[,] { { 0, 1, 2 }, { 3, 4, 5 } };
int[,] nums6 = { { 0, 1, 2 }, { 3, 4, 5 } };
```
Ko’p o’lchamli massivlarning elementlarini massiv elon qilingan paytda:
```csharp
int[,] nums3 = new int[2, 3] { { 0, 1, 2 }, { 3, 4, 5 } };
```
kabi aniqlashimiz yoki sikl yordamida elon qilishimiz mumkin:
```csharp
int[,] myArr = new int[4, 5];
Random rand = new Random();

for (int i = 0; i < 4; i++)
{
    for (int j = 0; j < 5; j++)
    {
        myArr[i, j] = rand.Next(1, 30);
        Console.Write("{0}\t", myArr[i, j]);
    }
    Console.WriteLine();
}
```
Bu yerda Random sinfidan foydalanildi, bu haqda ko’proq malumot olish uchun quyidagi linkdan foydalanishingiz mumkin: link
Shuningdek massivning har bir elementini alohidadan aniqlashimiz mumkin:
```csharp
int[,] nums2 = new int[2, 3];
nums2[0, 0] = 0;
nums2[0, 1] = 1;
…
nums2[2, 3] = 5;
```
Ikki o’lchamli massivlarda [2, 3] masivning qatorlar va ustunlar sonini belgilaydi yani 2 qatorlar soni va 3 ustunlar soni, quyida bunga misol ko’rishingiz mumkin:
```csharp
int[,] nums3 = new int[2, 3] { { 0, 1, 2 }, { 3, 4, 5 } };
```
![image](https://user-images.githubusercontent.com/81855769/123963478-f06a0300-d9cb-11eb-83ee-fdd4a184bdb4.png)

Keling endi 2 o’lchamli massivga misol ko’ramiz.
Sinfxonada 3 qator partalar joylashgan, har bir qatorda 4tadan parta bor, bir partaga 1ta bola o’tiradi, oddiy hisob kitob bilan bu honada 3*4=12 ta parta borligi va 12ta o’quvchi sig’ishini hisoblay olamiz, endi masalaga o’tamiz, matematika fanidan imtihonda barcha o’quvchilar 3,4 yoki 5 baholarini olishdi, savol sinfning o’rtacha bahosi necha?
```csharp
using System;
    class Program
    {
        static void Main(string[] args)
        {
            //3 qator 4 ustunlik 2 o'lchamli massiv elon qilamiz
            int[,] myArr = new int[3, 4];

            Random rand = new Random();

            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    // random yordamida bolalarning baholarini aniqlaymiz
                    // (3,6) bu oraliqni bildiradi va 3,4,5 sonlarini o'z ichiga oladi
                    myArr[i, j] = rand.Next(3, 6); 
                    Console.Write("{0}\t", myArr[i, j]);
                }
                Console.WriteLine();
            }
            int sum = 0; //sinfning umumiy bahosi
            double average = 0.0D; //sinfnig o'rtacha bahosi
            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    sum += myArr[i, j];
                }
            }
            average = Convert.ToDouble(sum) / 12;
            Console.WriteLine($"Sinfning umumiy bahosi: {sum}");
            Console.WriteLine($"Sinfning o'rtacha bahosi: {average}");
        }
    }
```
Natija:

5       3       5       4

4       3       5       4

3       3       3       3

Sinfning umumiy bahosi: 45

Sinfning o'rtacha bahosi: 3,75

Massivlarning asosiy hususiyatlari:

O’lchovi(rank): massivning o’lchovini bildiradi

Massiv uzunligi(array lenght): massivning barcha elementlari soni

o'lchov uzunligi(dimension length): bir alohida o’lchovining uzunligi
