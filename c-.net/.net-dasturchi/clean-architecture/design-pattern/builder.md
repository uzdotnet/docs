---
description: Xondamir Abduxoshimov
---

# Builder

Creational patternlar oilasi bilan tanishishda davom etamiz. Navbatdagi o'ljamiz **Builder** dizayn patterni. 

Builder dizayn patterni bizga murakkab obyektni qismlarga bo'lib, bosqichma - bosqich qurishga imkon yaratadi. Builder interfeysi yoki abstrakt sinfi yakuniy obyektga olib boruvchi qadamlarni belgilaydi. Ya'ni obyektni qurilish jarayoni boshqa qismda amalga oshiriladi. Agar aytilgan fikrlar tushunarsiz bo'lgan bo'lsa, xavotirga o'rin yo'q. Yaqin daqiqalar ichida bunga oydinlik kiritamiz. 

**Misol**:

Berilgan qismlarga ko'ra turli ko'rinishdagi laptoplarni yaratmoqchimiz, Qism qurilmalar : Klaviatura, USB Portlar, Qattiq disk, Touchpad, Batareyka... lar bo'lishi mumkin. Demak, laptoplarni murakkab obyektlarini qurish uchun berilgan qurilmalardan foydalanishimiz mumkin. Qurish jarayoni qanday bo'lishi mumkin?

1. Qattiq diskni o'rnatish
2. Batareykani o'rnatish
3. Klaviaturani o'rnatish
4. .......
5. .......
6. .......
7. Ekranni joylash

Ketma - ketliklardan foydalanib turli laptoplarni yaratishimiz mumkin. Ya'ni : 

* HP - 15.6 inch, 8GB RAM, 256 SSD
* Acer - 17 inch, 4 GB RAM, 128 SSD

Quyida bu holatni diagramma ko'rinishida ham ko'rishingiz mumkin:

![](../../../../.gitbook/assets/image%20%2858%29.png)

E'tbor bergan bo'lsangiz, laptop tayyorlash jarayoni har bir tur uchun bir xil, faqat natijaviy obyekt turi boshqacha. Endi, yuqoridagi diagrammani sal optimalroq ko'rinishga keltiramiz. 

![](../../../../.gitbook/assets/image%20%2848%29.png)

### Builder dizayn patterni diagramma ko'rinishdagi implementatsiyasi

![](../../../../.gitbook/assets/image%20%2860%29.png)

Diagrammaga ko'ra Builder patterni 4 ta layerga\(qismga\) bo'linyabdi.

1. **Builder** : Builder bu - bo'ladigan jarayonlarni aniqlovchi interfeys
2. **ConcreteBuilder** - Concrete Builder bu o'zida Builder\(intefeys yoki abstrakt sinf\) ni imkoniyatlarini implement qiluvchi sinf. 
3. **Director** - bu bo'ladigan jarayonlarni Builderdan olib, mahsulot yaratish ketma-ketligini belgilaydi.
4. **Product** - biz yaratmoqchi bo'lgan obyektni turini belgilovchi sinf

### C\# dasturlash tilida implementatsiya

Oldingi mavzuga o'xshab, ushbu dizayn patternni ham implement qilish uchun, berilgan diagrammaga asosan uni qismlarga ajratamiz.

### 1 - qadam: Productni yaratish

Product bosqichida yaratmoqchi bo'lgan mahsulot maydonlarini o'zida mujassamlashtirgan sinf yaratiladi.

```text
namespace BuilderDesignPattern
{
    public class Laptop
    {
        public string Turi { get; set; }

        public string Xotira { get; set; }

        public string Ekran { get; set; }

        public string Ozu { get; set; }

        public void MalumotlarniKorish()
        {
            Console.WriteLine($"Laptop turi: {Turi}");

            Console.WriteLine($"Laptop xotirasi: {Xotira}");

            Console.WriteLine($"Laptop ekran: {Ekran}");

            Console.WriteLine($"Laptop ozusi: {Ozu}");
        }
    }
}
```

###  2 - qadam: Builder abstrakt sinfini hosil qilish

Builder layeri qadamlarni e'lon qilish uchun xizmat qiladi.

```text
namespace BuilderDesignPattern
{
    public abstract class LaptopBuilder
    {
        protected Laptop Laptop;
    
        public abstract void DoimiyXotiraniJoylashtirish();
        public abstract void VaqtinchalikXotiraniJoylashtirish();
        public abstract void EkranniJoylashtirish();
        public abstract void MarkaniBelgilash();
    
        public void LaptopYaratish()
        {
            Laptop = new Laptop();
        }
    
        public Laptop LaptopniOlish()
        {
            return Laptop;
        }
    }
}
```

### 3 - qadam: ConcreteBuilder sinflarini yaratish

ConcreteBuilder qismda - laptoplarni yaratish logikasini implement qilamiz.

```text
namespace BuilderDesignPattern
{
    class HP : LaptopBuilder
    {
        public override void DoimiyXotiraniJoylashtirish()
        {
            Laptop.DoimiyXotira = "256GB";
        }
    
        public override void EkranniJoylashtirish()
        {
            Laptop.Ekran = "15.6 inch";
        }
    
        public override void MarkaniBelgilash()
        {
            Laptop.Turi = "HP";
        }
    
        public override void VaqtinchalikXotiraniJoylashtirish()
        {
            Laptop.VaqtinchalikXotira = "8GB";
        }
    }
    
    class Acer : LaptopBuilder
    {
        public override void DoimiyXotiraniJoylashtirish()
        {
            Laptop.DoimiyXotira = "128GB";
        }
    
        public override void EkranniJoylashtirish()
        {
            Laptop.Ekran = "17 inch";
        }
    
        public override void MarkaniBelgilash()
        {
            Laptop.Turi = "Acer";
        }
    
        public override void VaqtinchalikXotiraniJoylashtirish()
        {
            Laptop.VaqtinchalikXotira = "4GB";
        }
    }
}
```

### 4 - qadam: Directorni yaratish

Director layerida mahsulot yaratish ketma-ketligi belgilanadi..

```csharp
namespace BuilderDesignPattern
{
    public class LaptopDirector
    {
        public Laptop LaptopIshlabChiqarish(LaptopBuilder laptopBuilder)
        {
            laptopBuilder.LaptopYaratish();

            laptopBuilder.DoimiyXotiraniJoylashtirish();
            
            laptopBuilder.EkranniJoylashtirish();
            
            laptopBuilder.VaqtinchalikXotiraniJoylashtirish();

            laptopBuilder.MarkaniBelgilash();

            return laptopBuilder.LaptopniOlish();
        }
    }
}
```

### 5 - qadam: Client implementatsiya

```csharp
namespace BuilderDesignPattern
{
    class Program
    {
        static void Main(string[] args)
        {
            Laptop laptop;

            LaptopDirector laptopDirector = new LaptopDirector();

            HP hP = new HP();

            laptop = laptopDirector.LaptopIshlabChiqarish(hP);

            laptop.MalumotlarniKorish();

            Console.WriteLine("-------------------");

            Acer acer = new Acer();

            laptop = laptopDirector.LaptopIshlabChiqarish(acer);

            laptop.MalumotlarniKorish();

            Console.ReadKey();
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2863%29.png)

### Builder patternidan qachon foydalanamiz?

1. Murakkab Obyektni bosqichma-bosqich yaratish kerak bo'lsa

So'zimizga shuyerda yakun yasaymiz va sayohatimizni davom ettiramiz.

