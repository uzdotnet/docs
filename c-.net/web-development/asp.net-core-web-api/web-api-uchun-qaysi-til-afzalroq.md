---
description: Muhammad Abdulloh Komilov
---

# Dependency Injection

Dependency Injection (DI).

Juda ko’p insonlar Dependency Injection (DI) haqida har-hil tafsilotlarga ega, va bu juda ko’plab muhokamalarga olib kelgan mavzu. Biz bilamizki juda ko’p discuss ya’ni muhokamalarda Dependency Injection (DI) haqida gap ketadi lekin buni aslida nima ekanligini va qanday ishlashini ko’pchilik bilmaydi va xato fikrlaydi. Biz shu maqola orqali Dependency Injection(Qaramlikdan qutqarish) haqida tiniqroq fikrga ega bo’lamiz. Dastlab biz Dependency nima ekanligi haqida gaplashamiz. 

## Dependency (Qaramlik) nima?
Dependency nimaligini dastlab oddiy misolda ko’rishimiz mumkin. Faraz qilaylik bizda Class A va Class B bor.  

![](https://user-images.githubusercontent.com/91861166/158005825-6c101ec8-5ec5-487e-ba08-72688fc8ca7b.png)
    
Hozirgi holatda nima bo’lyabdi Class A, Class B ga qaram bo’lyabdi. Misol uchun bu eng soddasi. 

**Dependency Qanday boshqariladi?**

Class A, Class B ning objectiga ega bo’lish uchun Class A quyidagi variantlardan birini ishlatadi. 

![](https://user-images.githubusercontent.com/91861166/158005849-f38ec3c7-4d4e-43f2-bf72-c62189ffb83c.png)
 
  1.	Holatda B Classdan object yaratvoladida unga Dependency(qaram) bo’ladi.
  2.	Holatda esa B Class ni faqat gina kuzatib turadi ya’ni unda bo’lgan o’zgarishlarni kuzatib turadi va bunda ham qaram bo’ladi.
  3.	Bu holatda esa B Classdan Objectni qabul qilib oladi. Endi bu vaziyatda A Class B Class ga qaram bo’lmaydi, endi buni holatini  (IoC) boshqaradi ya’ni dependency IoC ga bog’liq bo’ldi.  

Endi bizda IoC bu qayog’dan paydo bo’ldi ekan? u nima o’zi? Degan savol paydo bo’lishi mumkin. Biz bu savol haqida ham fikringizni tiniqlashtirib olishingizga yordam beramiz 😊.
Ho’sh endi nima qilamiz endi chuqurroq kiramiz, ichkarigacha.
Endi biz Dependency injection ni mohiyatini o’rganishdan oldin biz bir narsani ko’rib chiqishimiz kerak.

## Inversion of Control (IoC).

**Ho’p Inversion of Control (IoC) o’zi nima?**

Inversion of Control bu termin ya’ni Programming style(dasturlash uslubi). Bu terming atamasi dastur yo’nalishi(oqim) teskari bo’lgan yo’nalish(oqim) ga ishora qiladi, ya’ni odatdagidan o’zgacha dasturlash uslubi. A va B Class lar misolida ko’rganimizdek bu yerda bog’liqliklar framework yoki runtime vaqtida bog’liqliklar amalga oshiriladi.

Bundan tashqari IoC umumiy(OOP ga yo’naltirilgan dasturlash tillari uchun) atama bo’lib bu faqat Di bilan cheklanib qolmaydi. Keep learning 😊.
Aslida Dependency Injection (DI) va Service Locator IoC ning implementatsiyasi desak bo’ladi yoki IoC manashu ikki versiyasi orqali ishlaydi desak ham bo’laveradi(bo’lo’radi). 

Misol uchun: Sizning Client Classingiz Service Classining komponentasidan foydalanishi kerak deylik. U holda siz qila oladigan eng yaxshi narsa Client Classi yoki Service Classi emas, balki IService Interface’si haqida habardor qilishdir. Shunday qilib siz istalgan vaqtda (va qancha marta hohlasangiz) va siz host kodidan tashqari holatda (without breaking the host code) “ba’zi inglizcha terminlar uzbekchada boshqacha bo’lib ketadi ekan”, Service Classini amalga oshirishni o’zgartirishingiz mumkin.

**IoC Implementation**
 
![](https://user-images.githubusercontent.com/91861166/158005871-69c343a4-c736-4b28-b75c-59d3707cdecc.png)

IoC ning implementatsiyasiga Event va Delegate ham kirar ekan, lekin asosan Dependency Injection qo’llaniladi juda ko’p hollarda.

**IoC va Di**

Dependency Injection (DI) va Inversion of Control (IoC) terminlari (atamalari) odatda bir xil design pattern ni tavsiflash uchun bir birining o’rnida(interchangeably) ishlatiladi.
Dependency Injection ning dastlabki nomi IoC bo’lgan.
Ammo lekin biroq [Martin Fowler](https://martinfowler.com/) (enterprice darajadagi dasturlarni loyihalaydigan olim) buni DI deb nomlashni taklif qildi ya’ni Dependency Injection deb nomlashni. Chunki barcha frameworklar yoki runtimelar boshqaruvlarni qandaydur tarzda nazorat qiladi, va u bu nazoratning qaysi tomoni teskari bo’layotganini bilmoqchi edi.

**Vanihoyat Dependency Injection (DI)**

DI – Bu bizga erkin bog’langan ko’dni ishlab chiqishga imkon beruvchi dasturiy ta’minot design patterin(dizayn patterini)’i.
DI dasturiy ta’minot komponentalari o’rtasida qat’iy ulanishni kamaytirishning ajoyib uslubi.
DI shuningdek, bizning dasturiy ta’minotimizdagi kelajakdagi o’zgarishlar va boshqa o’zgarishlar va har xil murakkabliklarni yaxshiroq boshqarishga imkon beradi.
DI ning maqsadi ko’dni saqlab turishdir. Buni deyishimizga sabab Dependency Injection ni (DI) Container deb ham atashadi bu haqida pastroqda ko’proq duch kelamiz.


**Dependency Injection Container**

Dependency Injection Container ba’zan IoC Container deb ham ataladi, Chunki DI ning asl nomi IoC da. Bu DI bilan yordam beradigan [framework](https://henriquesd.medium.com/dependency-injection-and-service-lifetimes-in-net-core-ab9189349420).
U avtomatik ravishda biz uchun dependency(qaramlikni) yaratadi va inject(uko’l) qiladi.


**Inject(ukol) qilish nima degani o’zi?**

Inject qilish degan narsani biz tashqaridan qiymat berish yoki kiritish deb tushunishimiz mumkin.

Dependency Injection patterini obyektlarni ishga tushirish va obyektga kerakli bog’liqliklarni ta’minlash uchun builder object dan foydalanadi. Bu sizga Class dan tashqaridagi qaramlikni “Inject”(uko’l) qilish imkonini beradi.


**Service Lifetimes**

Biz hizmatlarni Container dan ro’yxatdan o’tkazganimizda, biz foydalanmoqchi bo’lgan umrni(lifetime) belgilashimiz kerak. 
Service lifetime Container tomonidan yaratilgan objectni qancha vaqt yashashini nazorat qiladi.
Xizmatni ro’yxatdan o’tkazishda IServiceCollection da tegishli kengaytma usuli yordamida yashash muddati(lifetime) yaratilishi mumkin.

Microsoft Dependency Injection Container bilan foydalanish mumkin bo’lgan uchta yashash muddati (hizmat muddati (lifetime)) mavjud, ular: 

•	***Transient*** – Xizmatlar har safar so’ralganda(request yuborilganda) yaratiladi. U har safar so’rov yuborilganda object ni yangilaydi va ushbu ob’ektning har bir so’rovi uchun. Har safar siz ushbu object ga so’rov yuborganizda u yangitdan misol(instance) yaratadi. [here](https://henriquesd.medium.com/dependency-injection-and-service-lifetimes-in-net-core-ab9189349420).

•	 ***Scoped*** – Xizmatlar har bir so’rov uchun yaratiladi( har bir so’rov uchun bir marta). Bu eng ko’p Web ilovalar uchun tavsiya etiladi. Masalan agar so’rov paytida siz bir xil Dependency Injectiondan foydalansangiz, ko’p joylarda siz ushbu ob’ektning bir xil namunasidan foydalanasiz va u bir xil xotira taqsimotini amalga oshiradi, ya’ni hotiradan yutadigonga o’xshayabmiz . [here](https://henriquesd.medium.com/dependency-injection-and-service-lifetimes-in-net-core-ab9189349420).

•	***Singleton*** – Xizmatlar ilovaning amal qilish davomida bir marta yaratiladi. U butun dastur uchun bir xil misoldan foydalanadi. [here](https://henriquesd.medium.com/dependency-injection-and-service-lifetimes-in-net-core-ab9189349420).


Bu uchta pattern qanday elon qilinadi?
```csharp
public void ConfigureServices(IServiceCollection services)
        {
            services.AddTransient<IMyDependencyA, MyDependencyA>();
            services.AddSingleton<IMyDependencyB, MyDependencyB>();
            services.AddScoped<IMyDependencyC, MyDependencyC>();
        }
```
Vanihoyat kod ham yozadigan bo’ldik endi bir kodlarini va bu uchovi pattern qanday ishlashi haqida ko’ramiz.

**Lets go to the code 😎.**

Dependency Injection va Service lifetimes amalda qanday ishlashini ko’rsatish uchun. Men uchta Class va ularning tegishli Interface lari ularni boshqaruvchi controller yaratdik. Ushbu Class larning har biri GUID yaratadi, va ilova sahifasida  har bir Service Classida GUID ni ko’rsatadi, shu tarzda har bir misol qachon yaratilganligini tasavvur qilishimiz mumkin. 

Bu **ExampleTransientService** classi: 
```csharp
using System;
using DependencyInjectionAndServiceLifetimes.Interfaces;
 
namespace DependencyInjectionAndServiceLifetimes.Services
{
    public class ExampleTransientService : IExampleTransientService
    {
        private readonly Guid Id;
 
        public ExampleTransientService()
        {
            Id = Guid.NewGuid();
        }
 
        public string GetGuid() => Id.ToString();
    }
}
```

Bu **ExampleScopedService** classi:
```csharp
using System;
using DependencyInjectionAndServiceLifetimes.Interfaces;
 
namespace DependencyInjectionAndServiceLifetimes.Services
{
    public class ExampleScopedService : IExampleScopedService
    {
        private readonly Guid Id;
 
        public ExampleScopedService()
        {
            Id = Guid.NewGuid();
        }
 
        public string GetGuid() => Id.ToString();
    }
}
```

Bu **ExampleSingletonService** classi:

```csharp
using System;
using DependencyInjectionAndServiceLifetimes.Interfaces;
 
namespace DependencyInjectionAndServiceLifetimes.Services
{
    public class ExampleSingletonService : IExampleSingletonService
    {
        private readonly Guid Id;
 
        public ExampleSingletonService()
        {
            Id = Guid.NewGuid();
        }
 
        public string GetGuid() => Id.ToString();
    }
}
```

**Startup Classida ushbu uchta Service uchun konfiguratsiya mavjud:**
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
 
    services.AddTransient<IExampleTransientService, ExampleTransientService>();
    services.AddScoped<IExampleScopedService, ExampleScopedService>();
    services.AddSingleton<IExampleSingletonService, ExampleSingletonService>();
 
    services.AddControllersWithViews();
}
```

HomeControllerda biz ushbu Service larni konstruktorda Dependency Injection orqali kiritmoqdamiz va index usulida har bir Service ga murojaat bor. Namoyish maqsadida va misolni qisqartirish uchun men xizmatlarning har biriga ikki marta kiritaman, shunda nima sodir bo’layotganini tasavvur qilish osonroq bo’ladi.

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Text;
using DependencyInjectionAndServiceLifetimes.Interfaces;
 
namespace DependencyInjectionAndServiceLifetimes.Controllers
{
    public class HomeController : Controller
    {
        private readonly IExampleTransientService _exampleTransientService1;
        private readonly IExampleTransientService _exampleTransientService2;
 
        private readonly IExampleScopedService _exampleScopedService1;
        private readonly IExampleScopedService _exampleScopedService2;
 
        private readonly IExampleSingletonService _exampleSingletonService1;
        private readonly IExampleSingletonService _exampleSingletonService2;
 
        public HomeController(IExampleTransientService exampleTransientService1,
            IExampleTransientService exampleTransientService2,
            IExampleScopedService exampleScopedService1,
            IExampleScopedService exampleScopedService2,
            IExampleSingletonService exampleSingletonService1,
            IExampleSingletonService exampleSingletonService2)
        {
            _exampleTransientService1 = exampleTransientService1;
            _exampleTransientService2 = exampleTransientService2;
 
            _exampleScopedService1 = exampleScopedService1;
            _exampleScopedService2 = exampleScopedService2;
 
            _exampleSingletonService1 = exampleSingletonService1;
            _exampleSingletonService2 = exampleSingletonService2;
        }
 
        public IActionResult Index()
        {
            var exampleTransientServiceGuid1 = _exampleTransientService1.GetGuid();
            var exampleTransientServiceGuid2 = _exampleTransientService2.GetGuid();
 
            var exampleScopedServiceGuid1 = _exampleScopedService1.GetGuid();
            var exampleScopedServiceGuid2 = _exampleScopedService2.GetGuid();
 
            var exampleSingletonServiceGuid1 = _exampleSingletonService1.GetGuid();
            var exampleSingletonServiceGuid2 = _exampleSingletonService2.GetGuid();
 
            StringBuilder messages = new StringBuilder();
            messages.Append($"Transient 1: {exampleTransientServiceGuid1}\n");
            messages.Append($"Transient 2: {exampleTransientServiceGuid2}\n\n");
 
            messages.Append($"Scoped 1: {exampleScopedServiceGuid1}\n");
            messages.Append($"Scoped 2: {exampleScopedServiceGuid2}\n\n");
 
            messages.Append($"Singleton 1: {exampleSingletonServiceGuid1}\n");
            messages.Append($"Singleton 2: {exampleSingletonServiceGuid2}");
 
            return Ok(messages.ToString());
        }
    }
}
```
Men har bir xizmat konstruktoriga to'xtash nuqtasini qo'shdim va dastur bajarilganda nima sodir bo'lishini tushuntiraman. Bu sahifadagi natija:
 

**Nima bo’ldi:**

•	Ikkita Transient objectiga request ikkita yuborilyabdi va natija ikki xil chiqyabdi. U ExampleTransientService Classiga ikki marta request yuboryabdi,  va u har bir request uchun alohida object olyabdi.

•	Ikki Scoped objecti esa bir xil qiymatga ega 🤔 nima uchun mmmm? Chunki u ExampleScopedService Class konstruktoriga faqat bir marta dush keladi chunki so’rov bir xil.

•	Ikki Singleton objecti bir xil qiymatga ega. U ExampleSingletonService Class ining konstructoriga faqat bir marta uchraydi va dastur tugaguncha shundan olingan objectni ishlatadi va boshqa object olmaydi 20 dan ortiq so’rov yuborilgan taqdirdaham.

**Xulosa**

Dependency Injection ko’dingizni tozalaydi(Clean Code qilib beradi). Saqlash osonroq va Test qilish ham ancha osonlashadi. Lifetime lar sizning dasturingizni performance(ilovangizni ishlashiga) kuchli ta’sir qilishi mumkin. Qisqacha aytganda Transient Service lar har safar so’ralganda yangi yangi object yaratiladi. Scoped esa har bir so’rov bo’yicha yaratiladi. Singleton da esa dastur ishga tushganda bir marta object olinadi, va anshu dastur o’chguniga qadar manashu objectdan foydalangan holda ishlaydi. Manashu olingan objectlar DI Containerning ichida saqlanadi shuni esdan chiqarmang. Umid qilamanki manashu misollar bilan lifetime lar orasidagi farq va u haqida tushunchalarni bilib oldingiz deb.

Xurmat bilan: Muhammad Abdulloh Komilov
