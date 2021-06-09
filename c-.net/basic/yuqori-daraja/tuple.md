---
description: Javohir Buzrukov
---

# Tuple

Keling bu mavzuni sodda qilib o'rganish uchun o'xshatish metodidan foydalanamiz :\) O'zimiz bilgan, tushungan massiv ga o'xshatib ko'ramiz shunda soddaroq bo'ladi. Qani ketdik.

Tuple classi ni massivga o'xshagan to'plam deb qarasak boladi. Undan farqi har-xil turdagi ma'lumotlarni saqlash mumkin. Keling uni sintaksisi bilan tanishamiz:

```csharp
Tuple<int, string, string> person = new Tuple <int, string, string>(1, "Steve", "Jobs");

//yoki 

var person = Tuple.Create(1, "Steve", "Jobs");
```

Tuple da ko'pi bilan 8 ta element saqlash mumkin. Agar undan ko'payib ketsa, kompilyator bizga xatolik beradi. Lekin bunda ham yechim bor har doimgidek ayyorlik ishlatamiz :\) Tuple ichida tuple yozamiz quyidagicha: 

```csharp
var numbers = Tuple.Create(1, 2, Tuple.Create(3, 4, 5, 6, 7,  8), 9, 10, 11, 12, 13 );
```

Tuplega murojat class maydonlariga murojaat qilishga o'xshab ketadi. 

{% hint style="success" %}
obyektNomi.Item1, obyektNomi.Item2 ... obyektNomi.Item8 
{% endhint %}

```csharp
var person = Tuple.Create(1, "Steve", "Jobs"); 

person.Item1; // returns 1 

person.Item2; // returns "Steve" 

person.Item3; // returns "Jobs"
```

8 - elementga **person.Rest** ko'rinishda murojat qilsa ham bo'ladi. **person.Item8** dan farqi Rest qiymatni qovus ga olib chiqaradi.

{% hint style="info" %}
 E'tibor bering faqat 8- elementga oxirgi elementga EMAS
{% endhint %}

```csharp
var numbers = Tuple.Create("One", 2, 3, "Four", 5, "Six", 7, 8);
Console.WriteLine(numbers.Item1); // print "One"
Console.WriteLine(numbers.Item2); // print 2
Console.WriteLine(numbers.Item3); // print 3
Console.WriteLine(numbers.Item4); // print "Four"
Console.WriteLine(numbers.Item5); // print 5
Console.WriteLine(numbers.Item6); // print "Six"
Console.WriteLine(numbers.Item7); // print 7
Console.WriteLine(numbers.Rest);  // print (8)
Console.WriteLine(numbers.Rest.Item1); // print 8

```

Tupledan, funksiyalarda argument sifatida foydalanish ham mumkin.

```csharp
static void Main(string[] args)
{
    var person = Tuple.Create(1, "Steve", "Jobs");
    DisplayTuple(person);
}

static void DisplayTuple(Tuple<int,string,string> person)
{
    Console.WriteLine($"Id = { person.Item1}");
    Console.WriteLine($"First Name = { person.Item2}");
    Console.WriteLine($"Last Name = { person.Item3}");
} 
```

Funksiylardan Tuple toifasiga mansub qiymatlarni ham qabul qilib olishimiz mumkin:

```csharp
static void Main(string[] args)
{
    var person = GetPerson();
}

static Tuple<int, string, string> GetPerson() 
{
    return Tuple.Create(1, "Bill", "Gates");
}
```

### Tupledan foydalanishning afzallik va kamchiliklari

Qulayliklari:

* Funksiyalardan bir necha qiymatlarnii qabul qilish / yuborish
* Key/Value ko'rinishida ishlash imkoniyati

Kamchiliklari:

* string toifasi kabi Tuple **immutable** tur hisoblanadi. Yaratilgandan keyin uning qiymatlariga o'zgartirish kiritib bo'lmaydi.
* Tuple qiymatli emas balki ma'lumotli \(reference\) toifa hisoblanadi. Buning hisobiga, u CPU ya'ni protsessorni zo'riqishga olib keladi.

