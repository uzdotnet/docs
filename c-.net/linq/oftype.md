---
description: Jasurbek Xasanboyev
---

# OfType

**OfType** kalit so’zi IEnumerable tipidagi ma’lumotlarni berilgan toifa bo’yicha filtirlaydi.

Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            var DataSource = new List<object>() { 'a', "Jasur", "Xondamir", 1, 2, 3, 4, };
            var selected = DataSource.OfType<string>();
            foreach (var item in selected)
            {
                Console.WriteLine(item);
            }
            // Output: Jasur, Xondamir
    }
}
```

Query syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            var DataSource = new List<object>() { 'a', "Jasur", "Xondamir", 1, 2, 3, 4, };
            var selected = from x in DataSource
                           where x is string
                           select x;
            foreach (var item in selected)
            {
                Console.WriteLine(item);
            }
            // Output: Jasur, Xondamir
    }
}
```

