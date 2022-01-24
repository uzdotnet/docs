---
description: Mamataliyev Diyorbek
---
# Distinct

Distinct operatori berilgan to’plamdan elementlari takrorlanmaydigan yangi to’plam hosil qilish uchun ishlatiladi. Yangi hosil qilingan to’plamda ikkita bir xil element bo'lmaydi, to'plam elementlari tartiblanmagan holda bo’ladi.

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

Yuqoridagi misolda 50 dan kichik sonlar ichida 1, 2, 45 sonlari bir necha marta kelgan bo'lsa ham, **Distinct()** operatori qo'llangani uchun *newSonlar* to'plamiga *sonlar* to'plamidagi barcha elementlardan faqat bittadan olindi.

Endi biror class tipidagi obyektlar ustida **Distinct()** operatorini qo'llashni ko'raylik. Buning uchun classga `IEquatable` interfeysidan meros olib, ushbu interfeysga tegishli **Equals()** va **GetHashCode()** metodlarini qayta yozib olamiz:

```csharp
public class Talaba : IEquatable<Talaba>
{
    public string Name { get; set; }
    public int Weight { get; set; }

    public bool Equals(Talaba talaba)
    {

        // Taqqoslanayotgan obyektlarni null yoki null emasligini tekshirish
        if (Object.ReferenceEquals(talaba, null)) return false;

        // Taqqoslanayotgan obyektlar aynan bitta ma'lumotning havolasimi yoki yo'qligini tekshirish
        if (Object.ReferenceEquals(this, talaba)) return true;

        // Taqqoslanayotgan obyektlarning barcha xususiyat (property)lari bir xil ekanligini tekshirish
        return Weight.Equals(talaba.Weight) && Name.Equals(talaba.Name);
    }

    /* Agar Equals() metodi biror tekshirilayotgan juftlik true qiymat qaytarsa, 
    GetHashCode() metodi ham  bu juftlik uchun bir xil Code qaytarishi kerak: */

    public override int GetHashCode()
    {

        // Name xususiyatining qiymati null bo'lmasa, uning hesh-kodini olish
        int hashProductName = Name == null ? 0 : Name.GetHashCode();

        // Weight xususiyatining Hesh-kodini olish
        int hashProductCode = Weight.GetHashCode();

        // Talabaning hesh-kodini hisoblash
        return hashProductName ^ hashProductCode;
    }
}
```

Endi Talaba classi tipida massiv olib, uning ustida Distinct() operatorini qo'llashimiz mumkin. To'liq kod quyidagi ko'rinishda bo'ladi:

```csharp
using System;
using System.Linq;

public class program
{
    public static void Main()
    {
        Talaba[] talabalar = { new Talaba { Name = "Ali", Weight = 50 },
                       new Talaba { Name = "Vali", Weight = 61 },
                       new Talaba { Name = "Salim", Weight = 53 },
                       new Talaba { Name = "Ali", Weight = 50 },
                       new Talaba { Name = "Vali", Weight = 58 } };


        // Endi elementlari takrorlanmas to'plam hosil qilamiz

        //IEnumerable<Talaba> 
        var takrorlanmasToplam =
            talabalar.Distinct();

        foreach (var talaba in takrorlanmasToplam)
            Console.WriteLine(talaba.Name + " " + talaba.Weight);

       
        Console.ReadKey();

    }
    public class Talaba : IEquatable<Talaba>
    {
        public string Name { get; set; }
        public int Weight { get; set; }

        public bool Equals(Talaba talaba)
        {            
            if (Object.ReferenceEquals(talaba, null)) return false;
            if (Object.ReferenceEquals(this, talaba)) return true;
            return Weight.Equals(talaba.Weight) && Name.Equals(talaba.Name);
        }

        public override int GetHashCode()
        {
            int hashProductName = Name == null ? 0 : Name.GetHashCode();
            int hashProductCode = Weight.GetHashCode();
            return hashProductName ^ hashProductCode;
        }
    }
}
```

output: 
```
Ali 50
Vali 61
Salim 53
Vali 58
```

Yuqorida obyektlarni taqqoslash uchun **Equals()** va **GetHashCode()** metodlarini Talaba classi ichida qayta yozib qo'yaqoldik. Istasangiz bu metodlar bilan taqqoslash uchun yana boshqa class ochib, Talaba classiga bu sinfdan meros olib qo'yishingiz ham mumkin. (Odatda Comparer so'zi bilan tugaydigan nomdagi classlardan foydalanilardi). Qaysi usuldan foydalanish ixtiyoringiz.
