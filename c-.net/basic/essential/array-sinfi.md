---
description: Mamataliyev Diyorbek
---

# Array sinfi

Assalomu alaykum, yosh dasturchilar! Bugun sizlar bilan **Array** abstrakt sinfiga tegishli bo’lgan bir nechta standart metod va funksiyalarni o’rganamiz. Ulardan foydalanib, bir o'lchamli massivlar ustida turli amallarni osonlik bilan bajarishingiz mumkin bo'ladi. Darsga tayyor bo'lsangiz, boshladik.

Array abstrakt sinfi System nomlar fazosida joylashgan. Bu sinf metodlariga murojaat qilish uchun **Array** kalit so’zidan keyin nuqta qo’yib, metod nomini yozamiz. Masalan, **Array.Sort\(A\);**

## **Array.Exists\(\)**

Bu metod bizga massiv ichida berilgan shartga mos keluvchi element bor yoki yo’qligini aniqlab beradi. Kiruvchi parametr sifatida avvalroq e’lon qilingan bir o’lchamli massiv nomi va **lambda ifoda** kiritiladi. Lambda ifoda tekshirish uchun shart vazifasini bajaradi. Agar massivda biz bergan shartga mos keluvchi bir yoki bir nechta element mavjud bo’lsa bu metod bizga true qiymatini, aks holda false qiymatini qaytaradi. Keling, uning qanday ishlashini kodda ko’ramiz:

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

a&gt;10

Manfiy son yo'q

Yes

True

Yuqoridagi misolda ishlatilgan a, e, w o’zgaruvchilari massiv elementlarini lambda ifoda ichida ifodalash uchungina ishlatilib, kodning boshqa qismida foydalanilmagan bo’lishi kerak.

## **Array.Sort\(\)**

Agar siz massivlarga doir masala ishlagan bo’lsangiz, massiv elementlarini o’sish tartibida tartiblash haqida bosh qotirib ko’rgan bo’lsangiz kerak. Baxtingizga, **Array** sinfida buning uchun ham tayyor funksiya bor. **Array.Sort\(\);** qavsi ichiga e’lon qilingan massiv nomini yozsangiz kifoya. Keling, buni ham kodda ko’ramiz:

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

Nafaqat sonlarni, **string** tipidagi ma’lumotlarni ham tartiblashimiz mumkin. Bu holatda elementlar alifbo tartibida tartiblanadi:

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

output: c\#; c++; delphi; go; java; paskal; python; ruby;

Massivning faqat bir qismini o’sish tartibida tartiblab, qolgan elementlarni o’zgarishsiz qoldirish imkoniyati ham bor. Buning uchun uchta qiymat kiritiladi: massiv nomi, tartiblash boshlanadigan indeks, tartiblanadigan elementlar soni:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] MyNewArray={3,2,6,1,9}; 

            Array.Sort(MyNewArray,2,3);            
            foreach(int a in MyNewArray){
                Console.Write(a+" ");        
            }        

            Console.ReadKey();
        }
    }
}
```

output: 3 2 1 6 9

## **Array.IndexOf\(\)**

Aytaylik, siz massivdagi biror elementning qaysi indeksda turishini bilmoqchisiz. Bu vazifani bajarish uchun bittagina metodni chaqirib indeksni olishingiz mumkin. Bu metodning nomi **Array.IndexOf\(\)**. Kiruvchi parametr sifatida uning qavsi ichiga e’lon qilingan bir o’lchovli massiv nomi va qidirilayotgan element yoziladi. Agar bu element massivda mavjud bo’lsa uning massivdagi indeksi \(tartib raqami\) ni, aks holda -1 ni qaytaradi. Agar xohlasangiz elementni butunlay massivdan emas, uning bir qismidan ham qidirishingiz mumkin. Eslatib o’taman, massivda indekslash 0 dan boshlanadi. Keling, ko’p gapirmay shularni kodda ko’ramiz:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] MyArray={0,4,3,2,6,1,8,9,11};
            Console.Write(Array.IndexOf(MyArray,2)+"; ");    // 2 ga teng element indeksini qaytaradi

            Console.Write(Array.IndexOf(MyArray,10,3)+"; ");   /*  10 ga teng elementni 3-indeksdan boshlab oxirigacha qidiradi */

            Console.Write(Array.IndexOf(MyArray,6,1,4));   /* 6 ga teng bo'lgan elementni 1-indeksdan boshlab 4 ta elementgacha bo'lgan oraliqda qidiradi */

            Console.ReadKey();
        }
    }
}
```

