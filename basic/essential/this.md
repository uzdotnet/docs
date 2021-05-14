---
description: Shohruh Nosirov
---

# this

Biz bilamizki, obyektlarga initsializatsiya\(qiymat belgilash\) konstruktor orqali hosil qilinadi. Har qaysi yaratilgan obyekt parametrning aniq bir qiymatini qabul qiladi. Demak hozircha oddiy classni kurib turamiz.

```csharp
class p
{
    // Xossa (avtomatik)
    public int x { get; set; }
    public int y { get; set; }
    // Konstruktorlar
    public p()
    {
    }
    public p(int v1, int v2)
    {
        x = v1;
        y = v2;
    }
}
```

  
Bu dasturda nima jarayon ketayotganini bilsangiz kerak agar bilmasangiz qisqacha yana tushuntirib o’tib ketaman. Demak diqqat qilamiz!.

Biz **p** nomli class yaratdik. Unda 2 ta xossa: **x** va **y** va qo'shimcha tarzda yana 2 ta konstruktor ham bor. Sizda savol tug’ilgan bo'lishi mumkin:

{% hint style="info" %}
**Birinchi konstruktor nega yaratildi, u hech qanday vazifa bajarmayabdi?**
{% endhint %}

Men bunga qisqacha javob beraman. Agar biz dasturda qo'shimcha konstruktor yaratmasak jimlik bo'yicha \(yani yaratmasak ham uzi bitta konstruktor mavjud bo'ladi\) yaratilgan buladi. Bu holatda esa biz yana bitta konstruktor yaratdik. Unda 2 ta argument mavjud \(argument deganlarim v2 va v2 lar\) va u 2 ta xossaga qiymat taminlash amalini bajaryabdi.

Bu jarayonni tushundingiz degan umiddaman. Demak konstruktorni vazifasini tushunib oldik endi esa, **this** ning nima vazifa bajarishini tushuntirib o'taman. Buning uchun biz yana xuddi shu classni qaytadan yozamiz.

```csharp
class p
{
    // Xossa (avtomatik)
    public int x { get; set; }
    public int y { get; set; }
    // Konstruktorlar
    public p()
    {
    }
    public p(int x, int y)
    {
        x = x;
        y = y;
    }
}

```

  
Bu yerda avvalgi classdan farqi 2-konstruktorga 2 ta argument nomlari class xossalarining nomlari bilan bir xil bo'lib qoldi. **this** xuddi shu holatda kerak. Ya'ni, agar biz konstruktorda xossaning nomlaridan argument sifatida foydalansak shu kalit so’zdan foydalanmiz. Ammo, sizda “nega unday qilayabmiz” degan savol tug’ilgan bulishi mumkin albatta. Agar, **this** dan foydalanmasak konstruktorda xossaga qiymat berishda nizolar kelib chiqishi mumkin \(ya'ni xatoliklar\) . Bu yerda huddiki xossaga o'ziga-o'zini ta'minlaganday bo'lib qoladi. this dan foydalanishni quyidagi misolda ko'rishingiz mumkin.

```csharp
class p
{
    // Xossa (avtomatik)
    public int x { get; set; }
    public int y { get; set; }
    // Konstruktorlar
    public p()
    {
    }
    public p(int x, int y)
    {
        this.x = x;
        this.y = y;
    }
}

```

  
Endi hech qanday xatoliklar bo'lmaydi this.x bu o'sha classdagi xossa deb hisoblanadi x ni uzi esa konstruktordagi argument sifatida qabul qilinadi. Keyingi qatorda ham xuddi shu xolat bajariladi. Konstruktorda classning xossa nomlaridan foydalanish yaxshiroq. Chunki ba'zi xossalar **private** \(yani faqat shu classni ichida foydalanish mumkin\)  bo'lsa, o'sha classni obyektini yaratgan paytimiz unga konstruktor orqali qiymat bera olamiz. 

Xulosa qilib aytganda, agar biz konstruktorda argumentlarni nomlashda xossa nomlaridan foydalansak,  **this** dan foydalanar ekanmiz xolos. this haqida ma'lumotga ega bo'ldingiz degan umiddaman. Bu kodlarni albatta o’zingiz ham sinab kuring.

