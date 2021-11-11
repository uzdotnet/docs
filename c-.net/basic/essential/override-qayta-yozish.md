---
description: Sobirjonov O'tkirbek
---
# Override \(Qayta yozish\)

Siz OOP da methodlar bilan ishlayotganingizda sizga **Overloading** va **Overriding** degan so’zlarga duch kelishingiz mumkin. Bu ikki tushuncha odatda methodlar bilan o’z vazifasini amalga oshiradi. Overloading va Overriding polymorphism ni amalga oshirishnining keng tarqalgan usuli hisoblanadi. Biz hozir **Overriding (Qayta yozish)** haqida batafsil to’xtalib o’tamiz. 

## Overriding o’zi nima? 

Odatda C# da **Overriding** haqida gapirilganda, method **Overriding** nazarda tutiladi. Overriding bizga strukturani o’zgarishsiz ushlab qolgan holda, logikani o’zgartirish imkoniyatini beradi. 

## Overriding ishlatilmagandagi holat 

Shakllar class larini yaratamiz. Quyidagi kodda inheritance ishlatilgangan holda 3 ta class yaratdik. E’tibor bering hammasida Draw methodi bor. 
```csharp
public class Shape 
    { 
 
    } 
 
    public class Circle : Shape 
    { 
        public void Draw() 
        { 
            Console.WriteLine("Aylana chizildi"); 
        } 
    } 
 
    public class Triangle : Shape 
    { 
        public void Draw() 
        { 
            Console.WriteLine("Uchburchak chizildi"); 
        } 
    } 
 
    public class Rectangle : Shape 
    { 
        public void Draw() 
        { 
            Console.WriteLine("To'rtburchak chizildi"); 
        } 
    } 
```
Guvohi bo’lganingizdek “Draw” methodi ko’p bora qo’llanildi. Endi bir o’ylab ko’ring sizda 50 ta shakl classlarini yaratmoqchisiz, har birini chizish, bir biridan boshqacha bo’lsin. 2D va 3D da ham farq qiladi. U class larning har biriga “Draw” methodini e’lon qilib chiqishingiz qanchalar to’g’ri. Ya’ni siz chalkashib Drow yoki Drav deb yozib chalkashishingiz ham mumkin. Yoki birorta classda Draw methodi e’lon qilinmay qolib ketgan bo’lishi ham mumkin. Umumiy qilib aytganda ishonchilik yuqori emas. Bunga qanday yechim topish mumkin. 

## Overriding ishlatilgandagi holat 

Method overriding ni biz ikki xil usulda ko’rsatib o’tamiz 
1. Mavhum (Abstract) classlarni ichida abstract methodlar e’lon qilib, method override amalga oshirish mumkin. Abstract class larni ichida abstract methodlarni e’lon qilasiz va ushbu abstract class dan olingan avlod class o’zida ushbu abstract methodni override qilishi shart bo’lib qoladi.  

```csharp
using System;  
namespace ConsoleApp1 
{ 
    public abstract class Shape 
    { 
        public abstract void Draw(); 
    } 
 
    public class Circle : Shape 
    { 
        public override void Draw() 
        { 
            Console.WriteLine("Aylana chizildi"); 
        } 
    } 
 
    public class Triangle : Shape 
    { 
        public override void Draw() 
        { 
            Console.WriteLine("Uchburchak chizildi"); 
        } 
    } 
 
    public class Rectangle : Shape 
    { 
        public override void Draw() 
        { 
            Console.WriteLine("To'rtburchak chizildi"); 
        } 
    } 
 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            Circle circle = new Circle(); 
            circle.Draw(); 
            Triangle triangle = new Triangle(); 
            triangle.Draw(); 
            Rectangle rectangle = new Rectangle(); 
            rectangle.Draw(); 
        } 
    } 
} 
```
Natija : 
```
Aylana chizildi 
Uchburchak chizildi 
To'rtburchak chizildi 
```
Yuqoridagi Shape class ga e’tibor bering. Shakl (Shape) - bu mavhum narsa. Ya’ni shakl deganda sizning tasavvuringizda aynan bir shakl tasvirlanmaydi. Uchburchak, Aylana , Romb, To’rtburchak kabi shakllar tasvirlanishi mumkin. Biz kodni tejash va aniqlilikni oshirish uchun, avval Shape class ni abstract holatda yaratib oldik va qolgan classlarni unga avlod class qildik. 
  E’tibor bering! Shape class dagi struktura saqlanib qolyapti, avlod class da Draw nomli method bo’lishi va qayta yozilgan bo’lishini talab qiladi. Bu esa method nomini o’zgarishi e’lon qilinmay qolib ketishi kabi muammolarga yo’l qo’ymaydi.

