---
description: Muhammad Xodjayev
---

# Middleware tushunchasi

Middleware — bu [ASP.NET](http://ASP.NET) Core’dagi fundamental va ajralmas qismlardan biri hisoblanadi. U HTTP Request’lar va response’lar ustida amal bajarishimizga yordam beradi. Bugun ushbu maqolada biz middleware haqidagi tushunchalarni, uni qo’llashni ko’rib chiqamiz, kettik 🚀.

----------

## Middleware o’zi nima

Middleware — bu [ASP.NET](http://ASP.NET) Core pipeline’ida HTTP request’lar va response’lar ustida amal bajarishimiz uchun bizga yordam beradigan dasturning tarkibiy qismi. Har bir middleware ushbu ishlarni amalga oshira oladi:

-   Middleware biror-bir middleware’dan oldinham keyinham ish qila oladi.
-   Request yoki Response’ni o’zgartira oladi.
-   Pipeline’dan short-circuit (ya’ni chiqib ketish) qila oladi va response’ni _сразу_ yubora oladi.

> Middleware — program.cs’da pipeline’ga qanday ketma-ketlika qo’yilgan/qo’shilgan bo’lsa, usha ketma-ketlikda ishlaydi.

----------

## Middleware qanday ishlaydi

Yuqorida ikki martta ta’kidlaganimizdek, middleware bizga HTTP request yoki response’lar ustida ishlashimizni ta’minlaydi. Middleware’ni ishlatishga — 3 ta asosiy metodlar bor:

-   `Use` : Pipeline’ga middleware qo’shadi.
-   `Run` : Terminal middleware qo’shadi, ya’ni pipeline’ni to’xtatuvchi/hal qiluvchi middleware.
-   `Map` : Request’dan kelib chiqib (ya’ni conditional), pipeline’da yangi branch ochadi (Map’ham terminal middleware hisoblanadi).

Ushbu metodlar yordamida middleware yozsak biz anonim metodlar orqali yozamiz ya’ni bu — in-line middleware hisoblanadi. Yoki umuman bu metodlarni ishlatmasdan, reusable (ya’ni alohida class) class’da yozib uni pipeline’ga qo’shib qo’ysakham bo’laveradi.

----------

## Qanday ishlatamiz o’zi

![Order-of-middleware](../../../.gitbook/assets/order-of-middleware.png)

Ushbu rasmda middleware’lar o’zi qanday ishlashi haqida batafsil yoritilgan. E’tibor bering, qora strelka kelib birinchi middleware’ga uriladi, u yerda qandaydur ish bajariladi so’ng `next()` chaqiriladi. Keyin ikkinchi middleware’ga o’tib ketadi, keyin uchinchiga.

**Diqqat! 3 chi ya’ni terminal middleware’dan ortga qaytib ketyapti, bu degani birinchi bo’lib 1-2-3 va oxiriga 3-2-1 ya’ni response qaytarish uchun yana oldingi middleware’larga yo’lda kiradi degani, agarda u yerdaham `next()` dan keyin** qandaydur `logic` yozgan bo’lsangiz ularham ishga tushadi. Misolda ko’ramiz:

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Use(async (context, next) =>
{
    Console.WriteLine("1 chi Use middleware'da birinchi amal");
    await next.Invoke();
    Console.WriteLine("1 chi Use middleware'da ikkinchi amal");
});

app.Use(async (context, next) =>
{
    Console.WriteLine("2 chi Use middleware'da birinchi amal");
    await next.Invoke();
    Console.WriteLine("2 chi Use middleware'da ikkinchi amal");
});

app.Run(async context =>
{
		Console.WriteLine("-----");
    await context.Response.WriteAsync("3 chi middleware (terminal middleware)'dan salom");
});

app.Run();

```

Hozir bu kodda birinchi bo’lib birinchi `Use` middleware ishlaydi, so’ng `await next.Invoke()` bilan keyingi middleware’ni chaqiradi, keyin 2 chi middleware ishlaydi, so’ng 3 chi — `Run` ishlaydi. Tepada aytganimdek, pipeline ortga qaytib ketadi, yo’lda `Use` middleware’larga kiradi. U yerda `await next.Invoke()` dan keyin ham kod yozilgan, ular tabiiyki ishga tushadi. Xullas output quyidagicha:

```bash
1 chi Use middleware'da birinchi amal
2 chi Use middleware'da birinchi amal
-----
2 chi Use middleware'da ikkinchi amal
1 chi Use middleware'da ikkinchi amal

```

3 chi middleware’dan salom esa, u Respone bo’lganligi uchun website’da ko’rinadi.

----------

## Run Middleware

`Run` middleware’i `Use` kabi o’ziga `next` ni qabul qilmaydi va bu degani `Run` metodi ichida biz keyingi middleware’ni chaqira olmaymiz. Bu esa `Run` so’nggi ya’ni short-circuting middleware hisoblanadi.

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Use(async (context, next) =>
{
    Console.WriteLine("1 chi Use middleware'da birinchi amal");
    await next.Invoke();
    Console.WriteLine("1 chi Use middleware'da ikkinchi amal");
});

app.Run(async context =>
{
		Console.WriteLine("-----");
    await context.Response.WriteAsync("3 chi middleware (terminal middleware)'dan salom");
});

app.Use(async (context, next) => // ushbu middleware hech qachon ishga tushmaydi.
{
    Console.WriteLine("2 chi Use middleware'da birinchi amal");
    await next.Invoke();
    Console.WriteLine("2 chi Use middleware'da ikkinchi amal");
});

app.Run();

```

Ushbu kodda ikkinchi `Use` middleware’i hech qachon ishga tushmaydi, chunki `Run` ichida `next` yo’q. Output quyidagicha bo’ladi:

```bash
1 chi Use middleware'da birinchi amal
-----
1 chi Use middleware'da ikkinchi amal

```

----------

## Diqqat!

O’zi aslida [ASP.NET](http://ASP.NET) Core’da middleware’lar biz uchun yozib qo’yilgan. Hozir ko’rib chiqayotgan `Use`, `Run`, va `Map`lar qo’shimcha middleware qo’shishimizni ta’minlaydi.

![Order-of-middleware2](../../../.gitbook/assets/order-of-middleware2.png)

Bu rasmdagilar o’zi bor middleware’lar. Biz ushbu metodlar bilan Custom Middleware yozamiz. Ammo bizda o’zi bor middleware’lar ustida to’liq nazorat bor (ya’ni biz ularni orasiga o’zimizni middleware’imizni qo’shsak bo’ladi).

----------

Middleware’lar ketma-ketligi `Program.cs`da joylashgan bo’ladi. Ularni ketma-ketligi judayam muhim chunki bu xavfsizlikka, dastur ishlashiga to’g’ridan to’g’ri ta’sir o’tkazadi.

----------

## Map Middleware

`Map` metodi orqali biz pipeline’nni alohida branch (ya’ni shox)ga o’tkaza olamiz. Ya’ni Map ishlatilinayotganda biz PATH beramiz va agarda REQUEST PATH bilan bir-xil bo’lib qolsa, usha branch’ga kirib ketadi va ushbu middleware terminal (ya’ni hal qiluvchi/so’nggisi) bo’ladi.

Masalan:

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Map("/map1", HandleMapTest1);

app.Map("/map2", HandleMapTest2);

app.Run(async context =>
{
    await context.Response.WriteAsync("Map ishlamagan dasturdan salom");
});

app.Run();

static void HandleMapTest1(IApplicationBuilder app)
{
    app.Run(async context =>
    {
        await context.Response.WriteAsync("Map Test 1");
    });
}

static void HandleMapTest2(IApplicationBuilder app)
{
    app.Run(async context =>
    {
        await context.Response.WriteAsync("Map Test 2");
    });
}

```

Quyidagi jadvalda [http://localhost:5000](http://localhost:5000)’ga yuborilgan REQUEST va RESPONSE’larni ko’rishingiz mumkin:

|   	Request   	   |		Response	   |
| ------------ |-------------- |
|		[http://localhost:5000](http://localhost:5000)	   |  Map ishlamagan dasturdan salom             |
|		[http://localhost:5000/map1](http://localhost:5000/map1)	   |   Map Test 1            |
|         [http://localhost:5000/map2](http://localhost:5000/map2)     | Map Test 2              |
|		[http://localhost:5000/map3](http://localhost:5000/map3)				|Map ishlamagan dasturdan salom

----------

### Ichma-ich `Map`

Map metodi shuningdek ichma-ich `map`ni qo’llab-quvvatlaydi:

```csharp
app.Map("/level1", level1App => {
    level1App.Map("/level2a", level2AApp => {
        // "/level1/level2a" ishga tushyapti
    });
    level1App.Map("/level2b", level2BApp => {
        // "/level1/level2b" ishga tushyapti
    });
});
```

----------

### MapWhen

Va `MapWhen` bor. Bu nafaqat PATH’ni tekshiradi, balki uning so’rovini ham tekshira oladi. `Func<HttpContext, bool>` ushbu predicate’dan qaytgan qiymat (`true` yoki `false`)ga qarab turib yangi branch’ga olib kirib ketadi yoki yo’q. Ushbu misolda query string’ni tekshirib (ya’ni request’da kelgan so’rov)ni tekshirib beradi:

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapWhen(context => context.Request.Query.ContainsKey("Muhammad"), HandleBranch);

app.Run(async context =>
{
    await context.Response.WriteAsync("Map ishlamagan dasturdan salom.");
});

app.Run();

static void HandleBranch(IApplicationBuilder app)
{
    app.Run(async context =>
    {
        var branchVer = context.Request.Query["Muhammad"];
        await context.Response.WriteAsync($"Ishlatilingan branch = {branchVer}");
    });
}

```

Quyidagi jadvalda [http://localhost:5000](http://localhost:5000)’ga yuborilgan REQUEST va RESPONSE’larni ko’rishingiz mumkin:

|   	Request   	   |		Response	   |
| ------------ |-------------- |
|		[http://localhost:5000](http://localhost:5000)	   |  Map ishlamagan dasturdan salom             
|         [http://localhost:5000/?muhammad=main](http://localhost:5000/?muhammad=main)     | Ishlatilingan branch = main             |

----------
## Built-in middleware’lar

[https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-9.0#built-in-middleware](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-9.0#built-in-middleware) → ushbu link orqali [ASP.NET](http://ASP.NET) Core’da biz middleware yozmasak ham, shundoq ham mavjud bo’lgan middleware’lar to’plami mavjud. Kirib o’qib chiqishni maslahat beraman.

----------

Xurmat bilan,

Muhammad Xodjayev
