---
description: Shohruh Nosirov
---

# Any

Bizga to’plam berilgan payti biz unda bazi shartlarga javob beradigan bironta element bor yoki yuqligini bilishni hoxlasak bizga Any() methodi yordamga keladi.  U  bizga mantiqiy qiymat qaytaradi yani true yoki false.<br/>
Bizga butun sonlardan iborat tuplam berilgan. Ularning orasida birorta juft element bor yoki yuqligini tekshirishimiz kerak.

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

           //Juft son bor yoki yuqligini tekshirish sharti
            bool juft_bor = sonlar.Any(x => x % 2 == 0);
            Console.WriteLine("\nBirorta juft element bor yoki yuqligini tekshiramiz:");

            if(juft_bor)
            {
                Console.WriteLine("Bor");
            }
            else
            {
                Console.WriteLine("yuq");

            }


            Console.ReadKey();



    }
}
```

Yuqoridagi kodni o’zingiz ham ishlatib kurgan bulsangiz “Bor” degan yozuv chiqqaniga guvoh bulasiz demak kodimiz to’g’ri ishlagan ekan.