output: 3; -1; 4

## **Array.BinarySearch\(\)**

Ana endi sizlar bilan o’sha mashxur binar qidiruv algoritmi haqida gaplashamiz. Agar massivda shu algoritm yordamida elementni qidirmoqchi bo’lsangiz, buning ham yo’li oson. Array sinfida buning uchun ham tayyor standart metod mavjud. **Array.BinarySearch\(\)** metodi ham huddi **Array.IndexOf\(\)** metodiga o’xshaydi. Agar kiritilgan element massivda mavjud bo’lsa shu element indeksini, aks holda biror manfiy sonni qaytaradi. Unda yana bitta metodning nima keragi bor, deb o’ylayotgan bo’lsangiz javob beraman: binar qidiruvning asosiy ustunligi uning ishlash tezligi yuqoriligida. IndexOf\(\) metodi bilan kerakli elementni topish uchun ko’pi bilan O\(n\) vaqt sarflaysiz \(n - elementlar soni\), BinarySearch\(\) da esa O\(log2\(n\)\) vaqt. Bu farqni tasavvur qilish uchun bir misol: 1024 ta elementga ega massivdan kerakli elementni topish uchun IndexOf\(\) metodi O\(1024\) vaqt, BinarySearch O\(10\) vaqt sarflaydi. Ya’ni binar qidiruvning ishlash tezligi juda yuqori hamda bu farq elementlari soni ko’p bo’lgan massivlarda yaqqol seziladi.

{% hint style="info" %}
_**Eslatma:** **BinarySearch\(\)** metodi to’g’ri ishlashi uchun unga kiritilayotgan massiv o’sish tartibida tartiblangan bo’lishi shart !._
{% endhint %}

Binar qidiruvni sizga shuncha maqtadim, endi kodda ham ko’raylik:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] MyArray={0,4,3,2,6,1,8,9,11};
            Array.Sort(MyArray);  //massiv {0,1,2,3,4,6,8,9,11} ko'rinishida tartiblandi
            Console.Write(Array.BinarySearch(MyArray,2)+"  ");    // 2 ga teng element indeksini qaytaradi

            Console.Write(Array.BinarySearch(MyArray,10)+"  ");   /*  10 ga teng elementni 3-indeksdan boshlab oxirigacha qidiradi */

            Console.Write(Array.BinarySearch(MyArray,0,8,6));   /* 6 ga teng bo'lgan elementni 1-indeksdan boshlab 4 ta elementgacha bo'lgan oraliqda qidiradi */

            Console.ReadKey();
        }
    }
}
```

output: 2 -9 5

## **Array.Clear\(\)**

Massivlarda ma’lumotlarni saqlash bilan birga ularni kerak paytda o’chira olish ham kerak. Agar siz butun bir massivni yoki uning bir qismidagi elementlarni birdaniga o’chirmoqchi bo’lsangiz, bunda sizga **Array.Clear\(\)** metodi yordam beradi. Kiruvchi parametr sifatida massiv nomi, o’chirishni nechinchi indeksdan boshlashingiz va nechta elementni o’chirishingizni kiritishingiz kerak. **Array.Clear\(\)** metodi bilan massiv elementlari o’chirilganda massivning o’lchami o’zgarmaydi, o’chirilgan elementlar 0 \(string da null\) ga teng bo’lib qoladi. Masalan:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] MyArray={0,4,3,2,6,1,8,9,11};
            Array.Clear(MyArray,2,4);    // 2-indeksdan boshlab 4 ta elementni o'chirish
            foreach (int a in MyArray) {
                Console.Write(a+" ");
            }

            Console.WriteLine();

            Array.Clear(MyArray,0,9); // 0-indeksdan boshlab 9 ta elementni, ya'ni hammasini o'chirish 
            foreach (int b in MyArray) {
                Console.Write(b+" ");
            }
            Console.ReadKey();
        }
    }
}
```

output:

0 4 0 0 0 0 8 9 11

0 0 0 0 0 0 0 0 0

## **Array.Reverse\(\)**

