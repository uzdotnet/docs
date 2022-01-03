---
description: Ravshan Sodiqov
---
# Polimorfizm

Navbatdagi darsimiz ob’ektga yo’naltirilgan dasturlashning yana bir asosiy tushunchalaridan biri polimorfizm haqida. Polimorfizm odatda inkapsulyatsiya va vorislikdan keyin OOP ning uchinchi ustuni deyiladi. *Polimorfizm* yunoncha so’z bo’lib, “ko’p shaklli” degan ma’noni anglatadi va uning ikki xil ko’rinishi mavjud:

1.	**Statik polimorfizm**.  Ushbu tur *kompilyatsiya vaqti polimorfizmi (Compile Time Polymorphism)* deb ham yuritiladi. Chunki u qaysi metod yoki funksiyani chaqirishni kompilyatsiya vaqtida aniqlashtirib oladi va mos keladigan metod yoki funksiya topilmasa xatolik qaytariladi. 

Quyida “Algebra” sinfida bir xil nomga ega ikkita “Add” metodi mavjud va bu metodlar faqat parametrlari bilan farqlangan. 1 – “Add” metodining vazifasi 2 ta butun sonni qabul qilib, ularning yig’indisini qaytarish. 2 – “Add” metodining vazifasi 3 ta butun sonni qabul qilib, ularning yig’indisini qaytarish.
```csharp
class Algebra
{
  public int Add(int a, int b)
  {
    return a + b;
  }
  public int Add(int a, int b, int c)
  {
    return a + b + c;
  }
}
```
Keling endi dastur qanday ishlashini yaxshiroq tushunish uchun, “Algebra” sinfining  “Add” metodidan ikki xil ko’rinishidan ham foydalanib ko’ramiz:
```csharp
class Algebra
    {
        public int Add(int a, int b)
        {
            return a + b;
        }

        public int Add(int a, int b, int c)
        {
            return a + b + c;
        }
    }
    
    class Program
    {   
        static void Main(string[] args)
        {
            Algebra algebra = new Algebra();
            Console.WriteLine(algebra.Add(3, 8)); //output: 11
            Console.WriteLine(algebra.Add(2, 3, 8)); //output: 13
            Console.ReadKey();
        }    
    }
```
Biz sinf metodiga algebra.Add(3, 8) shaklida murojaat qildik va kompilyastiya jarayoni boshlangandan keyin dastur ikkita parametrli metodga ya’ni 1 – “Add” metodiga murojaat qildi. (Mustaqil tarzda s.Add(2, 3, 5) holatini o’rganib chiqing). Biz statik polimorfizmda bir metodni sinfni o’zida qayta aniqladik va qaysi metod ishlashi kerak ekanligi kompilyatsiya vaqtida aniq bo’ldi.  

2.	**Dinamik polimorfizm**. Runtime polimorfizmi yoki kech ulanish polimorfizmi deb ham atash mumkin. Polimorfizmning ushbu turida statik polimorfizmdan farqli tarzda bir sinfga tegishli metodlarni ushbu sinfdan voris oluvchi boshqa sinflarda qayta aniqlaymiz. Bu nima degani ? 
Misol tariqasida real bir voqeani qaraymiz. Geometrik shakl deganimizda uchuburchak, to’rtburchak, piramida va yana boshqa shakllar ko’z oldimizdan o’tadi. Lekin aynan bir shaklni tasavvur qila olmaymiz. Uchburchak deganimizda esa aksincha. Ushbu holat quyidagicha:
```csharp
class Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men shakl chizaman");
        }
    }

    class Uchburchak : Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men uchburchak chizaman");
        }
    }

    class Aylana : Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men aylana chizaman");
        }
    }
```

Yuqoridagi holatda “Shakl” sinfi ajdod sinf va unda Chizish() metodi mavjud, “Aylana” va “Uchburchak” sinflari esa uning voris sinflari va  Chizish() metodini esa ularda qayta yozdik. 
```csharp
    class Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men shakl chizaman");
        }
    }

    class Uchburchak : Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men uchburchak chizaman");
        }
    }

    class Aylana : Shakl
    {
        public void Chizish()
        {
            Console.WriteLine("Men aylana chizaman");
        }
    }

    class Program
    {   
        static void Main(string[] args)
        {
            //konstruktorlar e'loni
            Shakl shakl = new Shakl();
            Shakl uchburchak = new Uchburchak();
            Shakl aylana = new Aylana();

            //Metodni chaqirish
            shakl.Chizish();
            uchburchak.Chizish();
            aylana.Chizish();

            Console.ReadKey();
        }    
    }
```
Natija qanday bo’ladi ?

