---
description: >-
  Kross platforma, open source va dasturchilar uchun IOT, Mobile, Desktop, Web,
  Game turdagi maxsulotlar ishlab chiqish uchun bepul platforma
---

# .NET ga xush kelibsiz

Assalomu alaykum mening qadrdonlarim! Sizlarga .NET bo'yicha bilim berishni bugundan niyat qildim. Agar sizlarni Microsoft kompaniyasi tomonidan yaratilgan maxsulotlar qiziqtirsa va o'sha maxsulotlar orqali o'z maxsulotingizni ishlab chiqmoqchi bo'lsangiz, siz hozir yo'nalish tanlashda adashmadingiz! .NET  GA XUSH KELIBSIZ.

![Qaysi yo&apos;nalishdan ketmoqchisiz?](../.gitbook/assets/image%20%2827%29.png)

### .NET tillari

Siz .NET ilovalarini ishlab chiqish uchun C\#, F\#, Visual Basic tillaridan foydalanishingiz mumkin.

### .NET ni yuklash

Barcharga ma'lumki, .NET frameworklarining 3 turi hozirda faoliyatda. ".NET Framework", ".NET Core", ".NET5". Uchchala frameworkda ham SDK va Runtime bor. .NET SDK - dasturning qurilishi va ishga tushishini taminlaydi. .NET Runtime - Dasturning ishga tushishini taminlaydi xolos. Aytmoqchimanki, SDK o'zining ichiga Runtime ni ham oladi. Agar o'zining ichiga olsa nega kerak?

Barchamizga ma'lum .NET platformasida yozilgan ilovalarni ishga tushirish uchun .NET Runtime lari kerak bo'ladi. Bu sizga C++ emas. Istalgan kompyuterda ishga tushib ketaveradigan. Ya'ni Windows tizimi kompyuterga yangi o'rnatilgan paytda C++ Runtime lari bo'ladi. Shuning uchun C++ da yozilgan ilovalarni ishga tushirishda xech qanday so'rov bo'lmaydi. Mana endi sekin sekin Windowsning yangi versiyalarida .NET frameworklari ko'zga ko'rinyapti. 