Bu funksiya massiv elementlarini teskari tartibda joylashtirib beradi. Masalan, {2,3,5} ko’rinishidagi massivni {5,3,2} ko’rinishiga o’tkazadi. **Array.Reverse\(\)** ni ikki xil usulda ishlatish mumkin. Agar kiruvchi parametr sifatida faqat massiv nomi kiritilsa shu massivning barcha elementlarini teskari tartiblaydi. Yoki agar uchta parametr: massiv nomi, almashtirish boshlanadigan indeks, almashtiriladigan elementlar soni kiritilsa massivning shu qismidagina elementlarni qayta tartiblaydi.

Misol uchun:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] tub_sonlar={2,3,5,7,11,13,17,19,23,29};

            Array.Reverse(tub_sonlar);               
            foreach(int a in tub_sonlar){
                Console.Write(a+" ");
            }
            Console.WriteLine();

            Array.Reverse(tub_sonlar,2,5); 
            foreach(int b in tub_sonlar){
                Console.Write(b+" ");
            }

            Console.ReadKey();
        }
    }
}
```

output:

29 23 19 17 13 11 7 5 3 2

29 23 7 11 13 17 19 5 3 2

## **Array.TrueForAll\(\)**

Aytaylik, sizga biror massiv berilib, savol qo’yilgan: massivning barcha elementlari musbatmi? Barcha elementlar juftmi? Barcha elementlar uzunligi 5 dan kattami? .. va hokazo. Tinib-tinchimagan dasturchilar shu holat uchun ham tayyor standart metod yozib qo’yishibdi. Ko’rdingizmi, qanchalik qulay tilni o’rganyapsiz. Ha aytgancha, metodga qaytamiz. Array.TrueForAll\(\) metodiga kiruvchi parametr sifatida massiv nomi va lambda ifoda kiritiladi. Lambda ifoda elementlarni tekshirish uchun shart vazifasini bajaradi. Agar massivning barcha elementlari ushbu shartni qanoatlantirsa metod bizga true qiymat, aks holda, shartga mos kelmaydigan bir yoki bir nechta element mavjud bo’lsa false qiymatini qaytaradi. Yuqoridagilarni yaxshiroq tushunishingiz uchun bu funksiyaning dasturda yozilishi:

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] tub_sonlar={2,3,5,7,11,13,17,19,23,29};
            Console.WriteLine(Array.TrueForAll(tub_sonlar,e => e>0));          // True
            Console.WriteLine(Array.TrueForAll(tub_sonlar,a => a%2==0));     // False
            Console.WriteLine(Array.TrueForAll(tub_sonlar,a => a%2==1));      // False

            string [] ism={"Salim", "Sardor", "Sanjar"};
            Console.WriteLine(Array.TrueForAll(ism, s => s.StartsWith("S"))?"YES":"NO");  // YES so'zi chop etiladi

            if (Array.TrueForAll(ism, w => w.Length==5)) Console.Write(5);
            else Console.WriteLine("No");                                           //  No chop etiladi
            Console.ReadKey();
        }
    }
}
```

## **Array.Resize\(\)**

Bu funksiya massivning o’lchamini o’zgartirish uchun ishlatiladi. Kiruvchi parametr sifatida massiv nomi va yangi o’lcham kiritiladi. Natijada massivning o’lchami o’zgaradi. Qavs ichidagi massiv nomidan avval **ref** kalit so’zi yozilishi kerak. Agar massivning yangi o’lchami avvalgisidan kichik bo’lsa, elementlar massivning oxirgi elementidan boshlab to kerakli o'lchamga kelgunicha o'chiriladi. Agar yangi o’lcham eskisidan kattaroq bo’lsa, yangi elementlar massivga oxiridan qo’shilib, qiymati 0 \(null\) ga teng bo’ladi.

```csharp
using System;
namespace NewApplication
{
    class Program
    {
        public static void Main(string[] args)
        {        
            int [] MyNewArray={3,2,6,1,9}; 
            Array.Resize(ref MyNewArray,3);
            foreach(int a in MyNewArray){
                Console.Write(a+" ");
            }
            Console.WriteLine();

            Array.Resize(ref MyNewArray,7);
            foreach(int b in MyNewArray) {
                Console.Write(b+" ");
            }
            Console.ReadKey();
        }
    }
}
```

output:

3 2 6

3 2 6 0 0 0 0

Bu mavzudan sizga foydali nimadir o’rgata olgan bo’lsam xursandman. E’tiboringiz uchun rahmat.

