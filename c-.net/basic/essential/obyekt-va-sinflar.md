---
description: Sobirjonov O'tkirbek
---

# Obyekt va Class lar

Dasturlash olamida juda ko’p yoki to’g’rirog’i eng ko’p ishlatiladigan so’zlar ushbu ikki so’zdir. Ya’ni class va object. Agar siz dasturlashni endi o’rganayotgan bo’lsangiz va class va object nima ekanligini tushunmasdan keyingi mavzularga o’tmoqchi bo’lsangiz adashasiz. Siz bu mavzuni yaxshi o’rganishingiz kerak, to’g’rirog’i juda yaxshi o’rganishingiz kerak. Ushbu mavzuda object va class larni nima ekanligi va ularning farqini ko’rsatib o’tilgan. 

Demak boshladik!

1.	Avvalo object va classlarni nima ekanligini bilib olaylik. 
Tasavvur qiling, siz g’isht zavodidasiz yoki o’zingiz (qo’lbola) g’isht quymoqchisiz.Ushbu holatda sizning g’isht quyuvchi qolipingiz bu class va siz quygan g’ishtlar esa objectlar deb qarashingiz mumkin.

![Klass (class) ](https://user-images.githubusercontent.com/91861166/139823443-1e74b177-74c8-48be-a2ae-8d3b6653a684.png)

![Obyekt (object) ](https://user-images.githubusercontent.com/91861166/139823902-4b5bfcb8-6fde-40ce-b2f1-52a37a2ac824.png)

Menimcha tasavvur qildingiz deb o’ylayman.
1. Siz ma’lum maqsad asosida ishlaysiz. Bu misolda esa sizning maqsadingiz nima? Albatta g’isht quyish. Demak siz g’isht quyishingizdan avval uni qolipini tayyorlab olishingiz kerak bo’ladi. Chunki qolip bo’lmasa g’ishtlar ham bo’lmaydi. Huddi shuningdek, **Class**larsiz **Object**lar ham bo’lmaydi. 
2. Siz g’isht qolipni o’zingiz qilishingiz yoki tayyor yasalganini olishingiz mumkin. Tayyorini olishingizdan maqsad nima? Albatta u juda aniq o’lchamli va to’g’ri yasalgan bo’ladi. Demak siz **Class**larni yaratishingizdan avval yaxshilab o’ylab yozishingiz kerak bo’ladi. Chunki sizning g’isht qolipingiz qiyshiq va o’lchamlarida adashilgan bo’lsa siz quygan barcha g’ishtlar qiyshiq va nostandart bo’ladi.

Keling ushbu misolimizni dasturlashda ko’rib chiqamiz

![image](https://user-images.githubusercontent.com/91861166/139824677-1628e00c-83a5-498f-a04d-87b90798c609.png)

```csharp
public class BrikMold
{
  // O'lchov birliklari mm larda
  public double width = 112.5;
  public double length = 225;
  public double height = 75;
}
```

Public so’ziga hozircha uncha e’tibor bermang, uni keyingi mavzularda, Acces Modifiers mavzusida o’rganib olasiz.
Class so’zi doimo yozilishi kerak chunki biz class yaratayotganimizni bildirib turadi.
BrikMold (inglizcha, G’ishtQolip) – class nomi, ya’ni biz G’ishtqolipi **class**ini yozayotganimizni bildiradi. Siz buni boshqa nom bilan ham yozishingiz mumkin.

```csharp
public double width = 112.5;
public double length = 225;
public double height = 75;
```

Yuqoridagilar esa g’ishtlarning o’lchamlari, ya’ni biz yasaydigan barcha g’ishtlar shu standard asosida yaratilsin degan ma’noni bildiradi.

Bu classdan foydalanishni ko’rib chiqamiz.
```csharp
using System;
namespace ConsoleApp1
{
  classProgram
  {
    static void Main(string[] args)
    {
    BrikMold brik = new BrikMold();
    Console.WriteLine(brik.width);
    Console.WriteLine(brik.height);
    Console.WriteLine(brik.length);
    Console.ReadKey();
    }
  }
  public class BrikMold
   {
    // O'lchov birliklari mm larda
    public double width = 112.5;
    public double length = 225;
    public double height = 75;
    }
}
```

Natija :
```
112.5
75
225
```

Demak bu mavzu siz uchun tushunarli bo’ldi deb o’ylayman. Quyidagi namunalar orqali ko’proq yana o’rganishingiz mumkin. Bir-biridan farqlang, ma’nosini va ishlatilish usulini tushunishga harakat qiling.
1.
```csharp	
using System;
namespace ConsoleApp1
{
  classProgram
  {
    staticvoid Main(string[] args)
    {
      BrikMold brik = new BrikMold();
      Console.WriteLine($"O'chamlari : " +
      $"{brik.width}mm , " +
      $"{brik.height}mm, " +
      $"{brik.length} mm ");
      Console.ReadKey();
    }
  }
  public class BrikMold
  {
    // O'lchov birliklari mm larda
    public double width = 112.5;
    public double length = 225;
    public double height = 75;
  }
}
```

Natija :
`O'chamlari : 112.5mm , 75mm, 225 mm`


```csharp
using System;
namespace ConsoleApp1
{
  classProgram
  {
    staticvoid Main(string[] args)
    {
      GreenBrikMol dbrik = new GreenBrikMold();
      Console.WriteLine($"O'chamlari : " +
      $"{brik.width}mm , " +
      $"{brik.height}mm, " +
      $"{brik.length} mm " );
      Console.WriteLine($"Rangi : {brik.color}");
      Console.ReadKey();
     }
   }
   public class GreenBrikMold
   {
      // O'lchov birliklari mm larda
      public double width = 112.5;
      public double length = 225;
      public double height = 75;
      public string color = "Green";
    }
}
```
Natija :
```
O'chamlari : 112.5mm , 75mm, 225 mm
Rangi : Green
```