{% hint style="info" %}
Aytaylik men dasturchiman va .NET \(C\#\) da biror ilova ishlab chiqdim, yoki Telegramga o'xshagan dastur... xullas nima farqi bor.... Keyin uni do'stimni kompyuteriga o'tkazdim. Do'stim esa dasturchi emas. Shu bilan birgalikda .NET SDK ham o'rnatmaydi, SDK dasturchiga kerak xolosda. Chunki yozgan kodini build qilib berishi kerak bo'ladi. Oddiy odam esa kod yozmaydi. Dasturchi bo'lmagan oddiy odamga .NET Runtime beriladi. Yani Runtime dasturini kompyuteriga install qilgandan keyin, bizning dasturni ochishda muammo bo'lmaydi. Aks holda .NET Frameworkini o'rnat didi. 
{% endhint %}

Demak SDK va Runtime farqini tushinib oldingiz.

 Keling, ushbu frameworklarning farqlarini ko'rib chiqamiz.

{% tabs %}
{% tab title=".NET Framework" %}
Ushbu framework orqali .NET ilovarini faqat windows operatsion tizimi uchun ishlab chiqish mumkin. \(Tolka windows :\). .NET Frameworklarining turli versiyalari bor va bular 4.7.2 gacha yetib kelgan.  
  
.NET Framework Dev Pack \(SDK\): [https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-developer-pack-offline-installer](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-developer-pack-offline-installer)  
.NET Framework Runtime: [https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-web-installer](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-web-installer)
{% endtab %}

{% tab title=".NET Core" %}
.NET trendga chiqayotgan bir paytda, Java va .NET dasturchilari o'rtasida muzokaralar kelib chiqdi, chunki C\# bu Microsoftning Javasi. Bu yerda muammo nima edi? C\# orqali faqat Windows OS ga ilova yozish mumkin edi. Java da edi muammosiz barchasiga. Ushbu muammolardan keyin Microsoft ham o'zining cross platformali frameworkini ishlab chiqdi. Uning nomi .NET Core edi. Bu framework orqali Windows, Linux, MacOS, Docker \(Docker haqida [bu yerdan](https://www.youtube.com/watch?v=trW0gihZ78E&list=PL_WK6W0Gn1I4jcUIwAUkcLM76k08Bqi2K) o'rganasiz\) OS lariga ham ilovalar yaratish imkoni bor edi. Keyinchalik ko'p dasturchilar .NET Core ga o'tishdi. Qoladiganlari qoldi ham... Chunki Ko'p loyihalar .NET Frameworkda ko'tarilgan edi. Uni .NET Core ga olish da esa muammolarga duch kelish mumkin edi. Agar faqat Windows da ish qiluvchilar bo'lsa bundan muammo emasdi lekin... Aytganimdek, hozirda ham .NET Frameworkda ish qiladiganlar bor.

.NET Core SDK: [https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-3.1.408-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-3.1.408-windows-x64-installer)  
.NET Core Runtime: [https://dotnet.microsoft.com/download/dotnet/3.1/runtime](https://dotnet.microsoft.com/download/dotnet/3.1/runtime)  
{% endtab %}

{% tab title=".NET 5" %}
Endi deyarli loyihalarda muammolar yo'q edi, yagona muammoni qo'shmaganda. Ko'p dasturchilar .NET Core da ishlaydi, qolganlari esa .NET Frameworkda. Qaysidir Service lar yoki paket, kutubxonalar .NET Frameworkda yozilgan edi, ularning ko'pi hali .NET Core ga olinmagan edi. Aytmoqchimanki, katta loyihalarni ishlab chiqishda, kimdir qaysidir service ni .NET Frameworkda yozgan, masalan tayyor kutubxonani. Asosiy loyiha esa .NET Core da ko'tarilgan. Endi anavi kutubxonadan foydalanishda ozgina muammo kelib chiqishi mumkin. Chunki ularning qurilishi bir biriga to'g'ri kelmaydi. 1 ta gina yo'l bor edi. .NET Framework loyihasini .NET Core ga konvertatsiya qilish kerak edi. Qilishni ham yo'lini topishdi ammo barbr optimal emasdi. Keyin ular .NET5 ni ishlab chiqishga kirishishdi. Bu uchun tashqaridan ko'plab kontributerlar \(ko'ngilli dasturchilar\)  ham jalb qilingan edi. Hozirda hali ham uning ustida ish olib borilmoqda. Bu frameworkni oddiy qilib tushintirganda .NET Framework + .NET Core ham deyish mumkin. Ya'ni endi ishlar yana ham standartlashdi. .NET Standart edi. .NET 5 da loyiha ko'tarilsa, istalgan frameworkdagi service larni qabul qilad oladi. Kimdir Core da yoki Frameworkda yozsa kutubxonalarni. .NET5 orqali ularni bemalol import qilib ishlatish mumkin edi. Qo'rqmasdan ayta olaman, hozirda barcha NET 5 ga o'tyapti, ba'zi injiqlarni hisobga olmaganda.

![](../.gitbook/assets/image%20%2882%29.png)

.NET SDK: [https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-5.0.202-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-5.0.202-windows-x64-installer)  
.NET Runtime: [https://dotnet.microsoft.com/download/dotnet/5.0/runtime](https://dotnet.microsoft.com/download/dotnet/5.0/runtime)
{% endtab %}
{% endtabs %}

Keling quruq SDK ni o'zi orqali "Hello World" ni ekranga chiqarishni o'rganamiz.

### Hello World! \(Hech qanday muhitsiz\)

Hamma tilda ishlash uchun muhit kerak bo'ladi. Huddi avvalgi mavzuda gapirgan Visual Studio yoki IntelliJ IDEA lar kabi. Aslida kodlar qanday quriladi. Amalga oshishi qanday bo'ladi? Qaysidir ma'noda bu jarayonni ham "Dasturlashda tafakkur" tushunchasiga misol qilsak bo'laveradi. Shunchi men o'zimni boshimdan o'tkazganman. Har xil savollar bo'ladida...  
 - Loyihamga nuget \(paketlar menejeri\) dan paket o'rnata olmayapman?  
 - Dasturni kompilatsiya qilib bo'lmayapti?  
 - Visual Studio dasturi meni kompyterimga tushmayapti?  
Shunday savollarni ko'pini o'quvchilarimdan eshitganman. Ushbu gap so'zlardan keyin "Dasturlashda tafakkur" nomli qizg'in bir tushunchani kiritdim \(o'zimni lug'atimga :\). Agar bizning kodlarimiz qay tarzda build \(qurilish\) bo'lishini bilganimizda, bizga Visual Studio kerak emas edi. Kerak bo'lsa o'zimiz Visual Studio yaratgan bo'lardik. Qachonlardir C++ uchun yangi muhit qilgan edim C\# orqali. Bu bilan nima demoqchiman? Keling "Hello World" natijani olish uchun visual studiodan kechib turamiz bir gal.... Demak boshladik.

### .NET SDK ni o'rnatamiz.

Avvalo .NET SDK ni yuklab olishimiz kerak bo'ladi [bu yerdan](https://www.youtube.com/watch?v=trW0gihZ78E&list=PL_WK6W0Gn1I4jcUIwAUkcLM76k08Bqi2K).

Visual Studio esa siz va .NET SDK o'rtasidagi vositachi xolos. Keling Visual Studioni ishini o'zimiz ham qilib ko'ramiz, vaziyatni baholash uchun. Hullas SDK ni yukladik, endi uni install qilamiz. Menimcha qiyinchilik tug'diymaydi. Agar xatolik bersa, demak avval .NET ning boshqa versiyasi ustanovka qilingan bo'ladi, o'shani o'chirib tashlab keyn buni install qlish kerak, agar lozim topsangiz. Menimcha boshqa xatolik yuz bermaydi. SDK o'rnaganini tekshirish uchun CMD ni ochamiz. buning uchun WIN+R klavishlari bosiladi va CMD deb yoziladi.

![Vipolnit](../.gitbook/assets/image%20%2864%29.png)

CMD ga "dotnet" deb yozish kifoya. Agar .NET SDK o'rnatilgan bo'lsa, ushbu kalit  so'zni taniydi, aks holda bu so'z notanish deb inglizcha yoki ruscha gap chiqadi.

![Anaa dotnet ni tanigani uchun shu narsalar chiqdi](../.gitbook/assets/image%20%2811%29.png)

### Error berib qolishi mumkinmi?

{% hint style="info" %}
Albatta error ham berishi mumkin, faqat bir holatda.  
_'dotnet' is not recognized as an internal or external command_  
Yoki dotnet SDK install bo'lmagan bo'ladi, yoki CMD ni avvalroq ochib olgansiz \(SDK install bolishidan avval\). Muammoni hal qlish uchun CMD ni qayta ishga tushirib yuborish talab etiladi.
{% endhint %}

### Yangi loyiha yaratish

Yangi loyiha yaratish uchun CMD ni orqali ushbu buyruqni ishga tushiring:

```bash
> dotnet new console -o MyApp
```

So'ngra yangi yaratilgan MyApp direktoriyasiga qayting, uning uchun:

```bash
> cd MyApp
```

**Bular qanday ma'noni bildiradi?**

* `dotnet new console` buyrug'i yangi konsul loyihasini yaratish uchun ishlatiladi
* `-o` parametri esa MyApp nomi papkaga loyiha fayllarini joylashligini bildiradi. output so'zidan olingan. Loyihani qaysi papka ichiga yaratish kerakligini bildiradi.
* `cd MyApp` buyrug'ining vazifasi, joriy turgan direktoriyadan berilgan manzilga o'tish kerakligini bildiradi.

MyApp papkasidagi asosiy fayl  - Program.cs fayli bo'ladi.

{% code title="Program.cs" %}
```csharp
using System;
namespace myApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```
{% endcode %}

### Error berib qolishi mumkinmi?

`"Console Application" could not be created. Access to the path 'C:\Windows\System32\myApp' is denied.` Bizga ushbu errorni berishi mumkin. Buning ma'nosi Loyiha yaratilayotgan joyga o'zgartirish kiritish mumkin emas. Chunki bu sistema fayllari turadigan joy bo'lishi mumkin. Agar sizda ushbu xatolik bersa, siz joriy manzilni o'zgartirishingiz mumkin. Masalan: `cd d:/dasturlar`

### Dasturni ishga tushirish

CMD da quyidagi buyruqni ishga tushiring:

{% code title="Command Prompt" %}
```bash
D:\dasturlar\MyApp> dotnet run
Hello World!
D:\dasturlar\MyApp>
```
{% endcode %}

Do'stlar menimcha o'zingizning birinchi .NET ilovangizni yaratdingiz! Tabriklayman

