---
description: Mamataliyev Diyorbek
---

# Math sinfi

Assalomu alaykum, yosh dasturchilar. Dasturlashni o'rganar ekansiz, matematikaga ishingiz tushishi tabiiy hol. Aytaylik, dasturingizda biror formula yoki ifodaning qiymatini hisoblashga to'g'ri kelib qolishi mumkin. Xo'sh, bu holatlarda matematik ifodalarni dastur kodiga qanday kiritamiz? Ifoda ichida qo'shish (+), ayirish (-), ko'paytirish (`*`), bo'lish (/), qoldiqli bo'lish(%) dan tashqari boshqa amallar qatnashgan bo'lsa, qo'shimcha metodlardan foydalanishga to'g'ri keladi. Buning uchun bizga **Math** sinfi metodlari yordam beradi. Bu metodlarni chaqirish uchun **Math** so'zidan keyin nuqta qo'yib, metod nomini yozamiz. Metod turiga qarab bir yoki bir nechta qiymatni kiritganimizda bizga hisoblangan qiymatni qaytaradi. Masalan, **Math.Abs(-3.5)** metodi 3.5 ni qaytaradi. Endi esa, sizga ko'proq **Math** sinfi metodlarini tanishtirishga harakat qilaman.

**Math.Abs()** – sonning absolyut qiymati (moduli) ni hisoblaydi. Kiruvchi parametr sifatida kiritilgan bitta son ixtiyoriy sonli tipda bo'lishi mumkin, faqat 2^64 dan katta bo'lib ketmasligi kerak. Qaysi tipda (_double, decimal, long, int, .._) qiymat kiritilgan bo'lsa qaytarilgan qiymat ham shu tipda bo'ladi.

**Math.Acos()** – sonning arkkosinusini hisoblaydi. Kiruvchi va chiquvchi parametrlar faqat _double_ tipida bo'ladi. Qaytarilgan burchak qiymati radianda ifodalangan bo'ladi. Math.Acos(0)=1,5707963267948966.

**Math.Asin()** – sonning arksinusini hisoblaydi. Kiruvchi va chiquvchi parametrlar _double_ tipida bo'ladi. Qaytarilgan burchak qiymati radianlarda ifodalanadi. Math.Asin(1)=1,5707963267948966.

**Math.Atan()** – sonning arktangensini hisoblaydi. _double_ tipida ma'lumot qabul qiladi va qaytaradi. Qaytarilgan burchak qiymati radianlarda ifodalangan bo'ladi. Math.Atan(1)=0,7853981633974483.

**Math.BigMul()** – ikki butun sonning ko’paytmasini hisoblaydi. _int_ yoki _long_ tipida ma'lumot qabul qiladi. _long_ tipida qiymat qaytaradi. Masalan, Math.Bigmul(3,4)=12;

**Math.Cbrt()** - kiritilgan sonning kub ildizini hisoblaydi. _double_ tipida qiymat qabul qiladi va qaytaradi. Masalan, Math.Cbrt(27) ifoda bizga 3 ni qaytaradi.

**Math.Ceiling()** – sonni ortig'i bilan yaxlitlaydi. Kiritilgan sondan katta yoki unga teng bo'lgan eng yaqin butun sonni qaytaradi. _double_ yoki _decimal_ tipida ma'lumot qabul qiladi va qaytaradi. Math.Ceiling(3.14)=4, Math.Ceiling(6.0)=6; Math.Ceiling(-4.3)=-4;

**Math.Cos()** – burchakning kosinusini hisoblaydi. Burchak qiymati radianda kiritiladi. Kiruvchi va qaytariluvchi parametrlar faqat _double_ tipida bo'ladi. Math.Cos(3.141592653589793)=-1;

Keling, bu metodlarning qanday ishlashini ko'rish uchun kiritilgan sonning sinusini va kosinusini hisoblaydigan dastur yozib ko'ramiz:

