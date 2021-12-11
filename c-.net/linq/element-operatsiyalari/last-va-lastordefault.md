---
description: Sirojiddinov Ahmadjon
---
# Last va LastOrDefault

Assalomu alaykum, qadrli c# o'rganuvchilar. Biz sizlar bilan Linqning element operatsiyalarini o'rganayotgan edik. Qani endi o'rganishda davom etamiz.
Keyingi operatsiyamiz bu **Last** va **LastOrDefault**. Last() va LastOrDeafult extension methodlar hisoblanib, ularning vazifasi to'plamdagi eng oxirgi elementni qaytaradi. Shuningdek, bu methodlarni to'plamdagi biror shartga mos keluvchi elementlarning oxirgisini olish uchun ham ishlatishimiz mumkin. Qani endi so'z isboti bilan degandek buni kodda ko'ramiz :)
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
class Program
{
    static void Main(string[] args)
    {

        List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
        int lastNum = numbers.Last();
        Console.WriteLine(lastNum);     //OUTPUT : 10

        List<string> programLangs = new List<string>() { "C", "C++", "C#", "Java", "Python", "Javascript", "PHP" };
        string lastElement = programLangs.Last();
        Console.WriteLine(lastElement);      // OUTPUT : PHP


        List<int> emptyCollection = new List<int>();
        int empty = emptyCollection.Last();
        Console.WriteLine(empty);
        // To'plam bo'sh bo'lganligi uchun shu qismda "InvalidOperationExeption" xatoligi yuzaga keladi
    }
}
```

Yuqorida ko'rib turganimizdek, avvalgi ikkita to'plamning oxirgi elementlari 10 va PHP ekranga chiqarildi. Oxirgi qismda bo'sh bo'lgan to'plamning oxirgi elementini **Last()** orqali olishga uringanimiz uchun **InvalidOperationExeption** xatoligi yuzaga keldi.

Endi to'plamdan **Last()** methodi yordamida birorta shartga mos keluvchi oxirgi elementni olishni ko'raylik. Agarda bunday shartga to'g'ri keladigan element bo'lmasa yuqoridagi kabi **InvalidOperationExeption** xatoligi yuz beradi.

Demak shartni **Last()** methodi ichiga *Lambda Expression* yoki *Func delegati* yordamida  beramiz.
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 69, 90, 91, 93, 94, 97 };
        int lastNum = numbers.Last(x => x > 90);
        Console.WriteLine($"90 dan katta bolgan oxirgi element:  {lastNum}");     //97

        List<string> programLangs = new List<string>() { "C", "C++", "C#", "Java", "Python", "Javascript", "PHP" };
        string lastElement = programLangs.Last(x => x.Length > 5);
        Console.WriteLine(lastElement);      // OUTPUT : Javascript

        string lastElement2 = programLangs.Last(x => x.Length > 15);
        Console.WriteLine($"Uzunligi 15 dan katta bo'lgan oxirgi element:  {lastElement2}");      // InvalidOperationExeption
    }
}
```

Keyingi Methodimiz bu **LastOrDefault()**. **LastOrDefault()** methodi **Last()** methodi bilan deyarli bir xil ishlaydi. Yagona farq shundaki, agar to'plam 
bo'sh bo'lsa yoki shartga mos keladigan element topilmasa, *null* (sonli tiplarda 0) qaytaradi. 
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int>() { 2001, 2010, 2011, 2021, 2022 };

        int lastYear = numbers.Last(x => x > 2010);
        int lastYear2 = numbers.LastOrDefault(y => y > 2030);
        Console.WriteLine($"2010 dan katta bolgan oxirgi element {lastYear}");      //2022
        Console.WriteLine($"2030 dan kattasi yo'q, shuning uchun Default qiymat : {lastYear2}");   // 0 (shartga mos element bo'lmagani uchun)

        List<string> programLangs = new List<string>() { "C", "C++", "C#", "Java", "Python", "Javascript", "PHP" };        
        string lastElement2 = programLangs.LastOrDefault(y => y.StartsWith('O'));
        string lastElement = programLangs.LastOrDefault(x => x.Length > 9);        
        Console.WriteLine(lastElement2);        // OUTPUT : null
        Console.WriteLine(lastElement);         // OUTPUT : Javascript          
    }
}
```



**QISQACHA TAKRORLASH:**
**Last()** metodi to'plamdagi oxirgi elementni qaytaradi. Uni lambda ifodasi yoki Func delegati yordamida belgilangan shartga mos keladigan oxirgi elementni qaytarish uchun ham ishlatsa bo'ladi. Agar berilgan to'plam bo'sh bo'lsa yoki shartga mos elementni o'z ichiga olmasa,  u **InvalidOperationExeption** istisnosini chiqaradi.


**LastOrDefault()** metodi **Last()** metodi bilan bir xil ishni bajaradi. Yagona farq shundaki, agar to'plam bo'sh bo'lsa yoki shartga mos element topilmasa, *null* (yoki 0) qiymat qaytaradi.


Tushunarli bo'ldi degan umiddaman. Keyingi darslarda ko'rishguncha :) 
