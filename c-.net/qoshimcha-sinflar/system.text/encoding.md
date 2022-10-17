---
description: Mamataliyev Diyorbek
---

# Encoding

Encoding sinfi bilan tanishishdan avval, keling kodlash (encoding) turlari haqida biroz tushuncha olsak.

Yaxshi bilasizki, kompyuter xotirasida barcha ma’lumotlar 0 va 1 orqali ifodalanadi (xotira katakchalari doim ikkita holatdan birini qabul qilgani uchun shartli ravishda shunday belgilanadi). Agar biror sonli o’zgaruvchining qiymatini xotiraga saqlab turmoqchi bo’lsak, sonni ikkilik sanoq sistemasiga o’tkazib saqlanadi.

Masalan, 13 sonining ikkilikdagi ko’rinishi 1101 ni saqlash uchun 4 bit yetarli bo’ladi. (0 yoki 1 ni qabul qiladigan bitta xonaning hajmi 1 bit hisoblanadi). Agar bu sonni 16 bit kattalikdagi butun son (int16) sifatida saqlamoqchi bo’lsak, 0000000000001101 ko’rinishida nollar bilan to’ldiriladi.

Agar sonni emas, biror belgini yoki belgilardan tashkil topgan satrni saqlamoqchi bo’lsakchi?

