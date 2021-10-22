---
description: Mamataliyev Diyorbek
---

# Queue

Assalomu alaykum. Bugun ham to’plamlar bilan tanishishda davom etamiz. **Queue** to’plami haqida tasavvurga ega bo’lish uchun navbatga turgan odamlarni tasavvur qiling. Navbatga kim oldinroq qo’shilgan bo’lsa, o’sha oldinroq chiqib ketadi. Keyin kelganlar oldin chiqib ketolmaydi (agar shunday qilmoqchi bo’lsa janjal chiqishi hech gap emas). Dasturlashda ham shunday.

![Queue - Navbat](https://user-images.githubusercontent.com/91861166/138444755-78502d96-e872-4b56-99ad-9755dbec2532.jpg)


{% hint style="info" %}
**Queue** shunday to’plamki, unga elementni faqat oxiridan qo’shiladi, faqatgina boshidan chiqib keta oladi. **Queue**ga avvalroq qo’shilgan elementlar avvalroq tartib bilan chiqib ketadi. Shuning uchun **Queue** ni *FIFO* (*First In First Out Collection*) deb ham ataladi.
{% endhint %}

Biz **Queue** to’plami ustida quyidagi amallarni bajara olamiz:

**Enqueue()** – **Queue**ga yangi element qo’shadi (albatta oxiridan);

**Dequeue()** – **Queue**ning eng boshidagi element qiymatini qaytarib, bu elementni queuedan olib tashlaydi;

**Peek()** – **Queue**ning eng boshidagi element qiymatini qaytaradi, lekin Queue dan olib tashlamaydi;

**Count** – **Queue**dagi elementlar sonini (*int* tipida) qaytaradi;

**Contains()** – **Queue**da berilgan element mavjudligini tekshiradi. Bor bo’lsa true, aks holda false qiymat qaytaradi.

![QUEUE](https://user-images.githubusercontent.com/91861166/138444991-e2d615d0-a294-4393-b894-3ca24095bb97.png)


**Queue** dasturlashda aynan qaysi holatda ishlatiladi? Bir qurilmaga bir nechta qurilmadan bir vaqtda murojaat qilinadigan holatda, masalan bir nechta kompyuter bitta printerga lokal tarmoq orqali ulanganda yoki internet serverlarda navbatni ta’minlash muhim. Bu holatda **Queue**dan foydalanish mumkin. 

**Queue** haqida nazariy tushunchaga ega bo’lgan bo’lsangiz endi kodda ham ko’rsak. **Queue** to'plami `System.Collections.Generic` nomlar makonida joylashgan. Shuning uchun avval bu nomlar makonini chaqirib qo'yishimiz kerak bo'ladi: 
```csharp
using System;
using System.Collections;
using System.Collections.Generic;
public class program
{
  public static void Main()
  {
    //yangi Queue e'lon qilish
    var navbat=new Queue<int>();
        
    //Queue ga yangi element qo'shish
    navbat.Enqueue(2);
    navbat.Enqueue(5);
    navbat.Enqueue(8);
    navbat.Enqueue(13);
    navbat.Enqueue(21);
        
    //Queue ning eng boshidagi elementni aniqlash
    Console.WriteLine("Eng boshidagi element: "+navbat.Peek());
        
    //Queuedan elementlarni chiqarib tashlash
    Console.WriteLine(navbat.Dequeue()+" soni chiqarib yuborildi");
    Console.WriteLine(navbat.Dequeue()+" soni chiqarib yuborildi");
        
    //Queueda berilgan element borligini tekshirish
    Console.WriteLine(navbat.Contains(13));
        
    Console.Write("Queueda qolgan elementlar: ");
    foreach(int a in navbat)
        Console.Write(a+" ");
        
    Console.ReadKey();
  }
}
```

output: 
```Eng boshidagi element: 2
2 soni chiqarib yuborildi
5 soni chiqarib yuborildi
True
Queueda qolgan elementlar: 8 13 21
```

Maqola siz uchun foydali bo'ldi degan umiddaman. E'tiboringiz uchun rahmat.
