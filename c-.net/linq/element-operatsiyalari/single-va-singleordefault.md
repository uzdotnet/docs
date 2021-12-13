---
decription: Sirojiddinov Ahmadjon
---
# Single va SingleOrDefault

Element Operatorlarimizdan Keyingisi **Single()** va **SingleOrDefault()**. Bu methodlar ham avvalroq o'rganganlarimiz First va FirstOrDefault , Last va LastOrDefault
methodlari kabi ishlaydi, agarda siz ularni yaxshi o'zlashtirgan bo'lsangiz bu methodlar ham siz uchun kofe ichishdek gap :)

**Single()** methodinig vazifasi to'plamdagi yagona elementni qaytarish. Agar biz **Single()** methodga *lambda expression* orqali shart bersak shartga mos keladigan yagona elementni qaytaradi. 

Yodda tuting! Quyidagi holatlarda Single() methodini ishlatganimizda dasturimiz `System.InvalidOperationException` xatoligiga uchraydi:
1. To'plamda birdan ortiq element bo'lsa
2. To'plam bo'sh bo'lsa.
3. To'plamda Single() methodiga berilgan shartni qoniqtiradigan birdan ortiq element bo'lsa yoki birorta ham bo'lmasa.

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
namespace SingleMethod
{
    internal class Program
    {

        static void Main(string[] args)
        {
            List<int> num = new List<int>() { 5 };

            List<int> PhoneCodes = new List<int>() { 69, 90, 91, 93, 94, 97 };


            List<int> emptyList = new List<int>();

            Console.WriteLine("num o'zgaruvchisidagi Yagona element {0}", num.Single()); // 5
            

            Console.WriteLine("num o'zgaruvchisidagi 90 dan kichik yagona element {0}", PhoneCodes.Single(x => x < 90));   // 69


            // Quyidagi holatlarda bizga System.InvalidOperationException  qaytadi

            Console.WriteLine("Bo'sh toplam {0}", emptyList.Single());
            // System.InvalidOperationException chunki to'plam bo'm bosh

            Console.WriteLine(PhoneCodes.Single());
            // OUTPUT: System.InvalidOperationException Error chunki To'plamda birdan ortiq elementlar mavjud.

            Console.WriteLine($"PhoneCodes o'zgaruvchisidagi 90 dan katta sonlar {PhoneCodes.Single(y => y > 90)}");
            /* System.InvalidOperationException Error chunki PhoneCodes o'zgaruvchisida 90 dan katta
             bir nechta elementlar mavjud, bizga esa yagona element kerak. */
        }
    }
}
```

**SingleOrDefault()** methodi **Single()** methodi  bilan bir xil ishni bajaradi.

Ularning yagon farqi: 
**Single()** ishlatilganda to'plam bo'sh bo'lsa yoki berilgan shartga mos tushadigan element bo'lmasa `System.InvalidOperationException` xatoligi yuz beradi.
**SingleOrDefault()** esa yuqoridagi holatlarda *null* (yoki 0) qiymatini qaytaradi.

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
namespace SingleMethod
{
    internal class Program
    {

        static void Main(string[] args)
        {
            List<int> num = new List<int>() { 5 };

            List<int> PhoneCodes = new List<int>() { 69, 90, 91, 93, 94, 97 };

            List<int> emptyList = new List<int>();

            Console.WriteLine(num.Single());            // 5
            Console.WriteLine(num.SingleOrDefault());   //5

            Console.WriteLine(PhoneCodes.Single(a => a < 80));             // 69
            Console.WriteLine(PhoneCodes.SingleOrDefault(a => a < 80));    // 69

            Console.WriteLine("Bo'sh to'plam {0}", emptyList.Single());
            // OUTPUT:  System.InvalidOperationException Error chunki o'zgaruvchi bo'm bo'sh

            Console.WriteLine("Bo'sh to'plam {0}", emptyList.SingleOrDefault());  // OUTPUT:  0


            Console.WriteLine(PhoneCodes.Single(y => y < 69));
            // OUTPUT : System.InvalidOperationException Error chunki bunday element yo'q.

            Console.WriteLine(PhoneCodes.SingleOrDefault(y => y < 69));
            // OUTPUT : 0 chunki shartga mos tushadigan birorta ham element yo'q                     
        }
    }
}

```

Yuqorida ko'rib turganimizdek biz **Single()** va **SingleOrDefault()** funksiyalariga *lambda expression* methodi orqali shart berishimiz ham mumkin. Bu holatda **Single()** va **SingleOrDefault()**  to'plamdan shartga mos tushadigan yagona elementni qaytaradi. Agar shartni qoniqtiruvchi elementlar bir nechta bo'lsa bu ikkala method ishlatilganda ham "System.InvalidOperationException" xatoligi yuz beradi.

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
namespace SingleMethod
{
    internal class Program
    {

        static void Main(string[] args)
        {

            List<int> PhoneCodes = new List<int>() { 69, 90, 91, 93, 94, 97 };


            List<string> Weekdays = new List<string>() { "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" };

            Console.WriteLine("PhoneCodes o'zgaruvchisidagi 94 dan katta yagona son {0}", PhoneCodes.Single(x => x > 94));
            //OUTPUT: 97 chunki 94 dan boshqa katta son yo'q


            Console.WriteLine("Weekdays o'zgaruvchisidagi uzunligi 9 ga teng yagona element:  {0}", Weekdays.Single(y => y.Length == 9));  // Wednesday


            //ESLATMA.
            Console.WriteLine("Weekdays o'zgaruvchisidagi uzunligi 6 ga teng element {0}", Weekdays.SingleOrDefault(y => y.Length == 6));
            /* OUTPUT: System.InvalidOperationException Error chunki Weekdays to'plamida uzunligi 6 ga teng bolgan bir nechta elementlar bor
            ya'ni Monday, Friday, Sunday*/

        }
    }
}
```


!!! Esda tutish kerak bo'lgan fikrlar:
1. **Single()** to'plamdan yagona qiymatni olishda ishlatiladi.
2. **Single()** methodini ishlatganimizda quyidagi holatlarda System.InvalidOperationException qaytaradi:
	a. Agar To'plamda birorta element bo'lmasa ya'ni to'plam bo'sh bo'lsa.
	b. To'plam bir nechta elementdan tashkil topgan bo'lsa.

3. SingleOrDefault() methodi quyidagi holatlarda Default value qaytaradi
	a. Agar To'plam bo'sh bo'lsa ya'ni birorta ham element bo'lmasa.
	b. Shart berilgan holda shartni qoniqtiradigan birorta element bo'lmasa.

4. Qachonki biz **Single()** yoki **SingleOrDefault()** methodiga *lambda expression* orqali shart berganimizda bunday elementlar bir nechta bo'lsa `System.InvalidOperationException` qaytaradi
 
Yuqorida ishlatilgan Default value deganda odatda biz null yoki 0 qiymatni nazarda tutyapmiz.

E'tiboringiz uchun Rahmat. O'rganishda davom eting bo'lajak Software Engineerlar :)