2. Ixtiyoriy class ichida “virtual” kalit so’zi orqali method override amalga oshirish mumkin. Methodlar oldidan virtual kalit so’zi yozib ketiladi va ushbu virtual e’lon qilingan method tanasi ham yoziladi. Abstract methodlardan farqli o’laroq virtual methodlarda method tanasi ham bo’ladi. Sababi agar biror bir classda ushbu virtual method override qilinmasa, default holatda ushbu ota class dagi virtual method tanasidagi amallar bajariladi. 
```csharp
using System; 
namespace ConsoleApp1 
{ 
    public class Shape 
    { 
        public virtual void Draw() 
        { 
            Console.WriteLine("Shakl chizildi"); 
        } 
    } 
 
    public class Circle : Shape 
    { 
        public override void Draw() 
        { 
            Console.WriteLine("Aylana chizildi"); 
        } 
    } 
 
    public class Triangle : Shape 
    { 
        public override void Draw() 
        { 
            Console.WriteLine("Uchburchak chizildi"); 
        } 
    } 
 
    public class Rectangle : Shape 
    { 
    } 
 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            Circle circle = new Circle(); 
            circle.Draw(); 
            Triangle triangle = new Triangle(); 
            triangle.Draw(); 
            Rectangle rectangle = new Rectangle(); 
            rectangle.Draw(); 
        } 
    } 
} 
```
Natija :
```
Aylana chizildi 
Uchburchak chizildi 
Shakl chizildi 
```
E’tibor bering! To’rtburchak ( Rectangle ) class da Draw methodi override qilinmadi. Natijada ota class dagi Draw methodi ishga tushdi va “Shakl chizildi” so’zi yozildi. 
 
Method overriding tushunarli bo’ldi deb o’ylayman. Agar yana kengroq tushunmoqchi bo’lsangiz quyidagi kodni tahlil qiling. Tahlil qilish sizning fikrlashingizni sezilarli darjada oshiradi. 
```csharp 
using System;  
namespace ConsoleApp1 
{ 
    public abstract class Shape 
    { 
        public virtual void Draw() 
        { 
            Console.WriteLine("Shakl chizildi"); 
        } 
    } 
 
    public class Circle : Shape 
    { 
        private float _radius; 
        public Circle(float radius) 
        { 
            this._radius = radius; 
        } 
        public override void Draw() 
        { 
            Console.WriteLine($"Radiusi {_radius} ga teng bo'lgan aylana chizildi"); 
        } 
    } 
 
    public class Triangle : Shape 
    { 
        private float _a; 
        private float _b; 
        private float _c; 
 
        public Triangle(float a, float b, float c) 
        { 
            _a = a; 
            _b = b; 
            _c = c; 
        } 
 
        public override void Draw() 
        { 
            Console.WriteLine($"Tomonlari {_a} {_b} {_c} ga teng bo'lgan" + 
                $" uchburchak chizildi"); 
        } 
    } 
 
    public class Rectangle : Shape 
    { 
        private float _width; 
        private float _height; 
 
        public Rectangle(float width, float height) 
        { 
            _width = width; 
            _height = height; 
        } 
 
        public override void Draw() 
        { 
            Console.WriteLine($"Tomonlari {_width} {_height} ga teng bo'lgan" + 
                $" to'rtburchak chizildi"); 
        } 
    } 
 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            Circle circle = new Circle(5); 
            circle.Draw(); 
            Triangle triangle = new Triangle(3, 4, 5); 
            triangle.Draw(); 
            Rectangle rectangle = new Rectangle(4, 5); 
            rectangle.Draw(); 
        } 
    } 
} 
```
 
Natija :
```
Radiusi 5 ga teng bo'lgan aylana chizildi 
Tomonlari 3 4 5 ga teng bo'lgan uchburchak chizildi 
Tomonlari 4 5 ga teng bo'lgan to'rtburchak chizildi 
```
Yuqoridagi dasturlarimizda sezgan bo’lsangiz umumiy struktura o’zgarmadi va logika o’zgardi. Umumiy strukturada, “hamma shaklda Draw methodi bolishi kerak” degan shart bor edi.  Lekin Draw methodini tanasini uchburchak, to’rtburchak va boshqa shakl xususiyatlaridan kelib chiqqan xolda o’zgartirishingiz mumkin bo’ldi.
