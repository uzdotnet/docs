---
description: Sobirjonov O'tkirbek
---
# Interface

## Interface o’zi nima? 
 **Interfeys (en, Interface)** - bu aloqador bo'lmagan obyektlar orasida o'zaro ta'sir qilish uchun foydalanadigan qurilma yoki tizim.  
Masalan : Masofadan boshqarish pulti - siz va televizor o'rtasidagi interfeys. Ingliz tili - ikki kishi o'rtasidagi interfeys. 
Interface qanday yaratiladi? 
Interface larni yaratish juda ham oson.  Quyidagi ko’rinishda interface yaratishingiz mumkin.
```csharp
public interface IAnimal 
    { 
        public void Run(); 
        public void Jump(); 
        public void Eat(); 
    } 
```
Interface larni yaratishda bir qoida bor, Masalan siz Animal interface ni yaratmoqchi bo’lsangiz IAnimal deb nomlashingiz kerak, yoki Person interface ni yaratmoqchi bo’lsangiz IPerson deb nomlar ketishingiz kerak. Nomlar oldidan kelgan “I” harfi bu interface ekanligini bildirib turadi. 
Interface larda faqat funksiya prototipi e’lon qilib ketiladi va funksiya tanasi yozilmaydi. Ya’ni logika yozilmaydi, logikani siz ushbu interface ni implimentatsiya qilgan class da yozasiz. Bu sizga ma’lum bir obyekt xususiyatlarini ajratib olishingizda juda katta yordam beradi.  
Interface ni biror class implementation (implimentatsiya) qilishi mumkin. Va ushbu interface dagi xususiyatlarini o’ziga biriktirib oladi.  
```csharp
public interface IAnimal 
    { 
        public void Run(); 
        public void Jump(); 
        public void Eat(); 
    } 
 
    public class Animal : IAnimal 
    { 
        public void Eat() 
        { 
            Console.WriteLine("Oziqlandi"); 
        } 
 
        public void Jump() 
        { 
            Console.WriteLine("Sakradi"); 
        } 
 
        public void Run() 
        { 
            Console.WriteLine("Yugurdi"); 
        } 
    } 
```
Biror bir class, interfacedan me’ros olgan bo’lsa interface dagi barcha funksiyalarni o’zida e’lon qilishi shart bo’ladi. Masalan : Run yoki Jump funksiyalari e’lon qilinmay qolib ketsa xatolik yuz beradi. Buning afzalligi Interface da funksiya tanasi bo’lmaganligi uchun, umumiy strukturani o’zida saqlab turadi. Haqiqiy proyektlarda juda ko’p interface lar va juda ko’p methodlar bo’ladi, va ular orasidan biror bir method yozilmay qolishi ehtimoli bo’ladi va shunda interface ni qaysi methodi e’lon qilinmaganligi haqidagi error paydo bo’ladi. 
## Multiple Inheritance  
**Multiple Inheritance** bir yoki bir nechta classlardan meros olish degan ma’noda qo’llaniladi. Quyidagi class lar meros olish strukturasiga e’tibor bering. 
```csharp
   public class Father 
    { 
    } 
    public class Mother 
    { 
    } 
 
    public class Child : Father, Mother 
    { 
    } 
```
Ushbu ko’rinishda meros olish , ya’ni child class ham father ham mother class laridan meros olish xususiyati C++ va boshqa ko’p tillarda qo’llab quvvatlanadi. Lekin C# da esa bunga ruxsat yo’q. Child class, Father class ga voris bo’lishi yoki Mother class ga voris bo’lishi mumkin xolos. Quyidagi ko’rinishda 
```csharp
public class Father 
    { 
    } 
    public class Mother 
    { 
    } 
 
    public class Child : Father 
    { 
    } 
```
Yoki  
```csharp
    public class Father 
    { 
    } 
    public class Mother 
    { 
    } 
 
    public class Child : Mother 
    { 
    }  
```
## Interfaceni Multiple Inheritance ga nima aloqasi bor? 
**Interface**lar **multiple inheritance** ni qo’llab quvvatlaydi. **Multiple Inheriatance** - **Interface**larni larni qo’llashdagi asosiy imkoniyatlardan biri hisoblanadi. Ya’ni bir class bir nechta interface lardan meros olishi mumkin. 
Bir dastur yozsakda, u orqali interface larni ishlatishni samarasi va multiple inheritance ga nima aloqasi bor ekanligi tushunib olsak. 
Tasavvur qiling, biz hayvonlar classini tuzish jarayonidamiz va ularning xususiyatlarini belgilayapmiz. 
```csharp
public interface IRunnable 
    { 
        public void Run(); 
    } 
    public interface IJumpable 
    {
        public void Jump(); 
    } 
    public interface ISwimmable 
    { 
        public void Swim(); 
    } 
    public interface IHuntable 
    { 
        public void Hunt(); 
    } 
```
## Interface larni yaratib oldik, endi esa ularni qo’llashimizga e’tibor bering 
```csharp
public class Fish : ISwimmable 
    { 
        public void Swim() 
        { 
            Console.WriteLine("Suzdi"); 
        } 
    } 
 
    public class Tiger : IRunnable, ISwimmable,  
        IJumpable, IHuntable 
    { 
        public void Hunt() 
        { 
            Console.WriteLine("Ov qildi"); 
        } 
 
        public void Jump() 
        { 
            Console.WriteLine("Sakradi"); 
        } 
 
        public void Run() 
        { 
            Console.WriteLine("Yugurdi"); 
        } 
 
        public void Swim() 
        { 
            Console.WriteLine("Suzdi"); 
        } 
    } 
 
    public class Deer : IRunnable, IJumpable, ISwimmable 
    { 
        public void Jump() 
        { 
            Console.WriteLine("Sakradi"); 
        } 
 
        public void Run() 
        { 
            Console.WriteLine("Yugurdi"); 
        } 
 
        public void Swim() 
        { 
            Console.WriteLine("Suzdi"); 
        } 
    }  
```
Classlarni ham yaratib oldik, endi ularni tahlil qilsak:

1. Fish (Baliq) class: 
Suza oladi 
Ov qilolmaydi 
Yugura olmaydi 
Sakray olmaydi 
2. Tiger (Yo’lbars) class : 
Suza oladi 
Ov qiladi 
Yugura oladi 
Sakray oladi 
3. Deer (Kiyik) class: 
Suza oladi 
Ov qilmaydi 
Yugura oladi 
Sakray oladi

 
## Interfacelar nima uchun kerak? 
1. Interface lar Multiple Inheritance ni qo’llab quvvatlaydi. 
2. Interface lar asosiy strukturani ushlab turadi. 
3. Interface lar kodni qisqarishi , tushunarli bo’lishi va umumiylashgan bo’lishiga yordam beradi.  
4. Interface lar dastur tezroq yozilishiga yordam beradi ( Avval Interface larni yozib chiqsangiz, dasturingiz nima qilishini yozgan bo’lasiz, va ularni classlarda implementatsiya qilib, dasturingiz u amallarni qanday  amalga oshirishini yozasiz) 
5. Interface lar Dependency Injection uchun juda katta yordam beradi. SOLID ning “D” (Dependency Enviroment ) tamoyiliga amal qilishingizda asosan interfacelar ishlaydi. (Agar bu afzallikda siz tushunmagan narsalar bo’lsa e’tibor bermang, ularni keyingi mavzularda o’rganib olasiz). 
 
Demak barchasi tushunarli bo’ldi degan umiddaman, agar tushunmagan bo’lsangiz qayta qayta o’qib chiqing va dasturlaringizda ishlatib ko’ring.
