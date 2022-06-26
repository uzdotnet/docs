---
description: Zohidbek Mengliboyev
---

# Obyektni ishga tushiruvchilar

Obyektni ishga tushiruvchilar(Object Initializers)
Yaxshi! Bundan avvalgi mavzuda biz konstruktorlar haqida bilib oldik. Bilasizki, biz obyektni ishga tushirish va uni C# da dastlabki holatga keltirish uchun konstruktordan foydalanamiz. Obyektni initsializatsiya qilishning yana bir yo'li mavjud va u obyektni ishga tushiruvchilar(object initializers) vositasidan foydalanadi. Bu ficha C# 3.0 yoki undan yuqori versiyalarida kiritilgan. Obyektni ishga tushiruvchi(object initializer) - bu oddiy sintaksis yoki obyektni uning konstruktorlaridan birini chaqirmasdan tezda ishga tushirish. Xo’sh, bu bizga bir nechta yoki undan ko’p konstruktorlarni tuzishdan qochish uchun kerak. Keling, bir misol keltiraman. Tasavvur qiling-a, bizda bu inson sinfi ko'p maydonlarga ega. Endi bu juda oddiy misol. Bu yerda faqat to‘rtta maydonimiz bor. Haqiqiy yirik loyihalarda sizda yana bir nechta maydonlar bo'lishi mumkin:

```csharp
public class Inson
{
    public int Id;

    public string Ismi;

    public string Familiyasi;

    public DateTime Tavalludkuni;
}
```

Endi ushbu sinf bilan, agar siz turli maydonlarni initsializatsilash uchun konstruktorlar tuzmoqchi bo'lsangiz, siz shunday sinfga ega bo'lishingiz mumkin:
```csharp   
public class Inson
{
    public Inson(int id) { } // 1-kontruktor

    public Inson(int id, string ismi) { } // 2-konstruktor

    public Inson(int id, string ismi, string familiyasi) { } // 3-konstruktor

    public Inson(int id, DateTime tavalludkuni) { } // 4-konstruktor
	  
	  ........
}
```

Ko'rib turganingizdek, menda 4 ta konstruktor bor. Birinchisi faqat ID olad. Ikkinchisi ID va ism oladi. Uchinchisi id, ism, famiyani oladi va hokazo. Shunday qilib, siz juda ko'p turli xil kombinatsiyalarni ko'rasiz. Aynan shuni biz obyektni ishga tushiruvchilarni tanishtirmasimizdan oldin C# da shunday qilar edik. Ko'rib turganingizdek, bunday kod yozish tartibsiz va osongina nazoratdan chiqib ketadi. Shunday qilib, obyektni initsializatsilash muammosini hal etish uchun obyektni ishga tushiruvchilar maydonga keladi. Bunda bu konstruktorlarning hech biri kerak bo’lmaydi. Masalan, bunday:
```csharp
var inson = new Inson
{
    Ismi = "Zohidbek",
    Familiyasi = "Mengliboyev"
};
```

Men Inson sinfining konstruktorlaridan birini chaqirmayapman. Bu yerda ko'rib turgan sintaksis biz obyektni ishga tushiruvchi sintaksisi deb ataladigan narsadir. Shunday qilib, siz asosan xususiyatlar nomini belgilaysiz va ularga boshlang'ich qiymatni tayinlaysiz. Shuni esda tutingki, bunday obyektni qachon ishga tushirish kerak degan so'zlar orqasida standart yoki parametrsiz konstruktor chaqiriladi. Va keyin siz bu yerda o'rnatgan barcha xususiyatlar ishga tushiriladi. Shunday qilib, biz konstruktorlarni zarur hollarda kerak bo'lgan ssenariylar uchun ularni zaxiraga olib qo'yishimiz mumkin.
