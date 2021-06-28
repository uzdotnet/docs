---
description: Shohruh Nosirov
---

# SkipWhile

Biz Skip\(\) operatori haqida bilib oldik endi uning akasi SkipWhile\(\) haqida gaplashamiz. SkipWhile\(\) bizga Skip\(\) qilolmaydigan ishlarni qilishga yordam beradi. Endi tasavvur qilamiz bizda qandaydir top’lam berilgan. Men shu to’plamdan boshidan boshlab nechtadir elementni qandaydir shartni qanoatlantiradiganlarini tashlab yuborishni hoxladim. Shunda bizga SkipWhile\(\) kerak buladi.  
 Masalan butun sonlardan iborat List berilgan men uning ichidan juft elementlarini tashlab yuborib qolganlarini olmoqchiman.

```csharp
class Program
{
    static void Main(string[] args)
    {
                   List<int> sonlar = new List<int>() { 2, 2, 3, 4, 5, 6, 7, 8, 9, 10 };


            //Ekranga chiqaramiz
            Console.WriteLine("Boshlangich elementlar:");
           foreach(var i in sonlar)
            {
                Console.Write(i + " ");
            }


            var yangisonlar = sonlar.SkipWhile(x=>x%2==0);
            Console.WriteLine("\nYangi elementlari:");

            foreach(var i in yangisonlar)
            {
                Console.Write(i + " ");
            }


            Console.ReadKey();



    }
}
```

Dastur natijasiga e’tibor bergan bulsayiz bizga 2 2 dan tashqari barcha elementlarni qaytarib berdi ularning orasida juft elementlar ham bor edi. SkipWhile\(\) shart bajarilmay qolgandan keyin boshqa elementlarni umuman tekshirib kurmaydi. Buning ham TakeWhile\(\) ga uxshab bittagina joni bor xolos. Shuning uchun boshidagi 2 ta elementdan tashqari barchasini qaytarib berdi. Agar bizda juft elementdan boshlanmaganda bizga barcha elementlarni qaytarib bergan bular edi.  
 Shu bilan SkipWhile\(\) mavzuyimiz ham nihoyasiga yetdi.

