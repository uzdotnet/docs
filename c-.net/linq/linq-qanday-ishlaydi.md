---
description: Jasurbek Xasanboyev
---

# LINQ qanday ishlaydi?

LINQ ma'lumotlar bazasiga \(data source\)ga murojaatlar yuborish va ma'lumotlarni qayta ishlash uchun xizmat qiladi. LINQ so'rovlar \(query\) ma'lumotlar manbasi turlariga qarab bo'limlarga bo'linadi:

![](../../.gitbook/assets/image%20%2822%29.png)

Misol tariqasida eng oddiy so'rov turini ko'rib chiqamiz:

```csharp
class LINQQueryExample // dot-net.uz uchun
{
    static void Main()
    {
        // Ma'lumotlarni to`plam shaklida shakllantirib olamiz
        int[] scores = new int[] { 97, 92, 81, 60 };

        // Query yozamiz
        IEnumerable<int> scoreQuery =
            from score in scores
            where score > 80
            select score;

        // Query ma'lumotlaridan foydalanamiz 
        foreach (int i in scoreQuery)
        {
            Console.Write(i + " ");
        }
    }
}
// Output: 97 92 81
```

> Tepadagi kodda LINQ so'rov yordamida to'plam elementlari orasidan 80 dan kattalaridan yangi to'plam hosil qilindi va ekranga chiqarildi ;\)

