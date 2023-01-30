---
description: (AIJavhar) Javohirbek Boyaliyev
---
# LinkedList

LinkedList – ikki tomonlama bog'langan, ulangan to'plam. Ya'ni to'plamning har bir elementi o'zidan bitta oldingi va bitta keying elementning LINK ini saqlaydi. 
                                                   Huddi bular kabi:
                                                               ⬇️
                                                               
![](https://user-images.githubusercontent.com/91861166/215412659-31828165-e633-496d-969d-3b02c075ff8a.png)

Ushbu ko'rinishdagi (o'zaro bog'langan) to'plamlarni yaratish uchun: 
```csharp
LinkedList<string> people = new LinkedList<string>();
```
kabi code yoziladi. Bu yerda string tipiga mansub people (ODAM) deb nomlangan bo'sh to'plam yaratilish jarayoni. 

### LinkedList XUSUSIYATLARI:
LinkedList klassning quyidagi xususiyatlari mavjud:
•	Count: To'plamda mavjud elementlar miqdori
•	First:   Top'lamdagi birinchi bog'lam
•	Last:    To'plamdagi yakuniy (oxirgi, so'ngi, tugallovchi va shu kabi boshqa so'zlar) bog'lam

![](https://user-images.githubusercontent.com/91861166/215413018-902dee2e-ab15-48b2-a511-486dd630cd12.png)

Bu xususiyatlarni ko'rib chiqamiz:

```csharp
var Ustozlarim = new List<string> { "MuhammadKarim aka", "Temur aka", "Jamshid aka" };

LinkedList<string> Ustoz = new LinkedList<string>(Ustozlarim);
Console.WriteLine(Ustoz.Count);            // 3 
Console.WriteLine(Ustoz.First.Value);    // MuhammadKarim aka
Console.WriteLine(Ustoz.Last.Value);    // Jamshid aka 
```

LinkedList ning ba'zi method lari
•	AddFirst(T value): to'plamning boshida value qiymatiga ega yangi bog'lam(element)ni kiritadi
•	AddLast(T value): to'plam oxirida value qiymatiga ega bo'lgan yangi tugunni kiritadi
•	AddAfter( LinkedList<T> node, T value): node bog'lamidan keyin value qiymatli element qo'shadi
•	AddBefor( LinkedList<T> node, T value): node bog'lamidan oldin value qiymatli element qo'shadi
•	RemoveFirst(): to'plamdan birinchi bog'lamni o'chirib tashlaydi. Shundan so'ng, o'chirilgan tugundan keying tugun birinchilikka o'tadi.
•	RemoveLast(): to'plamdagi oxirgi bog'lam(element)ni o'chiradi.

Nazariy bildik, endi ba'zi methodlarni amalda qo'llab ko'ramiz:
```csharp
var people = new LinkedList<string>();
people.AddLast("Abror"); //To'plamning eng oxiriga “Abror” elementini qo'shadi. 
//Bizning vaziyatda to'plamimiz bo'sh shu sababdan bu to'plamning birinchi elementi bo'ladi.

people.AddFirst("MuhammadAmin "); // “MuhammadAmin” qiymatli elementni to'plamning boshiga joylashtiradi.

//Endi esa 1-bog'lam(element)dan keyin element qo'shishni ko'ramiz:
if (people.First != null) people.AddAfter(people.First, "Asadulloh");
 
// Bizning to'plam quyidagi ko'rinishga keladi: 
// Abror MuhammadAmin Asadulloh
foreach (var person in people) Console.WriteLine(person);
```

LinkedList haqida yana qisqacha: 

![](https://user-images.githubusercontent.com/91861166/215413108-71f53bd9-966c-427e-a715-d01bb4034921.png)
