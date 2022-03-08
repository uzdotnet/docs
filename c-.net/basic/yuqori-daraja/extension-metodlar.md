---
description: Sarvarbek Mumtozbekov
---
# Extension metodlar

Extension metodlar oldindan aniqlangan  tiplarga yangi metodlarni qo’shish imkoniyatini beradi. Bunday metodlar juda foydali bo’ladi agar bizda klass kodlarini o’zgartirishga imkoniyatimiz bo’lmasa. Yoki bo’lmasa voris olish imkoniyatimiz bo’lmasa, misol uchun klass *sealed* modifikatori bilan aniqlangan bo’lsa.
Misol uchun biz string tipiga yangi metod qo’shmoqchimiz:
```csharp
int i = s.DigitsCount();
Console.WriteLine(i);

public static class StringExtension
{
    public static int DigitsCount(this string str)
    {
        int x = str. Count(c => Char.IsDigit(c));
        return x;
    }
}
```
Extension metod tuzish uchun oldin static klass yaratib olish kerak, aynan shu klassda extension metod yoziladi. Bizning misolda bu **StringExtension**. Bu klassga static metod yaratiladi. Bizning misolda bu **DigitsCount**. Bu metodning vazifasi satrdagi raqamlar sonini aniqlash.
Umuman olganda extension metod bu oddiy static metod, faqat u birinchi parametr sifatida quyidagi ko’rinishida parametr yoziladi: `this tip_nomi patametr_nomi`,  bizning holatda bu `this string str`. Bizning extension metodimiz string tipi uchun bo’lgani sababli biz string tipini ishlatamiz.

Endi bu metodni xohlagan satrimizga ishlatimiz mumkin:
```csharp
int i=”nimadir123”.DigitsCount();
```
Birinchi  parametrni berish ham shart emas, birinchi parametr sifatida satrni o’zini oladi. Agar qo’shimcha parametr qo’shish kerak bo’lsa ikinchi, uchinchi parametr sifatida ketma-ket qo’shib yozilaveradi:
```csharp
public static ExtMethod(this int i, int x, int y){ … };
int x  =1; x.ExtMethod(1,2);
```
