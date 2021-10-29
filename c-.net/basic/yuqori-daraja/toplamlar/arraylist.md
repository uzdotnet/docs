---
description: Hikmatullayev Saidrahmatulloh
---
# ArrayList

C# da ArrayList hajmi dinamik ravishda oshib boruvchi umumiy obyektlar to'plamidir.

Demak ArrayList ni  dinamik massiv yaratish uchun foydalaniladi, ya'ni massiv hajmi siznind dasturingiz talabiga ko'ra avtomatik kattalashadi yoki kichiklashadi.
**ArrayList**da faqat *Object* tipidagi elementlarni saqlash mumkin, demak, siz **ArrayList**dan sonlarni ham, satrlarni ham, obyektlarni ham saqlashda foydalanishingiz mumkin

1-qadam.
ArrayList dan foydalanish uchun  `System.Collections` nomlar fazosini qo'shish kerak.

2- qadam.
Endi ArrayList elon qilishni ko'rib chiqaylik: 

```csharp
ArrayList  list=new ArrayList();
```

ArrayList qulayliklari bilan tanishamiz:

  **Add()**      funksiyasi orqali ArrayListga element qo'shishimiz mumkin.
  
  **AddRange()**      orqali ArrayList ga to'plam ham qo'shish mumkin.
  
  **Count()**      ArrayList elementlari sonini aniqlab beradi.
  
  **Remove()**       ArrayList dan biror elementni o'chirish uchun ishlatiladi.
  
  **RemoveAt()**      ArrayListdan biror indexdagi elementni o'chirish uchun ishlatiladi.
  
  **RemveRange()**      ArrayListning ikkita indeksi orasidagi elementlarini o'chirishda foydalaniladi.
  
  **Clear()**      ArrayListning barcha elementlarini o'chirish uchin ishlatiladi.
  
  **Sort()**      ArrayList elementlarini o'sish  tartibida saralaydi.
  
Umuman olganda bu funksiyalar `System.Collections` dagi barcha to'plamlar uchun ishlaydi.

### **Add()** funksiyasini ishlatishni ko'rib chiqaylik.

Misol1:
```csharp
using System; 
using System.Collections;  
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            ArrayList dasturlash = new ArrayList();//dasturlash nomli Arraylist ochdik
            // element qo'shish
            dasturlash.Add("C#");
            dasturlash.Add("C++");
            dasturlash.Add("C");
            dasturlash.Add("Go");
            dasturlash.Add("Python");
            // foreach orqali listni chop etamiz
            foreach (var dastur in dasturlash)
            {
                Console.Write($"{dastur} ");
            }
        }
    }
}
```
Dastur natijasi:
```
C# C++ C Go Python 
```

Misol2:

Birinchi misolda biz bir turdagi elementlardan foydalandik. Umuman olganda ixtiyoriy turdagi elementlarni qo'shish mumkin.
Uni quydagi misolda ko'ramiz.

```csharp
using System; 
using System.Collections;  
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            ArrayList list=new ArrayList(); //list nomli ArrayList ochdik
            list.Add("dotnetuz");
            var list1 = new ArrayList()     //list1 nomli ArrayList
            {
                1.1,"Csharp",2021,true,null
            };
            int[] arr = { 7, 13, 45 };
            Queue queue1=new Queue();
            
            queue1.Enqueue("C++");
            list.AddRange(list1);   //listga list qo'shish
            list.AddRange(arr); //listga massiv qo'shish
            list.AddRange(queue1); //listga queue qo'shish
            for(int i=0;i<list.Count;i++)
                    Console.WriteLine(list[i]);
        }
    }
}
```
Dastur natijasi:
`
dotnetuz
1.1
Csharp
2021
True

7
13
45
C++
`

### Sort() funksiyasi ishlatilishi.

Keling tushunish oson bo'lishi uchun 1- misolda Sort() funksiyasini ko'ramiz.
```csharp
using System;
using System.Collections;
namespace dotnetuz
{
    class Program
    {
        static void Main(string[] args)
        {
            ArrayList dasturlash = new ArrayList();//dasturlash nomli Arraylist ochdik
            // element qo'shish
            dasturlash.Add("C#");
            dasturlash.Add("C++");
            dasturlash.Add("C");
            dasturlash.Add("Go");
            dasturlash.Add("Python");
            // foreach orqali listni chop etamiz
            foreach (var dastur in dasturlash)
            {
                Console.Write($"{dastur} ");
            }

            dasturlash.Sort();
            // for orqali chop etamiz

            System.Console.WriteLine();
            for (var i = 0; i < dasturlash.Count; i++)
            {
                Console.Write(dasturlash[i]+" ");
            }
        }
    }
}
```
Dastur natijasi:
```
C# C++ C Go Python 
C C# C++ Go Python
```

**ArayList**ning Sort() metodi *QuickSort* algoritmi bo'yicha saralaydi.
