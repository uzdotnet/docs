---
description: Mamataliyev Diyorbek
---

# Array sinfi
Assalomu alaykum, yosh dasturchilar! Bugun sizlar bilan **Array** abstrakt sinfiga tegishli bo’lgan bir nechta standart metod va funksiyalarni o’rganamiz. Ulardan foydalanib, bir o'lchamli massivlar ustida turli amallarni osonlik bilan bajarishingiz mumkin bo'ladi. Darsga tayyor bo'lsangiz, boshladik.

Array abstrakt sinfi System nomlar fazosida joylashgan. Bu sinf metodlariga murojaat qilish uchun **Array** kalit so’zidan keyin nuqta qo’yib, metod nomini yozamiz.  Masalan, **Array.Sort(A);**

### **Array.Exists()**

Bu metod bizga massiv ichida berilgan shartga mos keluvchi element bor yoki yo’qligini aniqlab beradi. Kiruvchi parametr sifatida avvalroq e’lon qilingan bir o’lchamli massiv nomi va __lambda ifoda__ kiritiladi. Lambda ifoda tekshirish uchun shart vazifasini bajaradi. Agar massivda  biz bergan shartga mos keluvchi bir yoki bir nechta element mavjud bo’lsa bu metod bizga true qiymatini, aks holda false qiymatini qaytaradi. Keling, uning qanday ishlashini kodda ko’ramiz:
```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {
            int [] sonlar={2,4,6,8,11,14,15};
            
            if (Array.Exists(sonlar, a => a>10)) Console.WriteLine("a>10");
            else Console.WriteLine("a<10");
            
            if (Array.Exists(sonlar, e => e<0)) Console.WriteLine("Manfiy son bor");
            else Console.WriteLine("Manfiy son yo'q");
            
            if (Array.Exists(sonlar,w => w%2==0 && ((w>15)||(w<3)))) Console.WriteLine("Yes");
            else Console.WriteLine("No");
            
            string [] qurilmalar={"protsessor","monitor","videokarta","klaviatura"};
            Console.WriteLine(Array.Exists(qurilmalar, t => t.StartsWith("v") && t.EndsWith("a")));
            
            Console.ReadKey();
        }
    }
}
```
output: 
a>10
Manfiy son yo'q
Yes
True

Yuqoridagi misolda ishlatilgan a, e, w o’zgaruvchilari massiv elementlarini lambda ifoda ichida ifodalash uchungina ishlatilib, kodning boshqa qismida foydalanilmagan bo’lishi kerak.


### **Array.Sort()**

Agar siz massivlarga doir masala ishlagan bo’lsangiz, massiv elementlarini o’sish tartibida tartiblash haqida bosh qotirib ko’rgan bo’lsangiz kerak. Baxtingizga, **Array** sinfida buning uchun ham tayyor funksiya bor. **Array.Sort();** qavsi ichiga e’lon qilingan massiv nomini yozsangiz kifoya. Keling, buni ham kodda ko’ramiz:
```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {
            int [] raqamlar={5,2,8,4,0,1,7};
            Array.Sort(raqamlar);
            foreach (int b in raqamlar)
            {
                Console.Write(b+" ");
            }       
             Console.ReadKey();
        }
    }
}
```
output: 0 1 2 4 5 7 8

Nafaqat sonlarni, __string__ tipidagi ma’lumotlarni ham tartiblashimiz mumkin. Bu holatda elementlar alifbo tartibida tartiblanadi:
```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            string [] languages={"c#", "delphi", "paskal", "ruby", "python","c++","java","go"};
            Array.Sort(languages);
            foreach (string c in languages) {
                Console.Write(c+"; ");
            }
            Console.ReadKey();
        }
    }
}
```
output: c#; c++; delphi; go; java; paskal; python; ruby;

