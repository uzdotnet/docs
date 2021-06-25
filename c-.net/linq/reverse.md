---
description: Jasurbek Xasanboyev
---

# Reverse

**Reverse** methodi ma’lumotlar tartibini teskarisiga o’zgartirish uchun ishlatiladi. 
Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
            var MethodSytax = numbers.Reverse<int>();
            foreach (var num in MethodSytax)
            {
                Console.WriteLine(num);
            }
            // Output: 10 9 8 7 6 5 4 3 2 1
    }
}
```

Query syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
            var QuerySyntax = (from num in numbers
                              select num).Reverse<int>();
            foreach (var num in QuerySyntax)
            {
                Console.WriteLine(num);
            }
            // Output: 10 9 8 7 6 5 4 3 2 1
    }
}
```

