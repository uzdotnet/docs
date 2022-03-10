---
description: Niyozbek Mirzayev
---

# StringBuilder

C# dastrlash tilida Stringga o'xshash StringBuilder tipi mavjud. Ular bir-biriga yaqin, lekin ma'lum farqlar ularni ajratib turadi.

Keling, StringBuilder qanday yaratilishi haqida bilib olaylik. Avallo, **System.Text** kutubxonasini chaqirishimiz lozim, shundan so'ng quyidagicha kod yoradamida StringBuilder e'lon qilinadi:

```csharp
StringBuilder strB = new StringBuilder(); 
```

Endi esa asosiy qism, ya'ni String va StringBuilderning farqini ko'rib chiqamiz:

**String bu immutable tip hissoblandi, ya'ni uni xotirada e'lon qilganimizdan so'ng uni o'zgartira olmaymiz, StringBuilder esa mutable tip hisoblandi, ya'ni u xotirada o'z ko'rinishni va o'lchamini o'zgartira oladi. Shu sababdan, StringBulider Stringdan tezroqdir.**

Misol uchun, Quyidagi kodda _str_ o'zgaruvchisi 1000 martta xotiradan o'chirib tashlanadi va har safar _Salom_ so'zi qo'shilib qaytadan yaratiladi.

```csharp
string str = "Salom";  
for (int i = 0; i < 1000; i++)  
{  
     str += "Salom ";  
}
```

Keling end shu misolni StringBuilder orqali ko'raylik:

```csharp
    
StringBuilder strB = new StringBuilder(); 
for (int i = 0; i < 1000; i++)  
{  
     strB.Append("Salom ");  
}
```

str o'zgaruvchisida farqli ravishda strB o'zgaruvchisi xotirada 1000 marta o'chirilib tashlanmaydi, buning o'rniga _strB_ o'zgaruvchising o'ziga 1000 martta _Salom_ so'zi qo'shilib yoziladi.

Yuqorida ko'rganingizdek StringBuilderning ham String kabi o'z methodlari mavjut va quyida ulardan bir nechtasiga misolar keltirilgan:

* **Append** - StringBuilderning oxiridan String qo'shish uchun ishlatiladi.

```csharp
StringBuilder strB = new StringBuilder("Hello World!!");	
string str = " Yes ";
		
strB.Append(str); 
Console.WriteLine(strB); //output:   Hello World!! Yes 

```

* **AppendLine** - **Append** funksiyasi kabi ishlaydi, lekin har bir **String**ni yangi qatordan qo'shadi:

```csharp
StringBuilder strB = new StringBuilder("Hello World!!");		
string str = " Yes ";
		
strB.AppendLine(str);
//output: Hello World!!
//				Yes
```

* **Remove** -satrning ma'lum indexdan boshqa bir indexgacha bo'lgan qismini o'chiradi:

```csharp
StringBuilder strB = new StringBuilder("Hello World!!");
strB.Remove(0, 11);

Console.WriteLine(strB); 
//output: !!
```

* **Replace** - satrning ma'lum bir qismini boshqa bir satr bilan almashtiradi.

```csharp
StringBuilder strB = new StringBuilder("Hello World!!");
strB.Replace("World", "C#");

Console.WriteLine(strB); 
//output: Hello C#!!
```

* **Clear -** StringBuilder ichidagi barcha ma'lumotlarni o'chirish uchun ishlatiladi:

```csharp
StringBuilder strB = new StringBuilder("Hello World!!");
Console.WriteLine(strB); //output: Hello World!!
strB.Clear();
Console.WriteLine(strB);  //ikkinchi qatorda hech nima chiqmaydi sababi malumotlar o'chirilgan					
```

* **Insert -** Ma'lum bir berilgan indexdan boshlab String qo'shadi:

```csharp
StringBuilder sb = new StringBuilder("Hello World!");
sb.Insert(5," C#"); 

Console.WriteLine(sb);  //output: Hello C# World!
```
