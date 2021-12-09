---
description: Xondamir Abduxoshimov
---

# Factory Method

**Creational Patternlar** obyekt yoki tegishli obyektlar guruhini yaratishdagi ba'zi bir muammolarni yechishda foydalaniladi. Bu patternlar 5 tani tashkil qiladi:

1. Factory Method
2. Abstract Factory
3. Builder
4. Prototype
5. Singleton

Demak, o'rganishni Factory Method patterni bilan tanishish orqali boshlaymiz.&#x20;

**Factory Method** dizayn patterni obyekt yaratilish jarayonini abstrakt(mavhum)lashtirib, run-time paytida qachonki extiyoj sezilganda obyektni yaratilishiga imkon yaratadi. Dasturchilar ushbu patterni odatda obyekt yaratishning standart usuli sifatida foydalanishadi. Keling berilgan **factory method** patterniga yanayam sinchikovlik bilan yondashamiz.&#x20;

{% hint style="success" %}
Factory Method = FM
{% endhint %}

Biz FMdan foydalangan holda obyektni uning yaratilish logikasini yashirgan holda hosil qilamiz. Ya'ni, obyekt yaratish uchun interfeysdan foydalaniladi, lekin voris class qaysi class obyekti yaratilishini belgilaydi.&#x20;

Albatta sizga berilgan ma'lumotlar birdaniga tushunarsiz bo'lishi mumkin, men ham bir o'qishda o'rgana olmaganman. Lekin ko'proq misollar orqali ko'rsangiz buni tushunish osonroq kechadi.

Quyidagi ko'rsatilgan UML diagramma, FMni qanday tashkil etilishini belgilaydi.

![](<../../../../.gitbook/assets/image (13).png>)

Yuqoridagi diagramma elementlari nimani anglatadi birma - bir tahlil qilib chiqamiz:

1. **Product** -  obyektlarni yaratish uchun interfeys.
2. **ConcreteProduct** - Product interfeysini implement qiluvchi sinf.
3. **Creator** - Product obyektini qaytarib beruvchi FMni aniqlovchi abstrakt sinf.
4. **ConcreteCreator** - Creator sinfidan olingan voris sinf.

Misol:

Tasavvur qiling bizda transport vositalari bor va biz ularning bosib o'tgan masofalarini foydalanuvchiga ko'rsatmoqchimiz. Ho'sh ushbu holatda FMni qanday tashkil etamiz.

```csharp
using System;
namespace Factory
{
     public interface ITransport
     {
         void Drive(int miles);
     }


     public class Skuter : ITransport
     {
         public void Drive(int miles)
         {
             Console.WriteLine("Skuter yurgan yo'li : " + miles.ToString() + "km");
         }
     }

     public class Mototsikl: ITransport
     {
         public void Drive(int miles)
         {
             Console.WriteLine("Mototsikl yurgan yo'li : " + miles.ToString() + "km");
         }
     }


     public abstract class TransportFabrikasi
     {
         public abstract ITransport TranportOlish(string transport);    
     }


     public class TransportIshlabChiqarish : TransportFabrikasi
     {
         public override ITransport TranportOlish(string transport)
         {
             switch (transport)
             {
                 case "Skuter":
                     return new Skuter();
                 case "Mototsikl":
                     return new Mototsikl();
                 default:
                 throw new ApplicationException(string.Format("Uzrasiz akasi '{0}' transportini biz ishlab chiqolmimiz", transport));
             }
         }
     }
     
     class Program
     {
         static void Main(string[] args)
         {
             TransportFabrikasi fabrika = new TransportIshlabChiqarish();
            
             ITransport skuter = fabrika.TranportOlish("Skuter");
             skuter.Drive(10);
            
             ITransport mototsikl = fabrika.TranportOlish("Mototsikl");
             mototsikl.Drive(20);
            
             Console.ReadKey();        
         }
     }
 }
```

Natija:

![](<../../../../.gitbook/assets/image (7) (1) (1) (1).png>)

### FMni qachon foydalanamiz?

Endi asosiy nuqtaga keldik. Ho'sh sizningcha ushbu pattern bizga qanday imkoniyatlar yaratib beradi.

1. Ba'zi dasturlash tillarida konstruktorlarda istisnolardan foydalanish yomon oqibatlarga olib kelishi mumkin. Bu muammolarni keltirib chiqaradi. FM bo'lsa bunga chek qo'yadi.&#x20;
2. Qachonki konstruktorga murojaat qilganingizda, yaratiladigan obyekt turini aniq bilishingiz kerak. Bu har doim ham o'rinlik emas. Tasavvur qiling kompyuterga telfonizni ulamoqchisiz, lekin oldindan u qaysi uslubda kompyuteringizga ulanishini bilmayabsiz(Ethernetmi, COMmi yoki USBmi). Bu holatda FMni qo'llash ancha qulaylik beradi. Ya'ni, siz run-time paytida tanlovga ko'ra qaysi uslub mos kelishini aniqlashingiz mumkin.

O'ylaymanki aytib o'tilgan fikrlar sizga tushunarlik bo'ldi. Sayohatimizni davom ettiramiz.