```csharp
using System;
class Program
{
    static void Main(string[] args)
    {
        Console.Write("Burchakni radianda kiriting: ");
        double a = double.Parse(Console.ReadLine());
        Console.WriteLine("Sinus: "+Math.Sin(a));
        Console.WriteLine("Kosinus: "+Math.Cos(a));

        Console.ReadKey();
    }
}
```

**Math.Cosh()** – burchakning giperbolik kosinusini hisoblaydi. Faqat _double_ tipida ishlaydi.

**Math.E** – Math sinfining maydon (field)laridan biri. Fieldlar amal bajarish uchun emas, avvaldan belgilab qo'yilgan biror qiymatni qaytarish uchun ishlatiladi. Masalan, Math.E e sonining qiymatini _double_ tipida qaytaradi. e=2,718281828459045.

**Math.Exp()** - o'zgarmas e sonini kiritilgan darajaga ko'taradi va hosil bo'lgan qiymatni qaytaradi. Kiruvchi va chiquvchi qiymatlar _double_ tipida bo'ladi. Masalan, Math.Exp(1)=2,718281828459045; Math.Exp(2)=4,4816890703380645.

**Math.Floor()** - sonning butun qismi, kiritilgan sondan kichik yoki unga teng bo'lgan eng yaqin butun sonni qaytaradi. _double_ yoki _decimal_ tipida ma'lumot qabul qiladi va qaytaradi. Math.Floor(1.5)=1; Math.Floor(-1.5)=-2; Math.Floor(1.0)=1.

**Math.IEEERemainder()** - bir sonni boshqasiga bo'lgandagi qoldiqni hisoblaydi, faqat bu metodning ishlash algoritmi oddiy qoldiqnikidan boshqacharoq. a sonni b ga IEEERemainder orqali bo'lsak qoldiq `IEEERemainder(a,b) = a - (b * Math.Round(a / b))` umumiy formula bilan hisoblanadi. Ya'ni agar a/b ning kasr qismi 0.5 dan kichik bo'lsa IEEERemainder() ning qaytargan javobi oddiy qoldiq(a%b) bilan bir xil, aks holda a%b-b ga teng bo'ladi. Masalan, IEEERemainder(10,3)=-1; IEEERemainder(9,4)=1. Qiymat qabul qilish va qaytarish _double_ tipida bo'ladi.

**Math.Log()** - sonning logarifmini hisoblaydi. _double_ tipida ma'lumot qabul qiladi va qaytaradi. Ikki xil usulda ishlatish mumkin:

1. Agar bitta son kiritilsa shu sonning natural logarifmini hisoblaydi. Masalan, Math.Log(2,718281828459045) ifoda 1 ni qaytaradi.
2. Ikkita son Math.Log(a,b) ko'rinishida b asosga ko'ra a sonining logarifmini hisoblaydi. Math.Log(32,2) deb yozsak 2 asosga ko’ra 32 ning logarifmini hisoblab, bizga 5 ni qaytaradi.

**Math.Log10()** - sonning o’nli logarifmini hisoblaydi. Math.Log10(100) bizga 2 degan javobni qaytaradi. Qiymat qabul qilish va qaytarish _double_ tipida bo'ladi.

**Math.Log2()** - sonning 2 asosga ko'ra logarifmini hisoblaydi. _double_ tipida qiymat qabul qiladi va qaytaradi.

**Math.Max()** - ikki sondan kattasini aniqlab beradi. Kiruvchi parametr sifatida ixtiyoriy sonli tipdagi ikkita son kiritiladi, bizga ulardan kattasining qiymatini qaytaradi.

**Math.Min()** - ikki sondan kichigini topadi. Kiruvchi parametr sifatida ixtiyoriy sonli tipdagi ikkita son kiritiladi, bizga ulardan kichigining qiymatini qaytaradi.

**Math.PI** - bu Math sinfining yana bir maydon(field)i hisoblanadi. Pi sonining qiymati 3,14159265358979 ni _double_ tipida qaytaradi.

