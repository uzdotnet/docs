---
description: Mamataliyev Diyorbek
---
# Distinct

Distinct operatori berilgan to’plamdan elementlari takrorlanmaydigan yangi to’plam hosil qilish uchun ishlatiladi. Yangi hosil qilingan to’plam elementlari tartiblanmagan holda bo’ladi. 

Masalan, berilgan sonlar to’plamidan 50 dan kichik bo’lgan sonlarni olaylik. 

**Method Syntax:**
```csharp
using System;
using System.Linq;
namespace NetConsoleApp
{
  class Program
  {
    static void Main(string[] args)
    {
        int[] sonlar = new int[] { 1, 2, 1, 45, 3, 4, 32, 2, 1, 5, 91, 56, 45 };
        var takrorlanmasSonlar = sonlar.Where(e  =>  e < 50).Distinct();
        foreach (var item in takrorlanmasSonlar)
            Console.Write(item + " ");             
        Console.ReadKey();
    }
  }
}
```

output: 
```
1 2 45 3 4 32 5
```


**Mixed Syntax:**
```csharp
using System;
using System.Linq;
namespace NetConsoleApp
{
  class Program
  {
    static void Main(string[] args)
    {
        int[] sonlar = new int[] { 1, 2, 1, 45, 3, 4, 32, 2, 1, 5, 91, 56, 45 };
        var newSonlar = (from item in sonlar
                         where (item < 50)
                         select item).Distinct();
        foreach (var a in newSonlar)
        {
           Console.Write(a+" ");
        }
        Console.ReadKey();
    }
  }
}
```

output: 
```
1 2 45 3 4 32 5
```
