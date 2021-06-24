---
description: Xasanboyev Jasurbek
---

# SelectMany

To’plam elementlarini **IEnumerable**  ga o’zlashtiradi va hosil bo’lgan ketma – ketlikni bitta kesamdek tasvirlaydi. Method ko’rinishi:

```csharp
 static void Main(string[] args)
        {
            List<string> strList = new List<string>() { "Jasurbek", "Xasanboyev" };
            var methodResult = strList.SelectMany(x => x).ToList();
            foreach (var item in methodResult)
            {
                Console.Write(item + " ");
            }
            //Output: J a s u r b e k X a s a n b o y e v 
 }
```

Query ko’rinishi o\`zi aslida vajud emas lekin quydagi ko’rinishda ifodalash mumkin:

```csharp
 static void Main(string[] args)
        {
            List<string> strList = new List<string>() { "Jasurbek", "Xasanboyev" };
            var methodResult = from res in strList
                               from ch in res
                               select ch;
            foreach (var item in methodResult)
            {
                Console.Write(item + " ");
            }
            //Output: J a s u r b e k X a s a n b o y e v 
 }
```

Asosan quydagi holatlar uchun ko’proq ishlatiladi:

```csharp
class Program
    {
        static void Main(string[] args)
        {
            List<Employee> employees = new List<Employee>()
            {
                new Employee(){Id = 1, Name = "Muhammadkarim", Email = "muhammadkarim@gmail.com", Programming = new List<string>(){"PHP", "C#", "SQL"} },
                new Employee(){Id = 2, Name = "Jasurbek", Email = "jasur@gmail.com", Programming = new List<string>(){"C++", "C#", "Arduino"}},
                new Employee(){Id = 3, Name = "Xondamir", Email = "xondamir", Programming = new List<string>(){"C#", "Python", "MVC"}}
            };
            var MethodSyntax = employees.SelectMany(x => x.Programming);
            foreach (var item in MethodSyntax)
            {
                Console.WriteLine(item);
            }
            //Output: PHP, C#, SQL, C++, C#, Arduino, C#, Python, MVC
        }
    }
    class Employee
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public string Email { get; set; }
        public List<String> Programming { get; set; }
    }
```

SelectMany bizga asosan ichma – ich ro’yhatlar bilan ishlashda qo’l keladi. Query syntaxdan ko’ra method syntaxdan foydalanishni tavsiya beraman chunki query uchun SelectMany yo’q ichma ich tanlab kirishga to’g’ri keladi.

