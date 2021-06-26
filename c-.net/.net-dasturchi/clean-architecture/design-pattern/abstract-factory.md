---
description: Xondamir Abduxoshimov
---

# Abstract Factory

Barchaga xayrli kun, bugungi suxbatimizda **Abstract Factory** dizayn patterni qanday qilib C\# dasturlash tilida implementatsiya qilinadi? va U qanday muammolarga yechim bo'la oladi? kabi savollarga javob topamiz. Agarda siz bundan oldingi [**Factory Method** ](https://docs.dot-net.uz/c-.net/.net-dasturchi/clean-architecture/design-pattern/factory-method)haqida yozilgan maqolamizni o'qimagan bo'lsangiz, avvalo shu patternni o'rganishni maslahat beraman. Bu sizga bugungi maqolani yaxshiroq tushunishga imkon yaratadi. Demak, bugungi o'rganadigan patternimiz Creational Patternlar guruhiga mansub bo'lib, haqiqiy dasturlarda keng foydalaniladi.

### Abstract Factory Dizayn Patterni nima?

GoF\(Gang of Four\)da berilgan ta'rifga ko'ra : 

> Abstract Factory Dizayn Patterni umumiy mantiqga ega bo'lgan, alohida factory\(fabrika\)lar guruhida joylashgan aniq sinflarni yashirgan holda inkapsulatsiya\(kapsulalash\) usulini taqdim etadi.

Buni oddiy so'z bilan, Abstract Factory - bu boshqa fabrikalarni ishlab chiqadigan supper fabrika. Ya'ni fabrikalarning fabrikasi\(Factory of Factories\).

{% hint style="success" %}
Abstract Factory = AF
{% endhint %}

Keling AFni bir misol orqali tushunishga harakat qilamiz. Tasavvur qiling, Hayvonlar guruhini yaratmoqchimiz va ularning qanday ovoz chiqarishini bilmoqchisiz : Mushuk, Sher, Kuchuk.

Quyida berilgan diagrammaga e'tiboringizni qarating. Ko'rib turganingizdek bizda 3 ta hayvonlar sinfi mavjud. Ya'ni, Mushuk, Sher, Kuchuk. Ushbu sinflar Hayvon \(supper sinf yoki supper interfeys\) ning vorislari hisoblanadi. Hayvon\(supper sinf yoki supper interfeys\) da **Speak\(\)** degan metod mavjud. Har bir sinf Speak\(\) metodini implementatsiya qilib, kerakli ovozlarni qaytarib yuboradi. Shuningdek, bu hayvonlar quruqlikda yashovchi hayvonlar hisoblanadi. \(Bizga hayvonni qayerda yashashini bilishni nima foydasi bor degan savol bo'lishi mumkin. O'qishda davom eting birozdan so'ng tushunib olasiz\).

![](../../../../.gitbook/assets/image%20%2810%29.png)

Ushbu holatni Factory Method patterniga asoslangan holda osongina diagramma ko'rinishida tasvirlashimiz mumkin. Ya'ni:

![](../../../../.gitbook/assets/image%20%2847%29.png)

Yuqoridagi diagrammaga oydinlik kiritadigan bo'lsak, **QuruqlikHayvonlariFabrikasi** - hayvonlarni ishlab chiquvchi asosiy fabrika va unda birgina **HavonOlish** degan metod mavjud. HayvonOlish metodi **hayvonTuri** nomli argumentni qabul qilib, berilgan turga mos holda kerakli hayvonni ishlab chiqaradi va qiymatni Hayvon\(supper class yoki supper interfeys\) ko'rinishida qaytaradi.

Keling endi, quruqlikdagi hayvonlarni yaratish bilan cheklanib qolmay, suvda yashovchilarga ham fabrika yaratib ko'ramiz.

![](../../../../.gitbook/assets/image%20%2846%29.png)

Ko'rib turganingizdek Factory Methoddan foydalanib bu 2 hayvon turlarini diagrammasini hosil qildik. Sezgan bo'lsangiz bu pattern bizdan ortiqcha ishlarni talab qildi. Endi AFda bu ko'rinish qanday tus oladi. 

![](../../../../.gitbook/assets/image%20%2828%29.png)

### AFni C\# da implementatsiyasi

Keling ushbu implementatsiyani qadam ko'rinishida yaratib boramiz.

#### 1 - qadam: Abstrakt mahsulotni yaratish\(Abstract Product\)

Birinchi navbatda Hayvon nomi bilan interfeys hosil qilamiz va unda Speak\(\) nomli metodni e'lon qilamiz.

```csharp
namespace AbstractDesignPattern
{
    public interface IHayvon
    {
        string Speak();
    }
}
```

#### 2 - qadam: Aniq mahsulotlarni yaratish\(Concrete Products\)

Ushbu holatda AF interfeysini\(Bizni holatda Hayvon\) implement qiluvchi sinflarni hosil qilamiz. Yani: Mushuk, Sher, Kuchuk, Baqa, Aqula.

