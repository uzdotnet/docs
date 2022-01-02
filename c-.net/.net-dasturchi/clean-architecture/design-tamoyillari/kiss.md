---
description: Ravshan Sodiqov
---
# KISS

Navbatdagi mavzuyimiz dizayn tamoyillarining yana biri - **K.I.S.S** ga bagʻishlanadi. Unutmang, agar bu soʻzni IT sohasidagi biror maqolada uchratsangiz hech qachon toʻgʻridan – toʻgʻri tarjima qilmang :)) 
     
### Xoʻsh unda K.I.S.S o’zi nima ? 

![](https://user-images.githubusercontent.com/91861166/147854200-cda4c799-31f0-4adb-a0d2-b8e63afe68e2.png)

Ushbu atama foydalanuvchi interfeysini ishlab chiquvchi dizaynerlar, mahsulot dizaynini ishlab chiquvchilar va dasturiy taʻminotni loyihalashtiruvchilar tomonidan keng foydalaniladi. Sababi bu atama ishlayotgan sohangizda murakkab usullardan qochib, mumkin qadar soddalikdan foydalanish kerak ekanligini anglatadi. **K.I.S.S** – siz ishlayotgan sohada (qanday soha boʻlishidan qat’iy nazar) barcha muammolarni eng sodda va barchaga tushunarli yoʻl bilan hal qilish kerakligini anglatuvchi qoidadir. Keling atama haqida yaxshiroq tushunchaga ega boʻlish uchun kichik bir holatni tasavvur qilib koʻramiz.  Faraz qiling, sizda ikki yoʻl mavjud: birinchi yoʻl  sizni manzilingizga yetguningizga qadar qorongʻu va qoʻrqinchli oʻrmonda yashaydigan “bug” deb ataladigan qonxoʻr maxluqlar makonidan, yalmogʻiz kampirning uyi va uch boshli ajdar yashaydigan gʻorning oldidan oʻtishni taqozo qiladi. Ikkinchi yoʻldan esa tep – tekis, yangi asfalt qilingan yoʻldan yurib manzilga yetasiz. Xoʻsh qaysi yoʻlni tanlardingiz ?! Albatta tep – tekis yoʻldan yurish har doim yoqimliroq, shunday emasmi ?!   

![**K.I.S.S** ni bilmaydigan Anvar:](https://user-images.githubusercontent.com/91861166/147854235-4a306fc8-3baa-40e8-95d7-5c3403afc047.png)
 
Anvar  sinfda eng a’lochi  va barcha mavzuni eng yaxshi o’zlashtirgan oʻquvchi. Anvar oʻz sohasidagi muammolarni hal qila oladi, lekin uning bir kamchiligi **K.I.S.S** haqida umuman xabari yoʻq. Agar u ushbu tamoyildan ustamonlik bilan foydalanishni oʻrgansa shubhasizki, eng yaxshilardan biriga aylanadi :)

(Axir juda oddiy hal qilish mumkinku !) 
     
### Dasturlashda qanday qoʻllaymiz ?
Anvar ba’zida dasturlashga ham qoʻl urib turadi. U kiritilgan sonning ishorasini aniqlash masalasini mana bunday hal qiladi:
```csharp
int n = int.Parse(Console.ReadLine());
if (n > 0)
{
    Console.WriteLine("n musbat son");
}
else if (n == 0)
{
    Console.WriteLine("n = 0");
}
else
    Console.WriteLine("n manfiy son");

Console.ReadKey();
```

### Biz esa **K.I.S.S** qoidasiga rioya qilgan holda kodni mana bu koʻrinishga keltiramiz:
```csharp
int n = int.Parse(Console.ReadLine());
string text = n > 0 ? "musbat" : n < 0 ? "manfiy" : "nol";
Console.WriteLine(text);
Console.ReadKey();
```
Endi yaxshiroq shundaymi ?! Oʻtgan darsdagi loyihalash tamoyili **D.R.Y** va **K.I.S.S** haqida tushunchaga ega bo’lgach quyidagicha xulosa qilamiz: Demak, dasturlarimiz takrorlanmas va sodda koʻrinishdagi kodlardan iborat boʻlishi kerak ekan. 
