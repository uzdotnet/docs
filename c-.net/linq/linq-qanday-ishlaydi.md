---
description: Jasurbek Xasanboyev
---

# LINQ qanday ishlaydi?
LINQ ma’lumotlar manbasiga murojatlar yuborish va ma’lumotlarni qayta ishlash uchun hizmat qiladi. LINQ so`rov(query)lar ma’lumotlar manbasi turlariga qarab bo`limlarga bo`linadi: 
![image](https://user-images.githubusercontent.com/81855769/121767016-353e0f00-cb6f-11eb-80a9-4a10ee1bf0a1.png)
Misol tariqasida eng oddiy so`rov turini ko`rib chiqamiz: 
```
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
LINQ so`rov yordamida to`plam elementlari orasidan 80 dan kattalaridan  yangi to`plam hosil qilindi va ekranga chiqarildi.