```csharp
namespace AbstractDesignPattern
{
    public class Mushuk : IHayvon
    {
        public string Speak()
        {
            return "Myov";
        }
    }
    
    public class Sher: IHayvon
    {
        public string Speak()
        {
            return "Raar";
        }
    }
    
    public class Kuchuk: IHayvon
    {
        public string Speak()
        {
            return "Vov";
        }
    }
    
    public class Baqa: IHayvon
    {
        public string Speak()
        {
            return "Kvak";
        }
    }
    
    public class Aqula: IHayvon
    {
        public string Speak()
        {
            return "Men gapirmayman";
        }
    }
}
```

#### 3 - qadam: AFni yaratish \(Abstract Factory\)

AF bu interfeys yoki abstract sinf bo'lishi mumkin va u abstrakt mahsulotlarni ishlab chiqadi. 

```csharp
namespace AbstractDesignPattern
{
    public abstract class HayvonFabrikasi 
    {
        public abstract IHayvon HayvonOlish(string hayvonTuri);

        public static HayvonFabrikasi HayvonFabrikasiYaratish(string fabrikaTuri)
        {
            if (fabrikaTuri.Equals("Suv"))
                return new SuvHayvonlariFabrikasi();

            return new QuruqlikHayvonlariFabrikasi();
        }
    }
}
```

#### 4 - qadam: Aniq fabrikalarni yaratish\(Concrete Factory\)

Ushbu qismda aniq fabrikani tavsiflovchi bitta sinf yaratiladi va u AF \( bizda **HayvonlarFabrikasi**\) sinfini implement qiladi. Shuningdek **HayvonOlish** abstrakt metodini qayta ishlaydi.

```csharp
namespace AbstractDesignPattern
{    
    public class QuruqlikHayvonlariFabrikasi : HayvonFabrikasi
    {
        public override IHayvon HayvonOlish(string hayvonTuri)
        {
            switch (hayvonTuri)
            {
                case "Mushuk":
                    return new Kuchuk();

                case "Sher":
                    return new Sher();

                case "Kuchuk":
                    return new Sher();

                default:
                    throw new ApplicationException("Quruqlikda bunday hayvon yashamaydi");
            }
        }

    }

    public class SuvHayvonlariFabrikasi : HayvonFabrikasi
    {
        public override IHayvon HayvonOlish(string hayvonTuri)
        {
            switch (hayvonTuri)
            {
                case "Baqa":
                    return new Baqa();

                case "Aqula":
                    return new Sher();

                default:
                    throw new ApplicationException("Suvda bunday hayvon yashamaydi");
            }
        }

    }
}
```

#### 5 - qadam: Natijani ko'ramiz\(Client layer\)

Client qatlamida - kerakli fabrika va mahsulotlar yaratiladi. Dehqonchasiga, obyekt olish jarayoni.

```csharp
using System;
namespace AbstractFactoryDesignPattern
{
    class Program
    {
        static void Main(string[] args)
        {
            IHayvon hayvon = null;

            HayvonFabrikasi hayvonFabrikasi = null;

            string hayvonOvozi = null;

            //Suvdagi hayvonlarni ishlab chiquvchu fabrikani quramiz

            hayvonFabrikasi = HayvonFabrikasi.HayvonFabrikasiYaratish("Suv");

            Console.WriteLine($"Fabrika turi: {hayvonFabrikasi.GetType().Name}");

            Console.WriteLine();

            hayvon = hayvonFabrikasi.HayvonOlish("Baqa");

            hayvonOvozi = hayvon.Speak();

            Console.WriteLine($"{hayvon.GetType().Name} ovozi: {hayvonOvozi}");

            Console.WriteLine();

            Console.WriteLine("--------------------------");

            //Quruqlikdagi hayvonlarni ishlab chiquvchu fabrikani quramiz

            hayvonFabrikasi = HayvonFabrikasi.HayvonFabrikasiYaratish("Quruqlik");

            Console.WriteLine($"Fabrika turi: {hayvonFabrikasi.GetType().Name}");

            Console.WriteLine();

            hayvon = hayvonFabrikasi.HayvonOlish("Sher");

            hayvonOvozi = hayvon.Speak();

            Console.WriteLine($"{hayvon.GetType().Name} ovozi: {hayvonOvozi}");

            Console.ReadKey();
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2843%29.png)

### AF dan qachon foydalanamiz?

Implementatsiya bosqichini tugatdik, galdagi navbatda AF aynan qayerlarda ish beradi shu savolga javob topamiz.

* Birgalikda ishlatilishi kerak bo'lgan, bog'liq obyektlarni hosil qilishda
* Yaratilayotgan tizim, bir nechta mahsulotlar fabrikasini hosil qilishda

Bugungi suxbatimiz davomida Abstract Factory dizayn patterni haqida bilganlarimizni Alloh qodir qilgancha yoritishga harakat qildik. Barchasi tushunarlik bo'ldi degan umiddaman. Keyingi o'lja Builder dizayn patterni.

