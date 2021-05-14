---
description: Sobirjonov O'tkirbek
---

# Continue

Keling bu darsda sizlar bilan “continue” kalit so’zi bilan tanishamiz. “continue” kalit so’zi Bu davom etish degan manoni bildiradi . Aslida “continue” kalit so’zidan juda ham kam Foydalanamiz. Chunki “continue” odatda sikllarning ichida keladi. Keling bir dastur ko’raylik

```csharp
using System;

namespace MyApplication
{
  class Program
  {
    static void Main(string[] args)
    {
      for (int i = 0; i < 10; i++) 
      {
        if (i %2 == 0) continue;
        else Console.WriteLine(i); 
      }    
    }
  }
}
```

Biz bu dasturda 1 dan 10 gacha bo’lgan toq sonlarni ekranga chiqarish dasturini tuzdik. Bu “continue” kalit so’zi siklni 1 qadam oldinga yur deb buyruq beradi va shu zahotiyoq Sikl \(ya’ni bu rasmda for\) qadami \(ya’ni int i\) ning qiymati 1 ga oshadi. “continue” buyrug’I juda ham oson bolgani uchun tushuntira oldim deb o’ylayman. Endi Dasturlarda ko’rsak!

```csharp
using System;

namespace MyApplication
{
  class Program
  {
    static void Main(string[] args)
    {
      for (int i = 0; i < 10; i++) 
      {
        if (i == 8) continue;
	      else Console.Write(i + “ “);
      }    
    }
  }
}
```

Natijada Consolega : 0 1 2 3 4 5 6 7 9 chiqariladi.

