---
description: Asronov Abdullo
---

# Field and Properties

Field- Bu so'zni o'zbekchaga tarjima qilsak "MAYDON" degan ma'noni beradi. Lekin bizda  C# Field nima, uni qayerda ishlatishiz mumkin kabi savol tug'ilishi mumkin.  

C# dasturlash tilida  Field  bu  to'g'ridan-to'g'ri "Class" yoki "Strukturada" e'lon qilingan har qanday turdagi o'zgaruvchidir;  Yana Classning ichidagi har qanday tipdagi o'zgaruvchi; 

Fieldning Asosiy Vazifasi - U asosan ma'lumot saqlashga ishlatiladi. Ko'p hollarda fieldni private(yani Classning shaxsiy o'zgaruvchisi) holda ochiladi va bu fieldni biz faqat "Class" ni ichida foydalana olamiz . Aniqrogi shu classdan obyekt olinganda unga to'gridan to'gri murojat qila olmaymiz. Lekin boshqa tiplarda ham ochish mumkin; bu haqda keyingi Modifikatorlarga ruxsat berish mavzusida aniqroq tushunib olasiz.

Keling sizlar bilan Field ga oid bir misol kurib chiqamiz.

```csharp
using System;

namespace Field
{
    public class Program
    {
        public static void Main(string[] args)
        {
            AboutField aboutField = new AboutField();
            aboutField.Firstname = "Abdulloh";
            aboutField.LastName = "Asronov";
            aboutField.Age = 25;
            aboutField.Printing();

        }
    }
    public class AboutField
    {
        public string Firstname;
        public string LastName;
        public int Age;
        
        public void Printing()
        {
            Console.WriteLine(Firstname + " " + LastName + " " + Age);
        } 
    }
}
```

Property ga keladigan bulsak u Hususiyat degan manoni bildiradi.

Uning Asosiy vazifasi malumot tashishdan iborat.

Property(Maydon) get(o'qishi), set(yozishi)  yoki private fieldan malumot olishda ishlatish mumkin.

Get  property qiymatini qaytarish uchun set esa yangi qiymat belgilashga xizmat qiladi.

Tassavvur qiling tepada aytib o'tganimizdek private faqat o'zi ochilgan class ichida foydalana olamiz. Agar uni qiymatini qolmoqchi bo'lsak quyidagi tarzda Propertyga yuzlanamiz:

```csharp
using System;

namespace Field
{
    public class Program
    {
        public static void Main(string[] args)
        {
            AboutProperty aboutProperty = new AboutProperty();
            Console.WriteLine(aboutProperty.FirsName);

        }
    }
    public class AboutProperty
    {
        private string firsname = "Abdullo";
        public string FirsName
        {
            get
            {
                return firsname;
            }
            set
            {
                firsname = value;
            }

        }
       
    }
}
```

Yuqorida private fielddan propertyga uni qiymati olinib Firstname Propertysiga yozilmoqda va biz buni tashqarida ishlatish imkoniga ham ega bo'lyabmiz.
Umid qilamanki bu sizga foydali bo'ldi!
