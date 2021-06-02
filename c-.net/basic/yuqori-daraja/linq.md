---
description: Nodirbek Abdulaxadov
---

# LINQ asoslari

**LINQ** \(Language-Integrated Query\) - bu ma'lumot manbasidan so’rov olish  uchun oddiy va qulay til. Ma'lumotlar manbayi sifatida - IEnumerable interfeysini \(masalan, standart to'plamlar, massivlar\) amalga oshiradigan obyekt, DataSet, XML hujjati bo'lishi mumkin. Ammo manba turidan qat'iy nazar, LINQ ma'lumotni olish uchun barchasi uchun bir xil usulni qo'llashga imkon beradi.

**Qisqacha qilib aytganda** **LINQ** - _kodni ixchamlashtirish va oson o'qish imkoniyatini beradi va undan turli xil ma'lumot manbalari uchun so'rovlarda foydalanish mumkin._

**LINQ** ning bir nechta turi mavjud:

* **LINQ to Objects** : Massivlar va to'plamlar bilan ishlash uchun ishlatiladi
* **LINQ to Entities** : Entity Framework texnologiyasi orqali ma'lumotlar bazalariga kirishda foydalaniladi
* **LINQ dan Sql** : MS SQL Server-da ma'lumotlarga kirish texnologiyasi
* **LINQ to XML** : XML fayllari bilan ishlashda ishlatiladi
* **LINQ to DataSet** : DataSet obyekti bilan ishlashda foydalaniladi
* **Parallel LINQ \(PLINQ\)** : parallel so'rovlarni bajarish uchun ishlatiladi

![](../../../.gitbook/assets/image%20%284%29.png)

**LINQ** so'rovlari natijalarni obyekt sifatida qaytaradi. Bu sizga natijalar to'plamida obyektga yo'naltirilgan yondashuvni ishlatishga va natijalarning turli formatlarini obyektlarga aylantirish haqida tashvishlanmaslikka imkon beradi.

**LINQ-ning afzalliklari**

* **Tanish til:** Ishlab chiquvchilar ma'lumotlar manbalarining har bir turi yoki ma'lumotlar formati uchun yangi so'rovlar tilini o'rganishlari shart emas.
* **Kamroq kod yozish:** Bu an'anaviy yondoshuv bilan taqqoslaganda yoziladigan kod miqdorini ancha kamaytiradi.
* **Tushunarli kod:** LINQ kodni yanada tushunarli qiladi, shuning uchun boshqa ishlab chiquvchilar uni osonlikcha tushunishlari va saqlab turishlari mumkin.
* **Bir nechta ma'lumot manbalarini so'rov qilishning standartlashtirilgan usuli:** Bir xil ma'lumot manbalariga so'rov yozish uchun bir xil LINQ sintaksisidan foydalanish mumkin.
* **So'rovlarning vaqt xavfsizligini** kompilyatsiya qilish: kompilyatsiya vaqtida obyektlarning turini tekshirishni ta'minlaydi.
* **IntelliSense-ni qo'llab-quvvatlash:** LINQ umumiy to'plamlar uchun IntelliSense-ni taqdim etadi.
* **Ma'lumotlarni shakllantirish:** Siz har xil shakldagi ma'lumotlarni olishingiz mumkin.

### **LINQ** dan foydalanish

LINQ dan foydalanish uchun bizga .Net Framework 3.5 va C\# 3.0 kerak bo’ladi\(foydalanish uchun minimum versiyalar\).

**System** kutubxonasiga qo’shimcha ravishda **System.Linq** kutubxonasidan foydalanamiz.****

**Misol:**

```csharp
using System;
using System.Linq;
namespace LINQ_operations
{
    class Program
    {
        static void Main(string[] args)
        {
            // Ma’lumotlar manbayi (massiv)
            string[] names = { "Bill", "Steve", "James", "Mohan" };
            // LINQ so’rovi 
            var myLinqQuery = from name in names
                              where name.Contains('a')
                              select name;
            // So’rovni ishlatish
            foreach (var name in myLinqQuery)
                Console.WriteLine(name + " ");
            Console.ReadKey();
        }
    }
}

```

**Natija:**

![](../../../.gitbook/assets/image%20%2836%29.png)

**Amaldagi LINQ metodlari ro'yxati**

* **Select** : tanlangan qiymatlarning proektsiyasini belgilaydi
* **Where** : tanlov filtrini belgilaydi
* **OrderBy** : buyurtma buyumlarini ortib boruvchi tartibda
* **OrderByDescending** : buyumlarni kamayish tartibida buyurtma qiladi
* **ThenBy** : o'sish tartibida buyumlarni buyurtma qilish uchun qo'shimcha mezonlarni belgilaydi
* **ThenByDescending** : elementlarni kamayish tartibida buyurtma qilish uchun qo'shimcha mezonlarni belgilaydi
* **Join** : ma'lum bir asosda ikkita to'plamga qo'shiladi
* **GroupBy** : elementlarni kalitlarga ko'ra guruhlaydi
* **ToLookup** : barcha elementlarni lug'atga qo'shgan holda elementlarni kalitlarga ko'ra guruhlaydi
* **GroupJoin** : elementlarning ikkala to'plamini va kalitlarga ko'ra guruhlanishini amalga oshiradi
* **Reverse** : elementlarni teskari tartibda joylashtiring
* **All** : To'plamdagi barcha narsalarning ma'lum bir shartga javob berishini aniqlaydi
* **Any** : To'plamdagi kamida bitta buyumning ma'lum bir shartga javob berishini aniqlaydi
* **Contains** : To'plamda ma'lum bir element mavjudligini aniqlaydi
* **Distinct** : to'plamdagi nusxalarni olib tashlaydi
* **Except**: ikkita to'plamning farqini, ya'ni faqat bitta to'plamda yaratilgan elementlarni qaytaradi
* **Union** : ikkita bir xil to'plamlarni birlashtiradi
* **Intersect** : Ikki kolleksiyaning, ya'ni ikkala to'plamda ham bo'lgan narsalarning kesishishini qaytaradi
* **Count** : To'plamdagi ma'lum bir shartga javob beradigan elementlar sonini hisoblaydi
* **Sum** : yig'indagi raqamli qiymatlar yig'indisini hisoblaydi
* **Average** : to'plamdagi raqamli qiymatlarning o'rtacha qiymatini hisoblab chiqadi
* **Min** : minimal qiymatni topadi
* **Max** : maksimal qiymatni topadi
* **Take** : ma'lum miqdordagi narsalarni tanlaydi
* **Skip** : ma'lum miqdordagi narsalarni o'tkazib yuboradi
* **TakeWhile** : Agar shart to'g'ri bo'lsa, ketma-ketlik elementlari zanjirini qaytaradi
* **SkipWhile** : ular berilgan shartni bajarishi sharti bilan elementlarni ketma-ketlikda o'tkazib yuboradi va keyin qolgan elementlarni qaytaradi
* **Concat** : ikkita to'plamni birlashtiradi
* **Zip** : ma'lum bir shartga muvofiq ikkita to'plamni birlashtiradi
* **First** : to'plamdagi birinchi elementni tanlaydi
* **FirstOrDefault** : to'plamdagi birinchi elementni tanlaydi yoki sukut bo'yicha qaytaradi
* **Single** : to'plamning bitta elementini tanlaydi, agar to'plamda bir yoki bir nechta element bo'lsa, istisno qo'yiladi
* **SingleOrDefault** : To'plamdagi birinchi elementni tanlaydi yoki sukut bo'yicha qaytaradi
* **ElementAt** : ma'lum bir indeksda ketma-ketlik elementini tanlaydi
* **ElementAtOrDefault** : Muayyan indeksda yig'ish elementini tanlaydi yoki indeks doiradan tashqarida bo'lsa, standart qiymatni qaytaradi
* **Last** : to'plamdagi oxirgi elementni tanlaydi
* **LastOrDefault** : to'plamdagi so'nggi elementni tanlaydi yoki sukut bo'yicha qaytaradi

[LINQ metodlarining qo’llanishiga doir misollar**.**](https://github.com/Nodirbek-Abdulaxadov/LINQ-operations)\*\*\*\*

