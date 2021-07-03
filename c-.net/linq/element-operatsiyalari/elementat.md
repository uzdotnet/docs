---
description: Jasurbek Xasanboyev
---

# ElementAt

**ElementAt** metodiga parameter sifatida biror index ni kiritsak o\`sha index dagi elementni qaytaradi. Oddiy massivda index bo\`yicha murojaat bor lekin list va shunga o\`shash ba’zi to\`plamalar mavjud emas shunday holatda bizga ushbu metod qo\`l keladi. Agar biz bergan index mavjud bo’lmasa dastur hatolikka uchraydi. Shunday holatlarni oldini olish maqsadida **ElementAtOrDefault** metodi yordam beradi. Avvalgi darsdagi **DefaultEmpty** kabi bu metod ham index mavjud bo\`lmagan holatda **null** qiymat qaytaradi dastur esa hatoliksiz ishlayverdi.

Method Syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
        int res = numbers.ElementAt(5);
        Console.WriteLine(res); // OUTPUT: 6
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
                   select num).ElementAt(5);
        Console.WriteLine(res); // OUTPUT: 6
    }
}
```

Quydagi holatda esa hatolikka uchraydi, chunki 10-index mavjud emas

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = numbers.ElementAt(10);
        Console.WriteLine(res);
    }
}
```

![image](https://user-images.githubusercontent.com/81855769/123847020-7e43e080-d92f-11eb-9cb5-517ecf6012b6.png)

Bunday holatga uchramaslik uchun quydagicha yo’l tutamiz:

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            int res = numbers.ElementAtOrDefault(10);
        Console.WriteLine(res); //OUTPUT: 0
    }
}
```

