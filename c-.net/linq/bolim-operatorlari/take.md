---
description: Shohruh Nosirov
---

# Take

C\# 3.0 versiyasidan boshlab unga extension methodlar \(kengaytirilgan methodlar\) degan narsa qushilgan. Extension methodlar class obiektini o’zgartirmagan holatda yangi methodlar qushish imkonini beradi. Extension methodlar static classlarda e’lon qilinadi, o’zi ham static method buladi. System.Linq.Enumerable classida bir qancha extension methodlar bor ular Standart Query Operators\(Standart so'rov operatorlari\) deb ataladi. Bugun sizga usha methodlardan birini ko’rsatib o’taman. Ulardan biri Take\(\) extension methodi.Ketma-ketlikning boshidan boshlab ma'lum miqdordagi qo'shni elementlarni qaytaradi. To’plamlarni ajratish operatorlari ketma-ketlikni \(to'plamni\) ikki qismga ajratadi va qismlardan birini qaytaradi. Take \(\) kengaytmasi usuli birinchi elementdan boshlab belgilangan miqdordagi elementlarni qaytaradi.   
 Keling endi eng qiziqarli bo’limga o’ta qolamiz hadeb nazariya aytishdan men ham zerikdim. Menda butun turdagi 10 ta elementi mavjud List bor. Menga faqatgina boshidan boshlab 4 ta elementini olishni hoxladim. Buning uchun men sikl operatorlaridan foydalanib ham olishim mumkin edi. Yuq men ularni bezovta qilgim kelmadi aynan shunday ishlarni qiladigan Take\(\) methodini xizmatga chaqira qoldim.

```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> sonlar = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

            // Boshidagi 4 ta elementni olamiz
            List<int> yangisonlar = sonlar.Take(4).ToList();

            //Ekranga chiqaramiz
       Console.WriteLine("Boshlangich elementlar:");
           foreach(var i in sonlar)
            {
                Console.Write(i + " ");
            }

       Console.WriteLine("\nAjratib olingan elementlar:");
            foreach (var i in yangisonlar)
            {
                Console.Write(i + " ");

           }


                Console.ReadKey();

    }
}
```

Bu dasturni albatta ishlatib kuring!!!  
 Endi sizda shunday muammolar yuzaga keladigan bulsa bemalol hijolat bulmasdan Take\(\) ga murojat qilishingiz mumkin. Shu bilan Take\(\) methodi mavzuyimiz ham o’z nihoyasiga yetdi.

