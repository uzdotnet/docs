---
description: Jamshid Sodiqov
---

# Average

Average metodi to’plamdagi int tipidagi elementlarning o’rtacha qiymatini qaytaradi. Average metodi null, decimal, double yoki float qiymatini qaytaradi. Quyidagi misolda to'plamdagi barcha butun sonlarning o'rtacha qiymatini qaytaradigan Agerage metodini ishlashi ko'rsatilgan:

```
IList intList = new List>() { 10, 20, 30 };
var avg = intList.Average();
Console.WriteLine("Average: {0}", avg);
```

Siz o'rtacha qiymatni olmoqchi bo'lgan lambda ifodasi sifatida sinfning int, decimal, double yoki float propertylarini belgilashingiz mumkin. Quyidagi misolda murakkab turdagi Average metodinini ko'rsatadi:

```
IList studentList = new List>()
{ 
    new Student() { StudentID = 1, StudentName = "John", Age = 13} ,
    new Student() { StudentID = 2, StudentName = "Moin", Age = 21 } , 
    new Student() { StudentID = 3, StudentName = "Bill", Age = 18 } , 
    new Student() { StudentID = 4, StudentName = "Ram" , Age = 20} ,
    new Student() { StudentID = 5, StudentName = "Ron" , Age = 15 } 
};
var avgAge = studentList.Average(s => s.Age);
Console.WriteLine("Average Age of Student: {0}", avgAge);
```

**Output:**

**Average Of Student: 17.4**

{% hint style="info" %}
C# dasturlash tilida Average operatori query sintaksisida qo’llab quvvatlanmaydi!
{% endhint %}
