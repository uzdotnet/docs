---
description: Xondamir Abduxoshimov
---

# API dan foydalanish

### API bilan tanishuv

**API** \(Application Programming Interface\) - bu bir necha dastur o'rtasida muloqotni ta'minlash uchun foydalaniladigan tizim.Keling, ushbu tushunchaga soddaroq tilda to'xtalib o'tamiz. 

Biz odatiy hayotimizda ko'plab dasturlardan foydalanamiz, xususan ijtimoiy tarmoqlar\(_facebook_, _telegram_, _instagram_...\)dan. Sizningcha ushbu ma'lumotlar foydalanuvchi oynasiga qanday qilib tezkorlik bilan uzatiladi? Buning javobi oddiy. Bir dastur bilan ikkinchi dastur o'rtasida muloqotni yaxshilash va aniq tartiblangan holatda uzatish API orqali amalga oshiriladi.  

Web API larni yaratish bu Web Backend dasturchilarning vazifasi hisoblanadi. .NET da ASP.NET web frameworki orqali turli ko'rinishdagi Web API lar yaratish mumkin. 

### Web API bilan ishlash

Web API bilan ishlashimiz uchun suxbatimizga 2 tushunchani kiritamiz:

* Request
* Response

Tasavvur qiling, biz ob - havo ma'lumotlarini olib beruvchi dastur tuzmoqdamiz va biz tayyor Web API dan foydalanishimiz kerak. Bu holatda kerakli ma'lumotni olishimiz uchun berilgan url ga request jo'natishimiz lozim bo'ladi va shundagina bizga ma'lumot qaytadi. Berilgan requestga javob qaytishi response hisoblanadi.

Web API dan kelgan data bir necha ko'rinishda bo'lishi mumkin. Ulardan hozirda keng qo'llaniladigani - JSON \(JavaScript Object Notation\).

Request lar esa asosan 5 turli bo'ladi:

* Get - datalarni olish
* Post - yangi data yaratish
* Put - berilgan datani taxrirlash
* Delete - berilgan datani o'chirish
* Patch - berilgan datani aynan bir maydonini taxrirlash

Keling endi amaliy qismga yuzlanamiz. Bizga ajratilgan mavzu faqatgina API dan foydalanish bo'lgani uchun biz API ga qanday qilib request jo'natish va qaytgan response dan kerakli ma'lumotlarni ajratib olishni ko'rib chiqamiz. Bu kabi ishlarni amalga oshirish uchun bir necha namespace lar mavjud. Amaliyotimizda **System.Net.Http** namespace idan foydalanamiz va CRUD amallaridan faqatgina Get bilan tanishamiz. 

Keling ramazon ro'zasi og'zi ochish va yopish vaqtlarini olib beruvchi ConsoleApplication turkumiga mansub kichik dasturcha tuzib ko'ramiz. Vaqtlarni olish uchun tayyor [API](https://ramadan.uz/api/v2/docs) dan foydalanamiz.

```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace Working.With.API
{
    class Program
    {
        static void Main(string[] args)
        {
            //Asosiy API urli
            string baseApiUrl = "https://ramadan.uz/api/v2/";

            //Hudud idsi
            int regionId = 1;

            //Hudud bo'yicha url
            string regionsAPI = $"regions/{regionId}/dates/today";

            //Get metodiga murojaat
            var data = Get($"{baseApiUrl}{regionsAPI}");

            //qaytgan datani ekranga uzatish
            Console.WriteLine(data.Result);

            Console.ReadLine();

        }

        private static async Task<string> Get(string apiUrl)
        {
            using (HttpClient client = new HttpClient())
            {
                //Urlga request jo'natish va responseni qabul qilish
                var response = await client.GetAsync(apiUrl);

                //response ichidan contentni ajratib olish
                var content = await response.Content.ReadAsStringAsync();

                return content;
            }
        }
    }
}
```

![ekrandagi holat](../../.gitbook/assets/image%20%28105%29.png)

Agarda natijani json visualizer ko'rinishida ko'rsak. Quyidagicha ko'rinish oladi:

![jSON holatda ko&apos;rnishi](../../.gitbook/assets/image%20%28106%29.png)

Endi berilgan satr ichidan o'zingiz kerakli bo'lgan ma'lumotni olishingiz va ularni parse qilishda [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) paketidan foydanishingiz mumkin. **HttpClient** class tarkibida boshqa request metodlari ham mavjud. 

Qisqacha API nimaligi va undan qanday foydalanish mumkinligi to'g'risida tanishib o'tdik.







