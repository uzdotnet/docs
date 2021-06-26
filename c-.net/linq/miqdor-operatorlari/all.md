---
description: Shohruh Nosirov
---

# All

Bizga to’plam berilgan payti biz unga biror bir shartlarni bergan vaqtimiz uning ichidagi barcha elementlar shu shartga mos kelish kelmasligini tekshirib beruvchi All\(\) methodimiz mavjud.U bizga mantiqiy qiymat qaytaradi yani true yoki false .  
 Agar barcha elementlar shu shart mos kelsa true aks holda false qiymat qaytib keladi.  
 Bizga butun sonlardan iborat tuplam berilgan. Ularning barchasi juft ekanligini tekshirishimiz kerak.

```csharp
class Program
{
    static void Main(string[] args)
    {
         List<int> sonlar = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };


            //Ekranga chiqaramiz
            Console.WriteLine("Boshlangich elementlar:");
           foreach(var i in sonlar)
            {
                Console.Write(i + " ");
            }


            bool juft = sonlar.All(x => x % 2 == 0);
            Console.WriteLine("\nBarcha elementlar juft ekanligini tekshiramiz:");

            if(juft)
            {
                Console.WriteLine("Barchasi juft");
            }
            else
            {
                Console.WriteLine("Barchasi juft emas");

            }


            Console.ReadKey();




    }
}
```

Yuqoridagi kodni o’zingiz ham ishlatib kurgan bulsangiz “Barchasi juft emas” degan yozuv chiqqaniga guvoh bulasiz demak kodimiz to’g’ri ishlagan ekan. Chunki barcha elementlar juft emas. Toqlari ham mavjud.

