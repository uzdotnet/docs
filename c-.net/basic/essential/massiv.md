---
description: Shohruh Nosirov
---

# Massiv

C\#  dasturlash tilida kompyuter xotirasiga bir o’zgaruvchi yordamida bir nechta qiymatlarda foydalanishga to’g’ri keladi. Bir o’zgaruvchi bilan bir nechta qiymat ustida amallar bajarish uchun berilgan ma’lumotlar bir turga mansub bo’lishi kerak. C\#  dasturlash tilida bir o’zgaruvchi yordamida bir nechta qiymatlardan foydalanish uchun massiv degan turdan foydalaniladi. Dasturlash tillarida ro’yxat yoki jadval ko’rinishidagi ma’lumotlarni massiv deb atashadi. Massiv so’zining ma’nosi o’lcham, o’lchov demakdir. Massivning barcha elementlari bitta turga mansub bo’lib, ular bitta nom bilan nomlanadi va bir-birlaridan nomerlari \(indekslari\) bilan farq qiladi.

Endi dasturdagi ma’lumot strukturalari bilan tanishishni boshlaymiz. Dasturda ikki asosiy tur ma’lumot strukturalari mavjuddir. Birinchisi statik, ikkinchisi dinamikdir. Statik deganimizda xotirada egallagan joyi o’zgarmas, dastur boshida beriladigan strukturalarni nazarda tutamiz. Statik massivlar elementlar soni oldindan ma’lum bo’lgan va initsializatsiyalangan \(qiymat belgilangan\) massivlar hisoblanadi.  Dinamik ma’lumot tiplari dastur davomida o’z hajmini, egallagan xotirasini o’zgartirishi mumkin. Dinamik massivlar esa elementlari soni oldindan ma’lum bo’lishi va uni initsializatsiyalash \(qiymat belgilash\) shart emas. Statik massivlarning kamchiliki shundaki, agar ularning o’lchamini oldindan juda katta olinsa-yu, uning ko’p qismi keraksiz qolib ketsa, u holda xotira behuda sarflanishiga olib keladi. Shu muammoni hal qilish maqsadida massivlar C\# tilida asosan dinamik tarzda e’lon qilinadi. Massivlar dasturlashda eng ko’p qo’laniladigan ma’lumot tiplaridir. Massivlar hotirada ketma-ket joylashgan, bir tipdagi o’zgaruvchilar guruhidir. Alohida bir o’zgaruvchini ko’rsatish uchun massiv nomi va kerakli o’zgaruvchi indeksini yoziladi.

{% hint style="info" %}
_**Ta’rif:** Bir turga mansub bo’lgan yagona nom bilan saqlanuvchi tartiblangan ma’lumotlar majmuasi massiv deyiladi._
{% endhint %}

Massivlar yagona o’zgaruvchi bilan kompyuter xotirasiga saqlanadi, uning elementlari ma’lum bir indekslar bilan tartiblab joylashtiriladi. Massivlar yagona nom bilan bir nechta qiymatni o’zida mujassamlashtiradi, bularga matematikadagi vektorlarni misol keltirish mumkin. Vektor ham yagona nom bilan saqlanib uning tarkibida bir nechta qiymatni o’zida mujassamlashadi. Vektorning ham elementlari bir turga mansub va tartiblangan bo’ladi.

### **Bir o’lchovli massivlar** 

Odatda massivlar zarurat, katta hajmdagi tartiblangan, lekin chekli elementlarga oid masalalarni hal etishda yuzaga keladi. Dastur ishlatilishi davomida massivlar aniq nomga ega bo’lishi va uning elementlari ma’lum bir turda bo’lishi kerak. Bir o’lchovli massivlar kompyuter xotirasiga quyidagi shaklda saqlanadi

![](../../../.gitbook/assets/image%20%2841%29.png)

Massiv tarkibida **elementlar** mavjud bo’ladi. Massivning eng ko’pi bilan ketishi mumkin bo’lgan elementlar soni uning **o’lchamini** bildiradi. Massivning elementi turgan o’rni uning **indeksi** deyiladi. Massivning elementiga uning indeksi orqali murojaat qilinadi. Massivning indeksi sifatida butun sonlar xizmat qiladi. Har bir massiv o’zining individual nomiga ega bo’lishi kerak, ya’ni bir xil nomdagi massivlar bo’lmaydi. Ularning nomi oldin e’lon qilingan oddiy o’zgaruvchi nomi bilan ustma-ust tushmasligi kerak.

 **Statik** massivlarni e’lon qilishning umumiy ko’rinishi quyidagicha:

{% hint style="info" %}
_**&lt;tip&gt; \[\]&lt;massiv\_nomi&gt;={boshlang’ich qiymatlar}**_
{% endhint %}

Bunda _{boshlang’ich qiymatlar}_ albatta bo’lishi kerak. Misollar:

```csharp
int []A={1,4,3,1};
string[] B = { “olma”, “gilos”, “anor”};
double[] C = { 0.005, 1.234, 12.5, 13.5, 10.6 };
```

  
Yuqoridagi massivlarda massivning o’lchami uning initsializatsiya qismida qatnashgan elementlar soni bilan aniqlanadi. C\# tilida xuddi C++ da bo’lgani kabi element indeksi 0 dan boshlanadi. A\[0\] indeksli element 1 ga teng, B\[1\] indeksli element esa “gilos” ga teng va h.

Aytib o’tganimizdek, C\# tilida massivlar xotiradan unumli foydalanish maqsadida massivlarni dinamik tarzda e’lon qilishga kelishib olingan. Dinamik tarzda massivni e’lon qilishning umumiy ko’rinishi quyidagicha:

{% hint style="info" %}
_**&lt;tip&gt; \[\] &lt;massiv\_nomi&gt;=new &lt;tip&gt;\[o’lcham\]**_
{% endhint %}

Bu yerda **new** operatori &lt;o’lcham&gt;ga mos ravishda xotiradan joy ajratadi. Dinamik massivlarni e’lon qilishga doir misollar:

```csharp
n = Convert.ToInt32(Console.ReadLine());
int[] M1 = new int[10];
float[] M2 = new float[100];
double[] M3 = new double[n];
```

  
M1 va M2 nomli massivlarning elementlari uchun 10 va 100 ta joy ajratilgan. Ular ham dinamik massiv hisoblanadi. M3 massiv uchun xotiradan qancha joy ajratish foydalanuvchining o’ziga havola qilingan, ya’ni n o’zgaruvchisi klaviaturadan kiritiladi, bu o’zgaruvchi qiymati esa M3 massiv o’lchami sifatida qabul qilinadi. M3 massiv dinamik massivga yorqin misoldir.

Dinamik massiv o’lchami ham statik massiv kabi aniqlanishi lozim, faqat bunda u dastur ishlashi davomida anqlanishi bilan static massivdan farq qiladi.

Indekslar massiv elementlariga murojat qilish uchun ishlatiladi. Indeks massivdagi element sonini bildiradi .Massivdagi to’rtinchi elementga murojat qilish uchun biz 3 indeksidan foydalanishimiz kerak. Misol uchun :num\[3\]. Massiv elementlarining qiymatlarini olish va o’rnatish uchun indekslardan foydalanamiz.

```csharp
int[] nums=new int [4];
nums[0]=1; 
nums[1]=2;
nums[2]=3;
nums[3]=5;
Console.ReadLine(nums[3]);   //5
```



Va bizda faqat 4 ta element uchun belgilangan massiv mavjud bo’lgani uchun , masalan oltinchi elementni qo’llay olmaymiz nums\[5\]=5;.  Agar biz buni qilishga harakat qilsak biz **IndexOutOfRangeException**-ni  olamiz.

Statik massivlar elementlar oldindan aniqlanadi. Buning uchun sikl operatorlariga murojaat qilamiz. Masalan, quyidagi misolda dinamik massivga qiymat berish hamda uning elementlarini chop etish amallar ko’rsatilgan. Biz massiv elementlari bilan ishlashimiz uchun for sikl operatori kerak buladi. Bu haqida yetarlicha bilimga ega bo’lmasayiz [quyidagi link](https://dot-net.uz/basic/starter/for-sikl-operatori) orqali o’tsangiz Starter bulimida Suxrob Xayitmurodov yetarlicha malumot bergan. Agar for sikl operatori haqida malumotga ega bulsayiz davom etamiz.

```csharp
using System;
internal class ArrayExample
{
    private static void Main()
    {
        int[] A = new int[10];
        int i;
        for (i = 0; i < 10; i = i + 1)
            A[i] = i;
        for (i = 0; i < 10; i = i + 1)
            Console.WriteLine(‘A[‘ + i + ’]: ’ + A[i]);
    }
}
```

Bu dasturda A massivning elementlari sifatida i ning qiymatlari kelmoqda. Xuddi shunday massiv elementlarini klaviatura orqali ham kiritish mumkin. Buning uchun quyidagi kodni ko’raylik:

```csharp
using System;
 
internal class ArrayExample
{
    private static void Main()
    {
        int[] A = new int[10];
        int i;
        for (i = 0; i < 10; i = i + 1)
            A[i] = Convert.ToInt32(Console.ReadLine());
        for (i = 0; i < 10; i = i + 1)
            Console.WriteLine(‘A[‘ + i + ’]: ’ + A[i]);
    }
}
```

Massiv elementlari qiymatlaridan foydalanishga doir quyidagi sodda misolni ko’rib chiqaylik.

> **Men Shahbozga  judayam qiziqarli matematik masala berdim. Masala sharti quyidagicha: Men unga 10 ta son aytaman ularning yig’indisini topib 10 ga bo’lishi kerak buladi. Keyin Shahboz menga shu kodni yozib berdi.** **Sizham bu kodni o’z kompyuteringizda tekshirib kuring.**

```csharp
using System;
 
internal class Average
{
private static void Main()
    {
        int[] A = new int[10];
        int i;
        double S = 0;
        Console.WriteLine("Sonlarni kiriting");
        for (i = 0; i < 10; i = i + 1)
            A[i] = Convert.ToInt32(Console.ReadLine());
        for (i = 0; i < 10; i++)
            S += A[i];
        S = S / 10;
        Console.WriteLine(S);
    }
}
```

Massivlar bilan ishlaganda uning o’lchami chegarasidan chiqib ketmaslik lozim. Agar bu holat yuz bersa C\# kompilyatori **IndexOutOfRangeException** xatoligi haqida xabar beradi. Bu xatolikni siz ham sinab kurmoqchi bulsangiz quyidagi kodni kiritib , ishlatib kuring:

```csharp
using System;
 
internal class ArrayErr
{
    private static void Main()
    {
        int[] sample = new int[10];
        int i;
        // Chegaradan chiqish holati yuz bermoqda 
        for (i = 0; i < 100; i = i + 1)
            sample[i] = i;
    }
}
```

Massivlar haqida boshlang’ich malumotlarga ega bo’ldingiz degan umiddaman.

