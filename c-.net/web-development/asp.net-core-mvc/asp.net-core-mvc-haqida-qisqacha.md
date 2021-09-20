---
description: Temur G'aniyev
---

# ASP.NET Core MVC haqida qisqacha.

**ASP.NET Core MVC** bu ASP.NET Core bilan ishlatish uchun optimallashtirilgan, yengil, ochiq kodli, yuqori testlash imkoniyatiga ega bo'lgan, ohirgi veb standartlarni qo'lab quvatlovchi ASP.NET frameworkning ko'rnishlaridan biri hisoblanadi. ASP.NET Core MVC loyihani 3 qismga **MODEL VIEW CONTROLLER** ajratish orqali clean code \(toza yoki optimal kod\) yozishga imkon beradi. 

**ASP.NET Core MVC** quydagilarni jamlagan.

* Routing
* Model binding
* Model validation
* Dependency injection
* Filters
* Areas
* Web APIs
* Testability
* Razor view engine
* Strongly typed views
* Tag Helpers
* View Components

## Routing
Routing loyihangizga kelgan so'rov urlni qayta ishlovchi mehanizm hisoblanib kelgan urlga mos kodni bajarilishni taminlaydi Boshqacha qilib aytsak **URL Maping** bilan shug'ulanadi. ASP.NET Core MVC da har bir routeni nomi bo'ladi. Dastlab default\(birinchi tanlangan yoki standart\) route ga yo'naltiriladi. Routing orqali loyihangiz tushunarli va qidirishga oson urllarga ega bo'ladi. **Routing Template Syntax** yordamida o'zingizga qulay ko'rnishdagi standart yoki ixtiyoriy qiymatlarga ega bo'lgan routing shablonini yasashingiz mumkin.
```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
});
```
Model binding

editing...