![Natija](https://user-images.githubusercontent.com/91861166/147952367-3db0cf1b-190f-4f8a-ac65-d0f81500296f.png)

Nega natija biz o’ylagandek chiqmadi ?  Biz yuqorida ikkita xatoga yo’l qo’ydik. 

  **1 – xato:**  Chizish() metodini ajdod sinfda, ya’ni, Shakl sinfida qayta yozish imkoniyati bor ekanligini aytmadik. (virtual so’zi bilan hal qilamiz) 
  
  **2 – xato :**  Chizish() metodini voris sinflarda qayta yozayotganimizni ham aytib o’tmadik. (override so’zi bilan hal qilamiz)

Dasturga muammolarimizni hal qiluvchi kalit so’zlarni qo’shamiz:
```csharp
namespace PolymorphismDemoApp
{
    class Shakl
    {
        public virtual void Chizish()
        {
            Console.WriteLine("Men shakl chizaman");
        }
    }

    class Uchburchak : Shakl
    {
        public override void Chizish()
        {
            Console.WriteLine("Men uchburchak chizaman");
        }
    }

    class Aylana : Shakl
    {
        public override void Chizish()
        {
            Console.WriteLine("Men aylana chizaman");
        }
    }

    class Program
    {   
        static void Main(string[] args)
        {
            //konstruktorlar e'loni
            Shakl shakl = new Shakl();
            Shakl uchburchak = new Uchburchak();
            Shakl aylana = new Aylana();

            //Metodni chaqirish
            shakl.Chizish();
            uchburchak.Chizish();
            aylana.Chizish();

            Console.ReadKey();
        }    
    }
}
```
Xatolarimizni hal qila oldikmi ? 

![Natija](https://user-images.githubusercontent.com/91861166/147952466-5b1185c3-4d90-4517-98f0-56a12420189a.png)

Xayriyat, endi natija biz xohlagan ko’rinishda ! 

### Abstraksiya olamiga sayohat 
Yuqorida biz geometrik shakl deganda aynan bir shakl ko’z oldimizga kelishini va uni chizish mumkin emasligini tushunib yetdik. Demak, “Shakl” sinfi mavhum (abstract) sinf va uning “Chizish” metodi ham mavhum (abstract). Voris sinflarda esa bu metodning qiladigan ishi tayin.
```csharp
namespace PolymorphismDemoApp
{
    abstract class Shakl
    {
        public abstract void Chizish();
    }

    class Uchburchak : Shakl
    {
        public override void Chizish()
        {
            Console.WriteLine("Uchburchak chizaman");
        }
    }

    class Aylana : Shakl
    {
        public override void Chizish()
        {
            Console.WriteLine("Aylana chizaman");
        }
    }

    class Program
    {   
        static void Main(string[] args)
        {
            //konstruktorlar e'loni
            //Shakl shakl = new Shakl(); endi Shakl sinfining kostruktrini yaratib bo'lmaydi 
            Shakl uchburchak = new Uchburchak();
            Shakl aylana = new Aylana();

            //Metodni chaqirish
            uchburchak.Chizish();
            aylana.Chizish();

            Console.ReadKey();
        }    
    }
}
```
{% hint style="info" %}
OOP ni amalda yaxshi qo’llashni istasangiz quyidagi 3 qoidani doimo yodda tuting:
  **1 – qoida:** Abstract metodlarni yaratishda metod nomi oldiga abstract so’zini qo’shish kerak va abstract metodlarning tanasi bo’lmaydi.  
  **2 – qoida:**  Hech bo’lmaganda bitta bo’lsa ham abstract metodni o’z ichiga olgan sinf o’z – o’zidan abstract sinfga aylanadi va sinf nomi oldiga abstract so’zi qo’shib qo’yiladi.  
  **3 – qoida:** Abstract sinflar umumiylikni saqlab turish uchun yaratiladi va ularning kostruktori e’loni ham mavjud bo’lmaydi.
{% endhint %}
Yuqoridagi dasturda hayotdagi haqiqiy voqeani aks ettirdik deyishimiz mumkin. “Shakl” sinfi mavhum (abstract) va “Aylana”, “Uchburchak” sinflari uchun ajdod sinf. Undagi  Chizish() metodi ham hech qanday vazifa bajarmasdan faqat umumiylikni saqlab turish uchun yaratildi va voris sinflarda ushbu metodni qayta aniqladik (override kalit so’zi orqali).

Yakunda yana bir muhim qoidani bilishingizni ta’kidlab, shu bilan mavzuni o’z nihoyasiga yetkazamiz:
{% hint style="info" %}
**Yodda tuting:** 
Agar ajdod sinfdagi metod _virtual_ bo’lsa, bu sinfdan voris olganimizda bu metodni qayta aniqlashimiz majburiy emas, ya’ni agar ehtiyoj bo’lsagina qayta aniqlaymiz.   Agar ajdod sinfdagi metod _abstract_ bo’lsa bu sinfdan voris olganimizda bu metodni qayta aniqlashga majburmiz. 
{% endhint %}
