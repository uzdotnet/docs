---
description: Xakimbekov Doniyorbek
---

# Enum

**enum** - bu o’zgarmaslarni ifodalovchi maxsus “sinf” (qiymati **o’zgarmaydigan** yoki bir so’z bilan aytganda **read-only** o’zgaruvchilar).
**enum** ni yaratish uchun __enum__ kalit so’zidan foydalanamiz (interfeys yoki sinf o’rniga) va enum elementlari vergul bilan ajratib yoziladi: 

## **Misol uchun:**

```csharp
using System;
namespace NewApplication
{
    enum Level 
    {
      Low,
      Medium,
      High
    }
}
```

**enum** elementlariga nuqta sintaksisi bilan kirishingiz mumkin:
```csharp
Level myVar = Level.Medium;
Console.WriteLine(myVar);
```
{% hint style="info" %}
*enum* so’zi bu “*enumerations*” qisqartmasi bo’lib “maxsus sanab o’tilgan” degan ma’noni anglatadi.
{% endhint %}

Siz **enum** sinfidan Class ichida ham foydalana olasiz:
Misol uchun:
```csharp
classProgram{
enumLevel
{
Low,
Medium,
High
}
staticvoidMain(string[] args)
{
Level myVar =Level.Medium;
Console.WriteLine(myVar);
}}
```
Console:  `Medium`

**enum** qiymatlari:
Odatda, **enum** ning birinchi qiymati doim “0” dan boshlanadi va shu tariqa ikkinchisi “1” bo’lib davom etadi…

Elementdan butun qiymat olish uchun elementni *int* ga o’zgartirishimiz (convert) kerak:
Misol uchun
```csharp
enumMonths{
January,// 0
February,// 1
March,// 2
April,// 3
May,// 4
June,// 5
July// 6}
staticvoidMain(string[] args)
{
int myNum =(int)Months.April;
Console.WriteLine(myNum);
}
```
 Console: `3`
 
 
Shuningdek, siz o’zingizni enum qiymatlaringizni belgilashingiz ham mumkin va keyingi elementlar raqamni mos ravishda yangilaydi. Misol uchun:
```csharp
enumMonths{
January,// 0
February,// 1
March=6,// 6
April,// 7
May,// 8
June,// 9
July// 10}
staticvoidMain(string[] args)
{
int myNum =(int)Months.April;
Console.WriteLine(myNum);
}
```
Console: `7`

**enum** ko’pincha mos qiymatlarni tekshirish uchun switch ichida foydalaniladi. Misol uchun
```csharp
enumLevel{
Low,
Medium,
High}
staticvoidMain(string[] args){
Level myVar =Level.Medium;
switch(myVar)
{
caseLevel.Low:
Console.WriteLine("Low level");
break;
caseLevel.Medium:
Console.WriteLine("Medium level");
break;
caseLevel.High:
Console.WriteLine("High level");
break;
}}
```
Console:
`Medium level`

**enum** nima uchun va qachon ishlatiladi?

Oy kunlari, kunlar, ranglar, kartalar toʻplami va h.k. kabi oʻzgarmas qiymatlarga ega boʻlganingizda enum dan foydalaning.
