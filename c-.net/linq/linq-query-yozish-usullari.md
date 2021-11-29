---
description: Suxrob Xayitmurodov
---

# LINQ query yozish usullari

Kamina is back again baby!! :haha

Assalomu alaykum hurmatli yurtdoshlar. Galdagi mavzuyimizda **LINQ** da **query** yozish usullari ko'rib chiqamiz. C\# tilida **query**larni yozishning 3 xil usullari mavjud. Har bir usulning o'ziga yarasha kerakli tomonlari mavjud:

1. Query Syntax
2. Method Syntax
3. Mixed Syntax \(Query + Method\)

Birinchisidan boshlaymiz: **Query Syntax** usuli har qanday murakkab querylani oson, tushunishga qulay va sodda ko'rinishga ega usul hisoblanadi. Bu usul ko'p hollarda SQL queryga juda o'xshab ketadi. Quyida siz ushbu usulning sintaksisini ko'rishingiz mumkin:

```csharp
from obj in dataSource
where condition
select obj
```

Ikkinchisidan davom ettiramiz: **Method Syntax** bugungi kunda eng mashhur usullardan hisoblanadi \(serioz\). Chunki ko'pgina murakkab vazifalarni ushbu usul bilan osonlikcha hal qilsa bo'ladi. Bu usul sintaksisi o'qishga juda oson hisoblanadi \(ko'pchilik dasturchilar tomonidan tasdiqlangan\). Lekin murakkab **query**lar uchun ushbu usulni **Query Syntax**ga nisbatan yozish birmuncha qiyin. Bu usulda **query** bir necha metodlar \(albatta nuqta\(.\)\) bilan aralashgan holda yoziladi. Quyida sintaksisini ko'rishingiz mumkin:

```csharp
DataSource.ConditionMethod().SelectionMethod()
```

Uchinchisi bilan tugatamiz: **Mixed Syntax**. Bu usul joriy usullar, **Query Syntax** va **Method Syntax**larning kombinatsiyasi desak adashmaymiz. Ushbu usul bilan **query**larni yozish bir muncha osonlashishi mumkin. Sintaksisi quyidagicha

```csharp
(from obj in dataSource
where condition
select obj).Method()
```

Agarda 10 daqiqa vaqtingizni diqqat bilan ushbu maqolaga sarflasangiz, demak siz hech qachon **query** yozish usullarida qiyinchiliklarga duch kelmaysiz!

```csharp
class LINQQueryExample // dot-net.uz uchun
{
    static void Main()
    {
        List<int> list = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
        var querySyntax = from obj in list
                          where obj > 2
                          select obj;
        foreach (var item in querySyntax)
        {
            Console.WriteLine(item);
        }
        Console.WriteLine("#____________#_____________#________________#");


        var methodSyntax = list.Where(obj => obj > 2);

        foreach (var item in methodSyntax)
        {
            Console.WriteLine(item);
        }
        Console.WriteLine("#____________#_____________#________________#");



        var mixedSyntax = (from obj in list
                           select obj).Max();

        Console.WriteLine("Max value: " + mixedSyntax);

    }
}
```

