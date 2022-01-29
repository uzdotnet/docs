---
description: Farrukh Kholmatov
---

# String

## **String**

C\# dasturlash tilida satr bilan ishlash uchun **String** ishlatiladi. **String** o’zgaruvchisi ikkita tirnoq \(" "\) bilan o’ralgan belgilar to’plamini o’z ichiga oladi.

```csharp
    string myText = "Hello";
```

**string** kalit so’zi **String** uchun taxallus hisoblanadi, ya’niki **string** && **String** so’zlari o’zaro tengdir va qaysi ko’rinishdan foydalanish esa dasturchining xohishiga bog’liq. **string** tipidagi o'zgaruvchi eng ko'pi bilan 2 Gb ma'lumotni, yoki **1073741791 ta** belgini saqlashi mumkin.

C\# dasturlash tilida satr bilan ishlash metodlari **String** sinfida joylashgan va bu sinf satrlarni xavfsiz yaratish, boshqarish va taqqoslash uchun ko'plab metodlarni taqdim etadi. 

Misol uchun: Satr uzunligini olish:

```csharp
int value = myText.Length;
//output: value = 5;
```

## String sinfining metodlari:

**CompareTo()** – berilgan satrni boshqa bir satr bilan solishtiradi va bizga **bool** ya’ni **True/False** qiymatda javob qaytaradi

```csharp
string str1 = "Hello";
string str2 = "World";
bool IsSame = str1.CompareTo(str2) == 0;
//output: IsSame = False
```

**ToLower()** – berilgan satrdagi barcha harflarni kichik harflarga o’zgartiradi

```csharp
string str1 = "Hello, WORLD !";
string str2 = str1.ToLower();
Console.Write(str2);
 //output: hello, world !
```

**ToUpper()** – berilgan satrdagi barcha harflarni katta harflarga o’zgartiradi

```csharp
string str1 = "Hello, World !";
string str2 = str1.ToUpper();
Console.Write(str2);
 //output: HELLO, WORLD !
```

**Split()** – berilgan satrni biz kiritgan belgi ajratib turgan qismlarga bo'ladi va yangi massivga yuklaydi:
```csharp
string satr="satr,ustun,katakcha";
string [] massiv=satr.Split(',');
foreach (string a in massiv)
    Console.WriteLine(a);

/* output: 
satr
ustun
katakcha
*/
```
Yuqoridagi misolda vergul satr qismlarini ajratuvchi belgi bo'lib xizmat qildi. Gapda so'zlar ko'pincha probel bilan ajratilgani uchun, vergul o'rniga probel ham yozishimiz mumkin. Yoki qavs ichiga hech narsa yozilmasa, Split() metodi bu belgini probel deb tushunadi:
```csharp
string str = "Hello! How are you?";
string[] myString = str.Split();
//output: 
myString[0] = "Hello!"
myString[1] = "How"
myString[2] = "are"
myString[3] = "you?"
```

**StartsWith()** – berilgan satr biz kiritgan satr bilan boshlanganmi yoki yo'qligini tekshiradi. bool tipida qiymat qaytaradi.

```csharp
string str1 = "Hello World";
string str2 = "He";
bool result = str1.StartsWith(str2);
//output: result = True
```

**Contains()** – berilgan satr tarkibida ko’rsatilgan satr yoki belgi bor yoki yo’qligini tekshiradi. Agar bor bo'lsa *true*, aks holda *false* qiymat qaytaradi.

```csharp
string str1 = "Hello World";
string str2 = "bye";
bool result = str1.Contains(str2);
Console.Write(result);   //output: False

Console.Write(str1.Contains("rld"));  // output: True

Console.Write(str1.Contains('a')); // output: False
```

**IndexOf()** – berilgan satr tarkibida kor’rsatilgan satrni indeksini topib, bizga int tipida qaytarib beradi. Agar berilgan satr tarkibida biz ko'rsatgan satr mavjud bo'lmasa, -1 ni qaytaradi.

```csharp
string str1 = "Hello World";
string str2 = "lo";
int result = str1.IndexOf(str2);
//output: result = 3
```

**Substring()** – berilgan satrning ko’rsatilgan diapazondagi qismini qirqib olib, bizga qaytaradi

```csharp
string str1 = "Hello World";
string str2 = str1.Substring(1, 4);
//output: str2 = "ello"
```

**IsNullOrEmpty()** – berilgan satrni bo’sh yoki null ekanligini tekshiradi. Agar satr bo'sh bo'lsa yoki qiymati null ga teng bo'lsa true, aks holda false qiymat qaytaradi.

```csharp
string name = "";
bool IsEmpty = String.IsNullOrEmpty(name);
//output: True
```

**Concat()** – berilgan ikki satrnni birlashtiruvchi funksiya

```csharp
string FirstName = "Farrukh";
string LastName = "Kholmatov";
string name = string.Concat(Firstname, Lastname);
//output: Farrukh Kholmatov
```

**String.Format && "$"** - satr va obyektlar ustida bir vaqtning o’zida ishlash imkonini beradi

```csharp
string name = "Petr";
int year = 45;
string str = String.Format("Hello {0}, {1}", name, year);
// str = "Hello Petr, 45"
int a = 5;
int b = 7;
string result = $"{a} + {b} = {a + b}";
// str = "5 + 7 = 12"
```

## WARNING!

C\# dasturlash tilida "+" \(qo’shish\) operatori orqali ham qo’shish ham birlashtirish mumkin.

{% hint style="info" %}
**Esda tuting!** _Sonlar qo’shiladi, satrlar birlashadi_
{% endhint %}

```csharp
int num1 = 5;
int num2 = 12;
int result = num1 + num2;
//output: result = 17

string str1 = "6";
string str2 = "9";
string result = str1 + str2;
//output: result = 69
```

