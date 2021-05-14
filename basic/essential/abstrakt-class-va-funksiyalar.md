---
description: Xondamir Abduxoshimov
---

# Abstrakt class va funksiyalar

 OOP\(Object Oriented Programming\) asoslarini o'rganish davomida, e'tiborimizni qaratishimiz lozim bo'lgan bir tushuncha bor. U - _abstraktsiyadur\(abstraction\)_. Bugun shu haqida gaplashib o'tamiz.

#### Abstraktsiya o'zi nima? <a id="Abstraktsiya-o&apos;zi-nima?"></a>

Abstraktsiya obyektga yo'naltirilgan dasturlash \(OOP\) tillarining asosiy tushunchalaridan biridir. Uning asosiy maqsadi foydalanuvchidan keraksiz ma'lumotlarni yashirish orqali murakkablikni boshqarishdir. Bu foydalanuvchiga barcha yashirin murakkablikni tushunmasdan, undan foydalanishga imkon yaratadi.

Abstraktsiya faqatgina dasturlashga taaluqli bo'lgan tushuncha emas, uni real hayotimizda ham ko'p javhalarda kuzatishimiz mumkin. Keling bo'lmasa, abstraktsiya tushunchasini, kundalik hayotimizda uchrab turadigan bankomatlardan pul yechish mavzusiga bog'lab ko'ramiz.

#### Abstraktsiya va bankomatdan pul olish <a id="Abstraktsiya-va-bankomatdan-pul-olish"></a>

> Tasavvur qiling siz talabasiz va bugun sizning bank kartangizga stipendiya tushdi. O'zingizni - o'zingiz mehmon qilish maqsadida, kartadagi mablag'ni naqd ko'rinishga keltirish uchun bankomatga tashrif buyurdingiz. Bankomatdan o'zingizga kerakli bo'lgan summani belgilab, uni naqd ko'rinishida qabul qilib oldingiz.

Ushbu jarayonda siz bilishingiz kerak bo'lgan ish bu - bankomat aparatiga kartani solib, yechilgan pulni qabul qilish. Sizga bankomat aparati o'zi qanday ishlaydi va pulni naqdlash jarayoni qanday bo'ladi - bu ahamiyatsiz. Kimdir bundan xavotirlanib, bankomat aparatini yaratdi, endi u abstrakt vazifasini bajaradi va sizga taaluqli bo'lmagan tafsilotlarni yashiradi. Siz shunchaki ichki dastur haqida hech qanday bilim talab qilmaydigan oddiy interfeys bilan o'zaro aloqada bo'lasiz.

Dasturlashda ham shu kabi tushunchalar o'rinli. Endigi navbatda C\# dasturlash tilidan foydalanib mavzuni yanayam mustahkamlaymiz.

#### C\# dasturlash tilida abstraktsiya <a id="C#-dasturlash-tilida-abstraktsiya"></a>

Abstraktsiya tushunchasi asosan sinf va metodlar uchun foydalaniladi va **abstract** kalit so'zi yordamida quriladi.

**Abstrakt sinf**- bu sodda qilib aytganda cheklangan sinf. Ya'ni undan obyekt olish taqiqlangan. Unga kirish uchun, undan voris sinf olish lozim.

**Abstrakt metod** - bu tanasi mavjud bo'lmagan, hamda faqatgina abstrakt sinfda ishlovchi metod hisoblanadi. Uni tanasi esa, voris sinfda taqdim etiladi.

Endi misollar bilan tanishib chiqamiz.

 **Example 1**

```csharp
using System; 

// abstrakt class 'Hayvonlar' 
public abstract class Hayvolar 
{
    // abstrakt metod 'Ovoz()'
    public abstract void Ovoz();
}

// class 'Hayvolar' dan olingan  voris class 'Sigir'
public class Sigir : Hayvolar 
{
    // Qayta ishlangan 'Ovoz()' metodi
    public override void Ovoz() 
    { 
        Console.WriteLine("Moo");
    }
}

class Program
{
    static void Main(string[] args)
    {
         // Sigir obyektini yaratish
         Sigir sigir_obj = new Sigir();
         
         // abstrakt metodni chaqirish
         sigir_obj.Ovoz();
     }
 }
```

 **Natija:** Moo

Ota sinfda joylashgan abstrakt metoddan foydalanish avvalida **override** kalit so'zini yozib qo'yish talab etiladi.

Sinfni abstrakt ko'rinishga keltirish, uning ichida faqatgina abstrakt metodlari bo'lishi kerakligini anglatmaydi. Sinfda oddiy metodlardan ham foydalanish mumkin.

 **Example 2**

```csharp
using System; 

abstract class AbstractClass 
{
    // Abstrakt bo'lmagan metod
    public int AddTwoNumbers(int num1, int num2) 
    {
        return num1 + num2; 
    }
    
    public abstract int MultiplyTwoNumbers(int num1, int num2);
}

class VorisClass : AbstractClass 
{
    public override int MultiplyTwoNumbers(int num1, int num2) 
    {
        return num1 * num2;
    }
}

class Program
{
    static void Main(string[] args)
    {
        VorisClass d = new VorisClass();
        Console.WriteLine($"Yig'indi: {d.AddTwoNumbers(4, 6)}, Ko'paytma: {d.MultiplyTwoNumbers(6, 4)}");
    }
}
```

 **Natija:** Yig'indi: 10, Ko'paytma: 24

#### Xulosa <a id="Xulosa"></a>

Abstraktsiya - bu umumiy tushunchadir, uni real dunyoda ham, OOP ga asoslangan dasturlash tillarida ham topishingiz mumkin. Haqiqiy dunyodagi har qanday narsalar, masalan, aytib o'tilgan bankomat aparati yoki hozirgi dasturiy ta'minot loyihangizdagi sinflar va ichki qismni berkituvchi omillar abstraktsiyani ta'minlaydi.

Ushbu abstraktsiyalar, murakkablikni kichikroq qismlarga ajratish orqali ishni ancha osonlashtiradi. Eng asosiysi, siz ularni qanday qilib funksionallikni ta'minlayotganini tushunmasdan turib, foydalanishingiz mumkin bo'ladi.

Qisqacha tarzda tushuntirib bermoqchi bo'lgan narsalarim shular edi. Agarda sizlarda ham bizning jamoamizga qo'shilish istagi bo'lsa 👉[ushbu ](https://t.me/uz_dotnet)telegram guruhga tashrif buyuring.

