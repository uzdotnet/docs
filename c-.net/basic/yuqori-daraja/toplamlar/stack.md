---
description: Mamataliyev Diyorbek
---

# Stack

To’plamlar bilan tanishishda davom etamiz. Biz o’rganadigan yangi to’plam – **Stack** avvalgilaridan boshqacharoq xossalarga ega. Stack shunday to’plamki, unga yangi elementni faqat ustidan qo’shish  mumkin, elementni undagi elementni olib tashlash ham uning ustidan bajariladi. Shuning uchun Stack ni *LIFO* (*Last In First Out*) collection deb ham aytiladi. Ya’ni, **Stack**ga eng oxiri qo’shilgan element undan eng birinchi bo’lib chiqib ketadi.

**Stack**ni yaxshiroq tasavvur qilishingiz uchun hayotiy misol sifatida rasmdagi idishga solingan sharlarni misol qilib keltirishimiz mumkin: 

![Stackga misol - idishdagi sharchalar](https://user-images.githubusercontent.com/91861166/138088109-0772ccdb-fd2f-48c8-9148-2268e6a8718f.jpg)


Sharchalardan birorta olishimiz kerak bo’lsa faqat eng ustidan boshlab olish imkoniyatimiz bor(o’rtasidan yoki oxiridan emas). Yangi sharchani qo’ymoqchi bo’lsak ham eng ustiga qo’ya olamiz. 
Demak biz **Stack** to’plami ustida quyidagi amallarni bajara olamiz:

**Push()** – **Stack**ga yangi element qo’shadi. Element Stackga eng yuqorisidan qo’shiladi (huddi quyidagi rasmdagidek);

**Pop()** – **Stack**ga oxirgi qo’shilgan element qiymatini qaytarib, bu elementni Stackdan olib tashlaydi. Elementni olib tashlanayotganda oxiri qo’shilgani birinchi bo’lib chiqib ketadi;

**Peek()** – **Stack**ning eng yuqorisidagi (oxirgi qo’shilgan) element qiymatini qaytaradi, lekin Stackdan olib tashlamaydi;

**Count** – **Stack**dagi elementlar sonini qaytaradi;

**Clear()** – **Stack**dagi barcha elementlarni o’chirib yuboradi. Bundan so’ng Stackdagi elementlar soni 0 ga teng bo’lib qoladi;

**Contains()** – **Stack**da biror element bor yoki yo’qligini tekshiradi. Bor bo’lsa *true*, yo’q bo’lsa *false* qiymat qaytaradi.

![Push va Pop amallari](https://user-images.githubusercontent.com/91861166/138085847-b8285bf1-dc86-483e-9ab6-e42b91ad4d62.jpg)


Savol tug’ilishi mumkin: Shuncha cheklovlarga ega bo’lgan to’plam dasturlashda nima uchun kerak? Biror qulayligi bormi? Albatta. Masalan, siz ko’p marta ishlatadigan **Undo/Redo** (**Ctrl+Z/Ctrl+Y**) ni ishlatganingizda bajargan ishlaringizni Stackga yozib boradi. **Ctrl+Z** qilganingizda oxirgi qilgan amalingiz birinchi bo’lib orqaga qaytadi va boshqa bo’sh stackga joylanadi (ikkinchi stack **Ctrl+Y** qilganingizda kerak bo’ladi).  Yoki yana bir misol brauzeringizdagi avvalgi yoki keyingi ochilgan web-sahifalarga o'tish uchun ishlatiladigan **back/forward** tugmachalari ham **Stack** yordamida ishlaydi.

![back va forward tugmachalari](https://user-images.githubusercontent.com/91861166/138086962-278ee084-abfa-4e72-8bbd-444e8c57d8a6.png)

**Stack** haqida tushunchaga ega bo’lgan bo’lsangiz endi uni kodda ishlashini ham ko’raylik. **Stack** to’plami `System.Collections.Generic` nomlar makonida joylashgani uchun avval shu nomlar makonini chaqirishimiz kerak bo’ladi:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
public class program
{
    public static void Main()
    {
        //yangi bo'sh Stackni e'lon qilish
        var sonlar=new Stack <int>();
        
        //Stackga yangi elementlarni qo'shish
        sonlar.Push(2);
        sonlar.Push(5);
        sonlar.Push(7);
        
        //Stackdagi elementlar soni:
        Console.WriteLine(sonlar.Count);  //3 
        
        //Stackdan oxirgi qo'shilgan element qiymatini pop() orqali olish
        int b=sonlar.Pop();  //7 ga teng element Stackdan chiqib ketdi
        Console.WriteLine("b="+b);
        Console.WriteLine("Elementlar soni: "+sonlar.Count); //2
        
        //Stackdan oxirgi qo'shilgan element qiymatini peek() orqali olish
        int c=sonlar.Peek();  //Stackdagi elementlar soni o’zgarmadi
        Console.WriteLine("c="+c);
        Console.WriteLine("Elementlar soni: "+sonlar.Count);
        
        Console.ReadKey();
    }
}
```

output:
```3
b=7
Elementlar soni: 2
c=5
Elementlar soni: 2
```

Shuning bilan darsimiz nihoyasiga yetdi. Agar Stack to'plamini sizga yaxshi tushuntira olgan bo'lsam xursandman. E'tiboringiz uchun rahmat.
