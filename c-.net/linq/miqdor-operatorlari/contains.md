---
description: Shohruh Nosirov
---

# Contains

   Bizga to’plam berilgan payti biz uning ichida berilgan element to’plamda mavjud yoki mavjud emasligini tekshirishimiz kerak bulsa bizga Contains() operatori kerak buladi.U bizga mantiqiy qiymat qaytaradi yani true yoki false . Agar berilgan element shu to’plamda mavjud bulsa true aks holda false qiymat qaytib keladi. <br/> 
 Bizga butun sonlardan iborat tuplam berilgan.Ularning orasida 5 soni mavjud ekanligini tekshirishimiz kerak

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


            bool bor = sonlar.Contains(5);
            Console.WriteLine("\nElementlar orasida 5 bor  ekanligini tekshiramiz:");

            if(bor)
            {
                Console.WriteLine("Bor");
            }
            else
            {
                Console.WriteLine("Yuq");

            }


            Console.ReadKey();


    }
}
```

Yuqoridagi kodni o’zingiz ham ishlatib kurgan bulsangiz “Bor” degan yozuv chiqqaniga guvoh bulasiz demak kodimiz to’g’ri ishlagan ekan. Chunki 5 elementi mavjud.