### ASCII
![ASCII jadvali](https://user-images.githubusercontent.com/91861166/196095625-c8a04828-7a6f-41a5-836b-b0ebd380f1b9.png)

Dastlab bu muammoni hal qilish uchun 1963-yilda ASCII (American Standart Code Information Interchange) jadvali ishlab chiqildi. Bu jadvalga 128 ta belgi kiritilgan bo’lib, ular 0 dan 127 gacha raqamlangan. Jadvaldan foydalangan holda xotiraga yozish uchun har bir belgiga mos keladigan raqam ikkilik sanoq sistemasiga o’tkazib xotiraga yozilgan. 0 dan 127 gacha bo’lgan sonlarning ikkilikdagi ko’rinishi maksimum 7 xonali bo’ladi. Demak, bu sonlarni ifodalash uchun xotiradan 7 bit xotira ajratiladi. Bundan tashqari, kengaytirilgan ASCII jadvallari ham mavjud bo’lib, bunday jadvallarda belgilar 0 dan 255 gacha raqamlarga mos qo’yilgan. Ularning barchasida dastlabki 128 ta belgi ketma-ketligi bir xil, keyingi 128 ta joyga boshqa tillardagi harflarni joylashga harakat qilishgan. Ko’pgina kompaniyalar o’zi uchun alohida kengaytirilgan jadvalni hosil qilishgani uchun, keyingi 128 ta belgining turlicha talqinlari paydo bo’lib, bu ham muammolarga sabab bo’lgan. Kengaytirilgan ASCII jadvallarida belgi xotiradan 8 bit = 1 bayt joy egallaydi.

Xulosa:

• ASCIIda belgilar 0-127 (yoki 0-255) oralig’idagi mos raqamlar orqali kodlanadi;

• Bu tizimda har qanday belgini kodlash uchun o’zgarmas uzunlikdagi 7 bit (kengaytirilganida 8 bit) xotira ajratiladi;

• ASCII orqali ko’pi bilan 256 xil belgini ifodalash mumkin xolos.

### UTF-32

ASCII dan foydalanib belgilarni kodlash imkoniyati paydo bo’lgan bo’lsada, hali jadvalga kiritilmagan minglab belgilar bor edi: matematik formulalarda ishlatiladigan grek harflari (α, β …), yapon, xitoy va boshqa tillardagi harflar, smayliklar, … . Shuning uchun avvalgi jadvalni kengaytirish zarurati paydo bo’ldi va UTF (Unicode Transformation Format) yaratildi. UTF-32 da har bitta harf 32 bit = 4 bayt xotiraga yoziladi.

Avvalgi muammo hal etildi, insonlar ishlatadigan barcha belgilar jadvalga kiritildi. Biroq, har bitta belgini 4 bayt joy band qilishi biroz qimmatga tushardi: bu usul avvalgi holga nisbatan 4 barobar ko’proq xotirani band qilardi. Xotiradan foydalanishni kamaytirish maqsadida o’zgaruvchan usulda kodlash tizimlari – UTF-16, keyinroq UTF-8 ishlab chiqildi.

### UTF-16

UTF-32 da 32 bit xotiraga yozilayotgan harflarning ba’zilarini aslida 16 bit joyga yozish ham mumkin. Masalan, 1110111011 sonini UTF-32 da 00000000000000000000001110111011 ko’rinishida yoziladi, holbuki u 16 bitga ham sig’adi: 0000001110111011. UTF-16 tizimida belgi tartib raqamining ikkilikdagi ko’rinishi uzunligi 16 dan kichik bo’lsa 16 bit xotiraga, aks holda 32 bit xotiraga yoziladi. Bu usul xotiradan yutishga imkon bersada, hozirda u ham UTF-32 kabi deyarli ishlatilmaydi. Chunki, bundan ham optimalroq UTF-8 tizimi bor.

Xulosa:

• UTF-16 da belgilar o’zgaruvchan uzunlikda, 2 yoki 4 bayt xotiraga kodlanadi. Agar sonni 2 baytga sig’dirish imkoni bo’lsa 2 baytga, aks holda 4 bayt joyga yoziladi.

### UTF-8

Bu usul xotiradan yanada ko’proq yutishga harakat qiladi. Agar jadvaldagi belgining tartib raqami ikkilikdagi uzunligi 8 dan kichik bo’lsa 1 bayt joyga, aks holda uzunligiga qarab 2, 3 yoki 4 bayt xotiraga yoziladi. Bundan tashqari, UTF-8 jadvalidagi dastlabki 256 ta belgi ASCII bilan aynan mos keladi. Demak, ko’proq ASCII jadvalida mavjud belgilar ishlatilgan matnni kodlashda UTF-8 xotira bo’yicha katta ustunlikka ega bo’ladi, chunki bu belgilar 1 bayt joy egallaydi xolos (UTF-32 4 baytni band qilardi).

Savol tug’ilishi mumkin, biz o’zgaruvchan belgilarni har xil uzunlikda yozib ketaversak, bitta belgi qayerda boshlanib, qayerda tugaganini bilmasak, keyin ularni qanday o’qiymiz? Belgi necha bayt xotiraga yozilganini bildirish uchun UTF-8 da quyidagicha shablon ko'rinishida yoziladi:

| Bayt | Ko’rinishi                          | Maksimal uzunligi |
| ---- | ----------------------------------- | ----------------- |
| 1    | 0XXXXXXX                            | 7                 |
| 2    | 110XXXXX 10XXXXXX                   | 11                |
| 3    | 1110XXXX 10XXXXXX 10XXXXXX          | 16                |
| 4    | 11110XXX 10XXXXXX 10XXXXXX 10XXXXXX | 21                |

Masalan, 1101 soni 00001101 kabi, 11110011 soni esa 11000011 10110011 kabi yoziladi. Hozirda juda ko’p hollarda belgilarni kodlash uchun UTF-8 ishlatiladi.

---------------------------------------------------------------------------------------------------------------------------------------------------

Endi esa dasturda turlicha kodlash turlarini ishlatishga yordam beruvchi Encoding sinfi haqida gaplashamiz. Bu sinf `System.Text` nomlar makoniga tegishli abstrakt sinf bo’lib, `IClonable` interfeysidan meros olgan.

### Sinfning xususiyatlari (properties)

**Encoding.ASCII** – kodlash turi sifatida ASCII ni o’rnatish uchun ishlatiladi.

**Encoding.UTF32** – kodlash turi sifatida UTF32 tizimini o’rnatish uchun ishlatiladi.

**Encoding.Unicode** – kodlash turi sifatida UTF16 ni o’rnatish uchun foydalanamiz.

**Encoding.UTF8** – kodlash turi sifatida UTF8 ni o’rnatadi.

**Encoding.UTF7** – kodlash turi sifatida UTF7 ni o’rnatadi. (UTF7 UTF8ning kichraytirilgan versiyasi bo’lib, xavfsizlik bilan bog’liq muammolar sabab bu kodlash turidan foydalanish tavsiya etilmaydi)

Keling, turli kodlash turlarida π harfini Consolega chiqarib ko’ramiz:

```csharp
using System;
using System.Text;
class p
{
    public static void Main()
    {
        Console.OutputEncoding = Encoding.UTF8;
        Console.WriteLine("\u03c0");

        Console.OutputEncoding = Encoding.Unicode;
        Console.WriteLine("\u03c0");

        Console.OutputEncoding = Encoding.ASCII;
        Console.WriteLine("\u03c0");
        Console.ReadKey();
    }
}
```

Natija:

```
π
π
?
```

3-qatorda ? belgisi chiqarilganining sababi π belgisi **ASCII** jadvalida yo’q, **UTF** da esa bor.

Yuqorida ko’rilgan xususiyatlarni fayllarga yozish va o’qishda kodlash turini belgilash uchun ham ishlatish mumkin.

### Sinfning metodlari

**GetBytes()** – belgilar to’plamining har bir belgiga mos kodlarini byte tipidagi massivga joylab qaytaradi.

```csharp
using System;
using System.Text;
namespace ConsoleApp3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string s = "abcd";
            Encoding encoding = Encoding.UTF8;
            byte[] a = encoding.GetBytes(s);
            foreach (var item in a)
            {
                Console.WriteLine(item);
            }
            
        }
    }
}
```

Natija:

```
97
98
99
100
```

Yuqoridagi kodda UTF8 o’rniga boshqa kodlash turlari – ASCII, UTF32, Unicode ni yozib dasturni ishlatib ko’ring, bu kodlash turlarining farqini yanada yaxshiroq tushunasiz.

**Convert()** – bir kodlash turidan boshqa kodlash turiga o’girish uchun ishlatiladi. O'girish uchun belgilar to'plamining baytlarini byte tipidagi massivga joylab berish kerak:

```csharp
using System;
using System.Text;

namespace ConsoleApp3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string s = "abcd";
            Encoding encoding = Encoding.UTF8;
            byte[] a = encoding.GetBytes(s);
            byte[] b = Encoding.Convert(Encoding.UTF8, Encoding.UTF32, a);
            foreach (var item in b)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

Natija:

```
97
0
0
0
98
0
0
0
99
0
0
0
100
0
0
0
```

**GetString()** – **GetBytes()** ga teskari ishni bajaradi. Ya’ni **GetBytes()** _string_dan _byte\[]_ ga o’girgan bo’lsa, **GetString()** o’ziga berilgan _byte_ tipidagi massivga ko’ra ko’rsatilgan kodlash turida satrni qaytaradi.

```csharp
using System;
using System.Text;
namespace ConsoleApp3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Encoding en = Encoding.ASCII;
            byte[] a = {100, 111, 116, 45, 110, 101, 116, 46, 117, 122 };
            string s = en.GetString(a);
            Console.WriteLine(s);
        }
    }
}
```

Natija:

```
dot-net.uz
```
