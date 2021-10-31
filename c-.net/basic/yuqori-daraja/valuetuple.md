---
description: Hikmatullayev Sayidrahmatulloh
---
# ValueTuple
*C# da ValueTuple.*


**Tuple** bu - bir nechta elmentlardan tuzilgan ma'lumotlar majmuasi .

**ValueTuple**  esa **Tuple** ni qiymat turini ifodalaydi.

 **Tuple** va **ValueTuple** ni solishtirib ko'raylik.

{% hint style="info" %}

* 1.**Tuple** malum biror son elementlar ketma-ketligi  ifodalanadi , **ValueTuple** esa elementlar qiymatlarini ifodalsh mumkin turi.

* 2.**Tuple** larda nol kompanentali kortej yaratishga ruxsat berilmagan , **ValueTuple** da bunday kartej yaratish mumkin.

* 3.**ValueTuple** elementlari o'zgaruvchan .**Tuple** ning  elementlari esa faqat o'qish ushun.

{% endhint %}

**ValueTuple** yaratish strukturasi.

{% hint style="info" %}

* Bitta element uchun

`ValuTuple<T1>(T1) `

* Ikta element uchun

`ValueTuple<T1,T2>(T1,T2)`

.

.

.

* Sakkizta yaratish uchun

`ValueTuple<T1,T2,T3,T4.T5,T6,T7,T8>( T1,T2,T3,T4.T5,T6,T7,T8)`
{% endhint %}

**ValueTuple** ga ham **Tuple** kabi 8 ta element kiritish mumkin halos.

Lekin bu muammoni **ValueTuple** ichida **ValueTuple** yaratish orqali hal qilish mumkin.

Keling **ValueTuple**ga elementlarni kiritish ko'raylik.

```csharp
using System;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            ValueTuple<int> t1 = new ValueTuple<int>(2021);     // t1 nomli bitta elementli valuetuple ochdik
            ValueTuple<string,string,double> t2 = new ValueTuple<string,string,double>("C#","C++",7.1);
            // t2 nomli 3ta elementli valuetuple ochdik
            ValueTuple<int, int, int, int, ValueTuple<int, int>> t3 = new ValueTuple<int, int, int, int, ValueTuple<int, int>>(1, 2, 45, 23,new ValueTuple<int, int>(12, 56));
            //t3 nomli 5 elmentli valuetuple ochdik 
            // ko'rib turganingizdek valuetuple ichida valuetuple ochdik
        }
    }
}
```
**VauleTuple** da ham **Tuple** kabi *Create()*  funksiyasidan foydalanish mumkin.

```csharp
using System;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            var tuple1 = ValueTuple.Create(); // bo'sh valuetuple yaratdik
            var tuple2=ValueTuple.Create(7.13,"C#","donetuz"); //3ta elementli valuetuple ochdik
            var tuple3 = ValueTuple.Create("C", "C++", "C#", "Python", "Java", "JavaScript", "JavaScript");
        }
    }
}
``` 
**ValueTuple** da har bir kortej o'z nomiga hususiyatiga ega bo'lish imkoni bor.

Buni quyadagi misolda koramiz.

```csharp
using System;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            (string ism, string familya, int yosh) student = ("Sayidrahmatulloh", "Hikmatullayev", 20);
            System.Console.WriteLine(student);
        }
    }
}
``` 
Qora oynadagi natija.

`(Sayidrahmatulloh, Hikmatullayev, 20)`

**ValueTupe**ning ellementlariga murojat qilishni ko'raylik.

```csharp 
using System;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            var tuple1 = ("dotnetuz", "Csharp", 2021);
            Console.WriteLine("Sayt :"+tuple1.Item1);
            Console.WriteLine("Dasturlash tili :"+tuple1.Item2);
            Console.WriteLine("Yil :" + tuple1.Item3);
        }
    }
}
``` 

Qora oynadagi natija.

`Sayt :dotnetuz`

`Dasturlash tili :Csharp`

`Yil :2021`

**ValueTuple** ham **Tuple** kabi elementlariga aftomatik nom beradi .

Lekin elementlarni o'zmiz nomlasak biz uchun ancha qulay bo'ladi.

Keling **ValueTuple** ni elementlarni nomlab murojat qilib koraylik.

```csharp
using System;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            var student = (Ism: "Sayidrahmatulloh", Familya: "Hikmatullayev", Yosh: 20);
            Console.WriteLine("Ismi : "+student.Ism);
            Console.WriteLine("Familyasi : "+student.Familya);
            Console.WriteLine($"Yoshi : {student.Yosh}");
        }
    }
}
``` 
Qora oynadagi natija.

