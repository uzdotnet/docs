---
description: Shohruh Nosirov
---

# Skip

Skip() methodi [Take()](https://docs.dot-net.uz/c-.net/linq/bolim-operatorlari/take) methodini teskarisi hisoblanadi. Demak Take() qanchadir elementni bizga olib berardi Skip()  esa shuncha elementni tashlab qolganlarini bizga qaytarib beradi. Endi sodda qilib tushuntiraman Diqqat qiling!!!<br/>
Take() bizga bir nechta elementni olib berarmidi. Endi bizga o’sha olgan elementlaridan keyin to’plamda qolgan elementlarni Skip() olib beradi.<br/>
Buni misolda kursayiz yanada yaxshiroq tushuncha olasiz.




```csharp
class Program
{
    static void Main(string[] args)
    {
        List<int> sonlar = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

            // Boshidagi 4 ta elementidan tashqari elemenlarini olamiz
            List<int> yangisonlar = sonlar.Skip(4).ToList();

            //Ekranga chiqaramiz
            Console.WriteLine("Boshlangich elementlar:");
           foreach(var i in sonlar)
            {
                Console.Write(i + " ");
            }

            Console.WriteLine("\nQolgan  elementlar:");
            foreach (var i in yangisonlar)
            {
                Console.Write(i + " ");
                    
           }


                Console.ReadKey();


    }
}
```
Bu dasturni albatta ishlatib kuring!!!<br/>
Endi sizda shunday muammolar yuzaga keladigan bulsa bemalol hijolat bulmasdan Skip() ga murojat qilishingiz mumkin.<br/>
Shu bilan Skip() methodi mavzuyimiz ham o’z nihoyasiga yetdi.



