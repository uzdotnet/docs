---
description: Jasurbek Sariboyev
---

# Max

Xo'sh do'stlar Linqda yana bir aggregat operator hisoblangan **Max()** va **Min()** metodlari mavjud. Ushbu metodlar sezib turganingizdek to'plamdagi eng katta va eng kichik raqamli elementni qaytaradi.

Keling bir to'plamda bu metodlarni ko'rib chiqamiz (quyidagi keltiriladigan misollarda Max() metodidan foydalaniladi, Min() metodini Max() metodi o'rnida o'zingiz ishlatib ko'rishingizni tavsiya beraman, ular bir xil ishlaydi): 

METHOD SYNTAX:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace maxMin 
{
    class Program
    {
        static void Main()
        {
            IList<int> list = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9,                   
                                                                10, 11 };
            
            var maxElement = list.Max();
            Console.WriteLine("Maksimum Element: {0}", maxElement);
            
            var maxElement1 = list.Max(l =>
            {
                if (l % 2 == 0)
                    return l;
                return 0;
            });
            
Console.WriteLine("Shartni qanoatlantirgan Maksimum Element: {0}", maxElement1);
        }
    }   
}
```
Output:
```
Maksimum Element : 11
Shartni qanoatlantirgan Maksimum Element :10
```
Yuqorida Max()ning 2 xil overload metodi keltirilgan.


Ushbu metoddan foydalanish juda ham oson. Keling buni yana bir misolda ko'rib chiqamiz, biroq bu safar murakkabroq to'plamdan foydalanamiz:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace maxMin 
{ 
class Program
{
    static void Main()
    {
        IList<Student> studentList = new List<Student>() {
        new Student() { StudentID = 1, StudentName = "Jasur", Age = 26 } ,
        new Student() { StudentID = 2, StudentName = "Muhammad", Age = 16 } ,
        new Student() { StudentID = 3, StudentName = "Temurxon", Age = 16 } ,
        new Student() { StudentID = 4, StudentName = "Toxirxon", Age = 27 } ,
        new Student() { StudentID = 5, StudentName = "umarbek", Age = 23 } ,
        new Student() { StudentID = 6, StudentName = "MuhammadKarim", Age = 24 }
            };
        var maxAge = studentList.Max(s => s.Age);
        Console.WriteLine("Maksimal yoshli o'quvchi yoshi: {0}", maxAge);
    }
}
    class Student
    {
        public int StudentID { get; set; }
        public string StudentName { get; set;}
        public int Age { get; set;}
    }
}
```
Output : 
```
Maksimal yoshli o'quvchi yoshi: 27 
```


Biz Max() metodidan ismlarni ham solishtirib eng uzunini chaqirib olishimiz mumkin. Buning uchun yuqoridagi murakkabroq misolimizning Student sinf(class)iga IComparable<Student> interfeysini qo'llab ko'ramiz:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace maxMin
{
    class Program
    {
        static void Main()
        {
	  // yuqorida keltirilgan studentList to'plamini chaqirib oling
        var maxValue = studentList.Max();
            Console.WriteLine("Ismi eng uzun o'quvchi: {0}", maxValue.StudentName);
        }
    }
    class Student:IComparable<Student>
    {
        public int StudentID { get; set; }
        public string StudentName { get; set; }
        public int Age { get; set; }

        public int CompareTo(Student other)
        {
             if(this.StudentName.Length > other.StudentName.Length)
              return 1;

            return 0;
        }
    }
}
```
Output : 
```
Ismi eng uzun o'quvchi: MuhammadKarim
```
  
Mana Max() metodi orqali ismlarni solishtirishni ham o'rganib oldingiz. Biroq bu sizga biroz qiyindek ko'rinishi mumkin. Keling endi buni osonlashtiramiz, qiyinidan - osoniga degandek. Biz yuqoridagi masalani hal qilishimiz uchun .Net 6 dan boshlab yangilik sifatida qo'shilgan **MaxBy()** (**MinBy()** ham mavjud) metodidan foydalanamiz. Bunda biz hech qanday interfeysdan foydalanmaymiz (baraka topishsin).
Keling buni ham bir misolda ko'rib chiqamiz:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace maxByMinBy
{
    class Program
    {
        static void Main()
        {
	     // yuqorida keltirilgan studentList to'plamini chaqirib oling
            var maxValue = studentList.MaxBy(s=>s.StudentName.Length);
            Console.WriteLine("Ismi eng uzun o'quvchi: {0}", maxValue.StudentName);
        }
    }
    class Student 
    {
        public int StudentID { get; set; }
        public string StudentName { get; set; }
        public int Age { get; set; }        
    }
}
```

Ushbu mavzu biroz kengayib ketdi, biroq tushunarli bo'ldi deb o'ylayman. Agar foydasi tekkan bo'lsa xursandman.
{% hint style="info" %}
Eslatma! C# da Max(),Min() metodlarini Query Syntaxda ifodalab bo'lmaydi.
{% endhint %}
