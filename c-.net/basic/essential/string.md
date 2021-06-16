---
description: Farrukh Kholmatov
---

# **String**

C# dasturlash tilida satr bilan ishlash uchun **String** ishlatiladi. **String** o’zgaruvchisi ikkita tirnoq (" ") bilan o’ralgan belgilar to’plamini o’z ichiga oladi

```csharp

	string myText = “Hello”;

```

**string** kalit so’zi **String** uchun taxallus hisoblanadi, ya’niki **string**  &&  **String** so’zlari o’zaro tengdir va qaysi ko’rinishdan foydalanish esa dasturchining xohishiga bog’liq.

C# dasturlash tilida satr bilan ishlash metodlari **String** sinfida joylashgan va bu sinf satrlarni xavfsiz yaratish, boshqarish va taqqoslash uchun ko'plab usullarni taqdim etadi. 

Misol uchun: Satr uzunligini olish
```csharp
int value = myText.Length;
//output: value = 5;
```

## String sinfining metodlari:

**CompareTo** – berilgan satrni boshqa bir satr bilan solishtiradi va bizga **bool**  ya’ni **True/False**  qiymatda javob qaytaradi

```csharp
string str1 = “Hello”;
string str2 = “World”;
bool IsSame = str1.CompareTo(str2) == 0;
//output: IsSame = False
```

**ToLower** – berilgan satrni kichik harflarga o’zgartiradi

```csharp
string str1 = “HELLO WORLD”;
string str2 = str1.ToLower();
 //output: str2 = “hello world”
```

**ToUpper** – berilgan satrni katta harflarga o’zgartiradi

```csharp
string str1 = “hello world”;
string str2 = str1.ToUpper();
 //output: str2 = “HELLO WORLD”
```

**Split** – berilgan satrdagi so’zlarni ustun shaklida ajratadi va to’plam qaytaradi


```csharp
string str = “Hello! how are you?”;
string[] myString = str.Split();
//output: 
myString[0] = “Hello!”
myString[1] = “how”
myString[2] = “are”
myString[3] = “you?”
```
{% hint style="info" %}
**NOTE!**  *Split kalit so’zi ishlashi uchun matnda “probel”(“ “) bo’lishi kerak*
{% endhint %}

**StartsWith** – berilgan satrni boshidan boshlab ko’rsatilgan satr bilan tekshiradi

```csharp
string str1 = “Hello World”;
string str2 = “He”;
bool result = str1.StartsWith(str2);
//output: result = True
```

**Contains** – berilgan satr tarkibida ko’rsatilgan satr bor yoki yo’qligini tekshiradi

```csharp
string str1 = “Hello World”;
string str2 = “bye”;
bool result = str1.Contains(str2);
//output: result = False
```

**IndexOf** – berilgan satr tarkibida kor’rsatilgan satrni indeksini topib beradi

```csharp
string str1 = “Hello World”;
string str2 = “lo”;
int result = str1.IndexOf(str2);
//output: result = 3
```

**Substring** – berilgan satrning ko’rsatilgan diapazondagi qismini qaytaradi

```csharp
string str1 = “Hello World”;
string str2 = str1.Substring(1, 4);
//output: str2 = “ello”
```

**IsNullOrEmpty** – berilgan satrni bo’sh yoki null ekanligini tekshiradi

```csharp
string name = “”;
bool IsEmpty = String.IsNullOrEmpty(name);
//output: True 
```

**Concat** – berilgan ikki satrnni birlashtiruvchi funksiya

```csharp
string FirstName = “Farrukh”;
string LastName = “Kholmatov”;
string name = string.Concat(Firstname, Lastname);
//output: Farrukh Kholmatov
```

**String.Format  &&  “$”** - satr va obyektlar ustida bir vaqtning o’zida ishlash imkonini beradi

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
C# dasturlash tilida “+” (qo’shish) operatori orqali ham qo’shish ham birlashtirish mumkin.

{% hint style="info" %}
Esda tuting! *Sonlar qo’shiladi, satrlar birlashadi*
{% endhint %}

```csharp
int num1 = 5;
int num2 = 12;
int result = num1 + num2;
//output: result = 17

string str1 = “6”;
string str2 = “9”;
string result = str1 + str2;
//output: result = 69

```