`Ismi : Sayidrahmatulloh`

`Familyasi : Hikmatullayev`

`Yoshi : 20`

Keling endi **ValueTuple** oraqali metod yaratamiz.
Metod yaratish dovomida `System.Console` funksiyasini ishlatishni ko'ramiz.

```csharp 
using System;
using static System.Console;
 /// <summary>
/// System.Console ni qoshib oldik
/// </summary>
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            Write(student());   // ko'rib turganingizdek Console.Write emas Write ishlatilgan
            //System.Console bizga shu imkoniyatni beradi.
        }
        static(int ,string ,string ) student()  // metod yaratib oldik
        {
            return (20, "Sayidrahmatulloh", "Hikmatullayev");
        }
    }
}
``` 
Qora oynadagi natija .

`(20, Sayidrahmatulloh, Hikmatullayev)`

**Metod** ochilganda **ValueTuple**ning elementlariga murojat qlish avvalgi misollar kabi bo'ladi.

**ValueTuple**ni quydagi misolda tushintirishga hatrakat qilaman.

```csharp
using System; 
/// <summary>
/// Alibaba nomli metod ochdik
/// Va Alibaba kompaniya haqida malumotlar kiritish uchun ValueTuple dan foydalandik
/// </summary>
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            var alibaba = Alibaba();
            Console.WriteLine(alibaba.Kompaniya_tarixi);
        }
        static (string Kompaniya_tarixi,string Foydasi,string Nufuzi ) Alibaba()
        {
            var kompaniya_tarixi = "Alibaba Group Holding Limited — Alibaba Group va Alibaba.com sifatida tanilgan, Xitoyning elektron tijorat, chakana savdo,\n Internet va texnologiyalarga ixtisoslashgan transmilliy texnologik kompaniyasi. \n1999-yil 28-iyunda Chjetszyan shahrining Xanchjou shahrida tashkil etilgan[1].\n Kompaniya veb-portallar orqali isteʼmolchidan isteʼmolchiga (C2C),\n biznesdan isteʼmolchiga (B2C) va biznesdan biznesga (B2B) savdo xizmatlarini taqdim etadi.\n Elektron toʻlov xizmatlari, xarid qilish qidiruv tizimlari va bulutli hisoblash xizmatlari mavjud.\n U dunyodagi ko'plab biznes sohalarida turli xil kompaniyalar portfeliga egalik qiladi va ishlaydi[2]. \nBuyuk Britaniyaning dunyo bozorini o‘rganuvchi «Kantar» kompaniyasi dunyoning eng qimmat kompaniyalari reytingini e’lon qildi. ";
            var foydasi = "25 mlrd AQSh dollar";
            var nufuzi="Jaxon reytingini kuchli o'ntaligida 'Alibab' turadi ";
            return (kompaniya_tarixi,foydasi,nufuzi);
        }
    }
}
```
Qora oynadagi natija .

`Alibaba Group Holding Limited - Alibaba Group va Alibaba.com sifatida tanilgan, Xitoyning elektron tijorat, chakana savdo,`
 `Internet va texnologiyalarga ixtisoslashgan transmilliy texnologik kompaniyasi.`

`1999-yil 28-iyunda Chjetszyan shahrining Xanchjou shahrida tashkil etilgan[1].`

` Kompaniya veb-portallar orqali iste'molchidan iste'molchiga (C2C),`
` biznesdan iste'molchiga (B2C) va biznesdan biznesga (B2B) savdo xizmatlarini taqdim etadi.`

` Elektron to?lov xizmatlari, xarid qilish qidiruv tizimlari va bulutli hisoblash xizmatlari mavjud.`

` U dunyodagi ko'plab biznes sohalarida turli xil kompaniyalar portfeliga egalik qiladi va ishlaydi[2].`

`Buyuk Britaniyaning dunyo bozorini o'rganuvchi «Kantar» kompaniyasi dunyoning eng qimmat kompaniyalari reytingini e'lon qildi.`


Misolda ko'rganimizdek **ValuTuple** orqali  o'zimiz uchu kerakli ma'lumotlarni qulay tarzda olishimiz mumkin.

Ya'ni biz  o'zimiz uchun **ValueTuple** dagi qaysi element kerak bo'lsa shu elementadan foydalanishimiz mumkin.

**ValueTuple** bizga elementlarni qiymatini o'zgartirish imkoniyatini ham beradi.
