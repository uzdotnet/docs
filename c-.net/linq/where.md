---
description: Xasanboyev Jasurbek
---

# Where

**Where** filtrlash kalit so’zi if shart operatori kabi ishlaydi. U bilan filtirlash jarayonida shart beriladi va bizga shartga to’g’ri keladigan varinatlarni [qaytaradi ](https://docs.dot-net.uz/c-.net/linq/filterlash-operatorlari). Ushbu filtrlash uslubi shart operatori kabi ishlagani uchun unda [mantiqiy operatorlar](https://docs.dot-net.uz/c-.net/basic/starter/operatorlar) dan ham foydalanishimiz mumkin. Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
        var MethodSyntax = numbers.Where(x => x > 4 && x < 7).ToList();
        foreach (var item in MethodSyntax)
        {
           Console.WriteLine(item);
        }
        // Output: 5, 6
    }
}
```

Query syntax

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            var MethodSyntax = from num in numbers
                               where num > 4 && num < 7
                               select num;
        foreach (var item in MethodSyntax)
        {
           Console.WriteLine(item);
        }
        // Output: 5, 6
    }
}
```

