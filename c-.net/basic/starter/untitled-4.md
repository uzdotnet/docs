---
description: Suxrob Xayitmurodov
---

# Kommentlar

![](../../../.gitbook/assets/image%20%2884%29.png)

Hech kod yozish mobaynida adashib ketgan paytlaringiz ham bo’lganmi. Menimcha bu hol bir necha bor takrorlangan. Shaxsan men har doim kodimni tartibga keltirmasam besh daqiqa ichida qaysi qatorga qanday kod yozganimni eslay olmayman, sababi kodim bir necha yuzlab qatorlarni o’z ichiga oladi. Shu sababli barcha qatorlarda ma’lum bir qismiga izohlar qoldirib ketaman. Izohlardan \(kommentlardan\) C\# kodlarini tushuntirish, uni yanada tushunarli qilish, tartiblash va ixcham shaklga keltirish uchun foydalanish mumkin. Bu qanday bo’ladi?   
C\# dasturlash tilida ikki xil kommentlar mavjud:  
1.Fikrlar uchun kommentlar, ya’ni siz yozgan kodingizni izohlab, uning qanday kodligini ta’kidlab o’tasiz, ushbu kommentni yozish uchun shunchaki ikkita **// beligisini yozasiz**

```csharp
//Konsolga chiqadigan satrli matn
Console.WriteLine("Shaxboz aka yengi epizodim deb doim videolarini boshlaydi");
```

2. Ko’p qatorli kommentlar, ya’ni bir necha qator yozgan kodingizni izoh sifatida olib qo’yasiz, shunda kodingiz kompilyatsiya jarayonida e’tiborsiz qoldiriladi. Uni /\*_mana shular orasiga yozasiz\*_/ :

```csharp
/*
string fo0 = COnsole.ReadLine();
string[] tokens = foo.Split(',');
List<int> nums = new List<int>();
int oneNum;
foreach(string s in tokens) {
    if(Int32.TryParse(s, out oneNum))
        num.Add(oneNum);
}
*/
```

Alohida aytib o’tish kerak! Kommentga olingan har qanday kod yoki ta’kid C\# tomonidan e’tiborga olinmaydi.

