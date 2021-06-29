---
description: Jasurbek Xasanboyev
---
# First va FirstOrDefault
**First** ingliz tilidan tarjima qiladigan bo\`lsak birinchi degan ma’noni anglatadi. O\`z nomidan ko\`rinib turibdiki bu metod to\’plamning birinchi elementini qaytaradi. Agar unga shart beradigan bo\`lsak ushbu shartga to\`g\`ri keladigan birinchi elementni qaytaradi. Quydagi misollar orqali buni yanada yaxshi tushunib olasiz degan umiddaman.

Method Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = numbers.First();
        Console.WriteLine(res); //OUTPUT: 1
    }
}
```
Query Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = (from num in numbers
                       select num).First();
        Console.WriteLine(res); //OUTPUT: 1
    }
}
```
Shartga mos keluvchi birinchi elementni topish:

Method Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = numbers.First(x => x > 6);
        Console.WriteLine(res); //OUTPUT: 7
    }
}
```
Query Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = (from num in numbers 
                      where num > 6 
                      select num).First();
        Console.WriteLine(res); //OUTPUT: 7
    }
}
```
Ro\`yxat bo\`sh bo\`lsa yoki shartni qanoatlantiruchi qiymat bo\`lmasa dastur hatolikka uchraydi. Bunday holat yuzaga kelmasligi uchun **FirstOrDefault** dan foydalanish tavsiya etiladi.
```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = numbers.FirstOrDefault(x => x > 9);
        Console.WriteLine(res); //OUTPUT: 0 demak bunday qiymat mavjud emas 
    }
}
```
