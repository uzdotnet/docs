---
description: Xondamir Abduxoshimov
---

# Prototype

Prototype dizayn patterni bilan tanishishni boshlaymiz. Bu pattern ham Creational patternlar oilasiga mansub. Prototype patternidan foydalanishdan maqsad berilgan obyekt nusxasini yaratishdan iborat. Ya'ni, yangi obyekt berilgan obyektdan prototip\(klon\) olgan holda yaratiladi. 

{% hint style="info" %}
Prototype DIzayn Patterni boshqa Creational patternlardan farq qiladi. Prototype patterni bizdan nusxa olinadigan obyektni yuborishimizni kutadi va uni nusxalab qaytaradi, boshqa Creational Patternlarga o'xshab sinf shart emas.
{% endhint %}

Bu patternni turli xil usullardan foydalanib implement qilish mumkin. Men osonroq tushunish uchun quyidagi diagrammadan foydalangan holda ko'rsatib berishga qaror qildim. An'anamizga ko'ra implementatsiya qilishni birinchi diagramma, so'ngra code orqali ko'ramiz. 

### Prototype dizayn patterni diagramma ko'rinishdagi implementatsiyasi

![](../../../../.gitbook/assets/image%20%2875%29.png)

1. **Prototype** - nusxalashni amalga oshiruvchi interfeys
2. **ConcretePrototype** - obyektni nusxalash uchun, Prototype interfeysni implement qilgan sinf

### C\# dasturlash tilida implementatsiya

Bizning korxonada Dasturchi injiner positsiyasidagi ishchilar bir nechta va ularning darajasi turlicha. Keling, ularning obyektlarini va nusxalarini Prototype patterni orqali implement qilamiz. 

### 1 - qadam: Prototype interfeysini yaratish

```csharp
namespace PrototypeDesignPattern
{
    public interface IEmployee
    {
        IEmployee NusxaOlish();
        
        string MalumotlarniOlish();
    }    
}
```

### 2 - qadam: Nusxa olinadigan sinfni yaratish

```csharp
namespace PrototypeDesignPattern
{
    public class Developer : IEmployee
    {

        public string Name { get; set; }

        public string Degree { get; set; }

        public string MalumotlarniOlish()
        {
            return $"Ismi: {Name}, Darajasi: {Degree}";
        }

        public IEmployee NusxaOlish()
        {
            return (IEmployee)MemberwiseClone();
        }
    }
}
```

### 3 - qadam: Natija olish

```csharp
namespace PrototypeDesignPattern
{
    class Program
    {
        static void Main(string[] args)
        {
            Developer developer = new Developer
            {
                Name = "Khondamir",
                Degree = "Junior"
            };
        
            Developer developerNusxasi = (Developer)developer.NusxaOlish();
        
            developerNusxasi.Name = "Olimjon";
        
            Console.WriteLine(developer.MalumotlarniOlish());
        
            Console.WriteLine("---------Olingan Nusxa-----------");
        
            Console.WriteLine(developerNusxasi.MalumotlarniOlish());
        
            Developer yanabirDeveloperNusxasi = (Developer)developer.NusxaOlish();
        
            yanabirDeveloperNusxasi.Name = "Malik";
        
            yanabirDeveloperNusxasi.Degree = "Senior";
        
            Console.WriteLine("---------Olingan Nusxa-----------");
        
            Console.WriteLine(yanabirDeveloperNusxasi.MalumotlarniOlish());
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2874%29.png)

Nusxalashni foyda taraflaridan biri, agar obyektlarda qaysidur maydonlar bir xil bo'lsa, unga o'zgartirish kiritish shart emas. 

### Builder patternidan qachon foydalanamiz?

1. Obyektni yaratish bizga murakkablik tug'dirsa
2. Bitta maydonlarni qayta o'zgartish kerak bo'lsa

Barchasi tushunarlik bo'ldi degan umiddaman. O'rganishda davom etamiz.

