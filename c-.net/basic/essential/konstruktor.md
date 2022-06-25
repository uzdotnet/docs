---
description: Shohruh Nosirov
---

# Konstruktor

Oddiy usullardan tashqari sinflarda **konstruktor** deb nomlangan maxsus usullar ham qo'llaniladi . Ushbu sinfning yangi ob'ekti yaratilganda konstruktorlar chaqiriladi. Konstruktorlar ob'ektni ishga tushirishni amalga oshiradilar. Ushbu sinfning yangi ob’ekti yaratilganda konstruktorlar chaqiriladi. Konstruktorlar ob’ektni ishga tushirishni amalga oshiradilar va sinflarni initsializatsiyalashga imkoniyat beradi, sinfning obyektini hosil qilganimizda, u xotiradan joy ajratadi. Ya’ni konstruktor – bu oddiy \(struktura bo’yicha\) funksiya, kirish ma’lumotlarini olib, sinf maydonlarini o’zlashtiradi. Konstrukto hosil qilingan har qaysi obyekt uni chaqiradi. Konstruktorlar biz biladigan metodlardan bir farqli jihati bor ekan bu esa hech qanday qiymat qaytarmaydi: na int tipi, na float tipi, na double tipini va hattoki void tipini ham.Shunaqa metod ham bularkanmi mana bularkanu. C\# tilida biz agar konstruktor yozish esimizdan chiqib qoladigan bulsa o’zi jimlik buyicha sinf bitta konstruktorni yaratadi ammo u bizga kurinmaydi.Bunday konstruktorlarni **standart konstruktorlar** ham deb atashadi. Bunday konstruktorning parametrlari va tanasi yo‘q. Buni kurishingiz uchun oddiy misolni siz uchun tayorlab quydim:

```csharp
using System;

namespace HelloApp
{
    public class Talaba
    {
        public string  ismi ;
        public int yoshi ;
    } 
   class Program
    {
        static void Main(string[] args)
        {
            Talaba Shohruh=new Talaba();
        }
    }
}
```

Kurdingizmi qanday aqlli tilni o’rganayapsiz. Konstruktorni asosiy qoidalaridan biri bu konstruktorning nomi sinf nomi bilan bir xil buladi. Konstruktorlarni asosiy qolipi bir xil bulgani bilan ular parametrlarining turlar bilan\( int, string\) farq qilishi mumkin. Talaba nomli class yaratamiz va uning ob’ekttini hosil qilamiz.

```csharp
using System;

namespace Hello
{
public class Talaba
    {
        public string  ismi ;
        public int yoshi ;
    } 
class Program
{
    static void Main(string[] args)
    {
            Talaba a = new Talaba();

            a.ismi = "Shohruh";
            a.yoshi = 24;
        Console.ReadKey();
    }
}
}
```

Talaba ob’ektini yaratish uchun **new Talaba\(\)** ishlatiladi. **new** operator Talaba ob'ekti uchun xotiradan joy ajratadi. Va keyin sinfda mavjud bulgan xossalar chaqirilib, ularga qiymatlar berilmoqda. a o'zgaruvchisi yaratilgan ob'ektga mos qiymatlarni xossalarga qiymatlar biriktiriladi. Agar biz ularga qiymat bermasak nima buladi degan savol tug’ilishi mumkin. Bu holat uchun ham C\# bizga yechim topgan bundan havotir olmasak ham buladi.Agar xossalarimiz raqamli turda buladigan bulsa 0 ni oladi, satrlilar uchun esa null\(yani hech qanday qiymat mavjud emas\) ni oladi. Endi konstruktorlarni o’zimiz ham yaratib kuraylikchi. Shu bilan birga bir biridan farq qiladigan konstruktorlani ham kursatib o’tib ketaman.Unda keying misolga etibor bilan qarang.Yuqorida , ob’ektni ishga tushirish uchun standart konstruktor ishlatilgan . Biroq, biz o’zimiz konstruktorni aniqlaymiz.

```csharp
class Person
{
    public string name;
    public int age;

    public Person() { name = "Nomalum"; age = 18; }      // 1-konstruktor

    public Person(string n) { name = n; age = 18; }         // 2 -konstruktor

    public Person(string n, int a) { name = n; age = a; }   // 3 -konstruktor

    public void GetInfo()
    {
        Console.WriteLine($"Name: {name}  Age: {age}");
    }
}
```

Endi sinf 3 ta konstruktorni aniqlaydi, ularning har biri har xil parametrlarni qabul qiladi vas inf maydonlarining qiymatlarini belgilaydi. Endi shu konstruktorlardan foydalanib kuraylikchi nima bularkan.

```csharp
static void Main(string[] args)
{
    Person Ali = new Person();              // 1-konstruktor chaqirilyapdi
    Person Vali = new Person("Vali");          //2-konstruktor chaqirilyapdi 
    Person Gani = new Person("G’ani", 25);   // 3-konstruktor chaqirilyapdi 


    Ali.GetInfo();             // Name: Nomalum  Age: 18
    Vali.GetInfo();           // Name: Vali  Age: 18
    Gani.GetInfo();          // Name: G’ani  Age: 25
}
```

Yana bir qoidamiz bor, agar sinfda konstruktorlar yaratilgan bulsa , ulardan birini aniq ishlatishimiz kerak ekan. Menimcha C\# mehnatni qadrlaydigan til menimcha shuncha konstruktor yaratganingdan keyin hech bulmasa bittasini ishlatgin demoqchi shekilli. Sizlarga bir yangilikni ham aytib utmoqchiman C\# 9.0 dan boshlab biz konstruktor chaqirayotganimizda new dan sung sinf nomini yozishimiz shart emas ekan. Masalan mana bunday qilib:

```csharp
Person Ali=new ();                             //     Person Ali = new Person();   degani
Person Vali=new(“Vali”);                  //     Person Vali = new Person("Vali");         
Person G’ani =new (“G’ani”, 25);     // Person G’ani = new Person("G’ani", 25);
```

Shu bilan konstruktorni ham bilib oldik darslarimiz qiziq ketayapdi degan umiddaman. Hali oldinda bizni qizg’in darslar kutib turibdi.