**Math.Pow(a,b)** - a sonini b-darajaga ko’taradi. Kiruvchi parametrda ikkita son asos va daraja _double_ tipida kiritiladi, bizga hisoblangan qiymatni qaytaradi. Masalan, Math.Pow(3,2) 9 ni qaytaradi.

**Math.Round()** - sonni yaxlitlaydi.

1. Agar kiruvchi parametrda bitta son Math.Round(a) ko’rinishida kiritilsa, a ni butun songacha yaxlitlangan qiymatini qaytaradi.
2. Agar ikkita son Math.Round(a,b) ko’rinishida kiritilsa, a sonni verguldan keyin b ta xonagacha yaxlitlangan qiymatini qaytaradi. Faqat haqiqiy (_double_,_decimal_) tipda qiymat qabul qiladi va qaytaradi.

**Math.ScaleB(x,n)** - `x*2^n` ifodaning qiymatini effektiv ravishda, yuqori tezlikda hisoblaydi. x soni _double_ tipida, n soni _int_ tipida bo'lishi kerak. Masalan, Math.ScaleB(3,4)=48.

**Math.Sign()** - sonning ishorasini aniqlab beradi. Agar son musbat bo’lsa 1 ni, manfiy bo’lsa -1 ni, nolga teng bo’lsa 0 ni qaytaradi. Kiruvchi parametr ixtiyoriy sonli tipda bo'lishi mumkin, lekin faqat int tipida qiymat qaytaradi.

**Math.Sin()** – burchakning sinusini hisoblaydi. Burchak qiymati radianda kiritiladi. Kiruvchi va qaytariluvchi parametrlar faqat _double_ tipida bo'ladi. Math.Sin(3.141592653589793)=0;

**Math.Sqrt()** - sonning kvadrat ildizini hisoblaydi. Kiritiladigan va qaytaradigan son _double_ tipida bo'ladi.

**Math.Tan()** - burchakning tangensini hisoblaydi. Burchak radianda kiritiladi. Kiruvchi va chiquvchi parametrlar faqat _double_ tipida bo’ladi. Masalan, Math.Tan(3.141592653589793) ifoda 0 ni qaytaradi.

**Math.Tanh()** - burchakning giperbolik tangensini hisoblaydi.

**Math.Tau** - Math sinfiga tegishli uchinchi field, o'zgarmas **tau** sonining qiymati 6,283185307179586 ni qaytaradi.

**Math.Truncate()** - bu metod ham sonning butun qismini hisoblaydi. Haqiqiy (_double_, _decimal_) tiplarda ishlaydi. Musbat sonlarda Math.Floor() bilan bir xil ishlaydi. Lekin ularning farqi manfiy sonlarda namoyon bo’ladi. -3.14 ning butun qismini olib ko’radigan bo’lsak, Math.Truncate(-3.14) ifoda -3 ni, Math.Floor(-3.14) ifoda esa -4 ni qaytaradi. Matematik tomondan butun qism olish uchun Math.Floor() to’la mos keladi, lekin shuni unutmangki, Math.Truncate() ni ham o’z o’rni bor.

Keling, yuqoridagi metodlarni qanday ishlashini kodda yana bir bor ko'rish uchun biror ifodani kodda yozib ko'ramiz. Aytaylik, a soni kiritilganda quyidagi ifodaning qiymatini hisoblashimiz kerak:

![ifoda](https://user-images.githubusercontent.com/91861166/137533450-80fcc47b-d82b-4a02-b152-4cac8bab370a.jpg)

Yechim quyidagicha bo'ladi:

```csharp
using System;
namespace ifoda
{
  class Program
  {
    static void Main(string[] args)
    {
        Console.Write("a=");
        double a = double.Parse(Console.ReadLine());
        double b = Math.Pow(Math.Floor(Math.Acos(Math.Abs(a) / (Math.Abs(a) + 1))), Math.PI) +
          Math.Exp(Math.Sin(Math.Log(Math.Log(a), 2)));
        Console.Write("Javob: " + b);
        Console.ReadKey();
    }
  }
}
```
