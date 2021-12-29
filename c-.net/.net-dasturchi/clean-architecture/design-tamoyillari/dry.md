---
description: Ravshan Sodiqov
---
# DRY

Shu paytga qadar siz kichik loyihalarni balki jamoa bo’lib, balki yolg’iz holda ishlagan bo’lishingiz mumkin va qachondir kun kelib  yirik jamoa bilan yirik loyiha ustida ishlash to’g’risida o’ylab ko’rganingiz aniq. Yirik loyihalar xuddi, noldan qurilayotgan binoga o’xshaydi. Binoning konstruktsiyasini  mukammal ishlab chiqish o’ta muhim ahamiyatga ega. Biz quradigan yirik dasturlar ham xuddi binoga o’xshaydi. Shuni unutmaslik kerak-ki, _“Yirik loyiha bu shunchaki minglab qator kod degani emas ! ”_. Dastur qanchalik katta yoki kichik bo’lmasin uni loyihalash muhim ahamiyatga ega. 

## Dasturiy ta’minotni qanday loyihalashtirish mumkin ?
Dasturiy ta’minotni loyihalashtirish bir necha tamoyillarga asoslanadi:
1.	**DRY** – **D**on’t **R**epeat **Y**ourself
2.	**KISS** – **K**eep **i**t **S**imple **S**tupid
3.	**YAGNI** – **Y**ou **a**ren’t **g**onna **n**eed  **i**t  
 ![](https://user-images.githubusercontent.com/91861166/147697616-07948c51-87d2-4af7-82da-b875bce07708.png)

**DRY** – ushbu tamoyilga amal qilishni o’zlari uchun muhim qoidaga aylantiradigan dasturchilar vaqt va sifatdan yuqori samaradorlikka erishishlari aniq. Bu qoida sizga kodingizda bir xil vazifani bajaruvchi dastur tanalarini yagona dastur tanasiga birlashtirishni anglatadi.  Bir so’z bilan aytganda bir xillliklardan xalos bo’lish demakdir. DRY so’zi bir o’qishda qaysidir dasturlash tilidagi biror kalit so’z bo’lsa kerak, degan fikr uyg’otishi mumkin, yo’q aksincha, bu so’z siz kod yozayotganingizda unutmaslik kerak bo’lgan qoidaning qisqartma shakli xolos. Endi ushbu qoidaga amal qilmay yozilgan dasturni ko’rib chiqamiz:  
```csharp
class Program
    {
        static void SwapForString(string var1, string var2)
        {
            string temp = var1;
            var1 = var2;
            var2 = temp;
            Console.WriteLine("{0} {1}", var1, var2);
        }

        static void SwapForInt(int var1, int var2)
        {
            int temp = var1;
            var1 = var2;
            var2 = temp;
            Console.WriteLine("{0} {1}", var1, var2);
        }

        static void SwapForChar(char var1, char var2)
        {
            char temp = var1;
            var1 = var2;
            var2 = temp;
            Console.WriteLine("{0} {1}", var1, var2);
        }
```
Yuqoridagi holatda ikkita string, ikkita int yoki ikkita char tipidagi o’zgaruvchilar uchun **Swap()** metodi yozilgan. Bu funksiya argumentlarning turiga qaramasdan bir xil vazifa bajarmoqda. 
```csharp
static void Main(string[] args)
{
      SwapForChar('x', 'y');             //output: y x
      SwapForInt(3, 6);                  //output: 6 3
      SwapForString("csharp", "python"); //output: python csharp
      Console.ReadKey();
}    
```
Ushbu holat **DRY** prinsipiga mutlaqo teskari bo’lgan jarayon, ya’ni,  **WAT** (Write Everything Twice) ga yaqqol misol bo’ladi.  Biz bu uchta metodni ham satr, ham butun va shu bilan birgalikda boshqa tipdagi o’zgaruvchilar uchun aniqlangan yagona **Swap()** ga almashtiramiz va dasturimiz quyidagicha ko’rinish kasb etadi:
```csharp
class Program
    {
        static void Swap<T>(T var1, T var2)
        {
            T temp = var1;
            var1 = var2;
            var2 = temp;
            Console.WriteLine("{0} {1}", var1, var2);
        }
        static void Main(string[] args)
        {
            Swap<char>('x', 'y');              //output: y x
            Swap<int>(3, 6);                   //output: 6 3
            Swap<string>("csharp", "python");  //output: python csharp
            Console.ReadKey();
        }     
    }
```
Ushbu  DRY tamoyili “_Biz takror kod yozishni yoqtiramiz_”, “_Barcha narsa egizagi bilan birga bo’lgani yaxshi_” yoxud “_Menga faqat ishlasa bo’ldi_” shiori ostida ish ko’ruvchi do’stlarimiz uchun ancha noqulay bo’lishi mumkin, ammo siz  bunday dasturchilar safiga kirmaysiz va dasturlar uchun dasturiy ta’minotni loyihalashtirish muhim ekanligini anglab yetdingiz degan umiddamiz !
