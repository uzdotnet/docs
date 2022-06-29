---
description: Ravshan Sodiqov
---

# View

**Views**  Frontend dasturchilar tomonidan ishlab chiqiladigan veb sahifalar uchun foydalanuvchi interfeyslari, ya’ni ma`lumotlarni foydalanuvchilar uchun qulay dizayn asosida taqdim etadi. ASP.NET Core frameworkida ko’rinishlar asosan Razor sahifalar sifatida tasvirlanadi. Razor sahifalar - HTML sahifalarning C#, F# va VBA dasturlash tillariga mansub kodlar bilan integrallashgan shaklidir (.cshtml kengaytma ostida). Ushbu Razor sahifalarni HTML shabloniga ega dinamik veb sahifalar deb ham atash mumkin. 

ASP.NET Core MVC asosida quriladigan loyihalarning veb sahifalari «Views» papkasida saqlanadi. Namunaviy holda taqdim etiladigan «Views» papkasi quyidagicha tuzilishga ega bo’ladi:
*	«Home» papkasi
*	«Shared» papkasi
*	_ViewImports.cshtml fayli
*	_ViewStart.cshtml fayli

### «Home» papkasi
Ushbu papka shu nom bilan ataluvchi, ya’ni HomeController boshqaruvidagi sahifalarni o’zida saqlovchi papkadir. Agar HomeControllerda quyidagicha metodlar aniqlangan bo’lsa:
```csharp
public IActionResult Index()
    {
        return View();
    }

    public IActionResult Privacy()
    {
        return View();
    }
````
Demak «Home» papkasida ham Index.cshtml va Privacy.cshtml fayllari mavjud bo’ladi. Yuqorida controller da aniqlangan metodlar «Home» papkasida saqlanadigan ko’rinishlarni  brauzerda  tasvirlash uchun xizmat qiladi. Bordi-yu, «Home» papkasiga Contact.cshtml sahifasini qo’shsak-u, HomeControllerda 
```csharp
public  IActionResult  Contact()
{
	return View();
}
```
metodini yozmasak, ushbu ko’rinish brauzerda tasvirlanmaydi.

{% hint style="info" %}
Shuni yodda tuting !
1. Controller boshqaruvidagi barcha sahifalar «Views» papkasida ichida joylashgan, Controller nomi bilan bir xil bo’lgan papkada saqlanadi. Agar-da loyihamizning «Controllers» papkasiga AdminController ni qo’shsak, ushbu controller boshqaradigan sahifalar «Views» papkasi ichidagi «Admin» papkasida saqlanadi.
2. Har bir ko’rinishni brauzerda aks ettirish uchun controller ichida ko’rinish nomi bilan bir xil metod aniqlanishi kerak. Aks holda ko’rinish brauzerda aks ettirilmaydi.
{% endhint %}

### «Shared» papkasi
Ushbu papka quyidagicha fayllarga ega:
*	_Layout.cshtml
*	_Layout.cshtml.css
*	_ValidationScripts.cshtml
*	Error.cshtml

Ma’lumki barcha HTML shabloniga ega sahifalar bir xil ko’rinishda tasvirlanadi: `<!DOCTYPE html> …`  va ko’pgina holatda barcha sahifalarning **header** va **footer** qismlarning dizayni ham bir xil ko’rinish kasb etadi. Biz esa loyihamizda foydalaniladigan view lardagi ushbu doim takrorlanuvchi kodlardan xalos bo’lish uchun, takrorlanuvchi kodlarni  **`_Layout.cshtml`** faylida saqlaymiz.


### `_ViewImports.cshtml` fayli

Dinamik view lar controller tomonidan yuborilgan ma’lumotlarni o’zida saqlaydi va bu ma’lumotlar odatda C# sinflari ko’rinishida bo’lishi mumkin. `_ViewImports.cshtml` fayli esa mana shu C# sinflarning nomlar fazo (namespace) larini o’zida saqlaydi. Odatiy holda ushbu fayl quyidagicha ko’rinishga ega bo’ladi:
```csharp
@using <Loyiha_nomi>
@using <Loyiha_nomi>.Models
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
```

## `_ViewStart.cshtml` fayli
Faylning nomidan ham anglab olish mumkin-ki, ushbu fayl ko’rinish qismida ilk ishga tushadigan kodni o’zida saqlaydi:
```csharp
@{
    Layout = "_Layout";
}
```
Yuqoridagi kod har bir sahifa uchun HTML shablonini hosil qiluvchi `_Layout.cshtml` faylini ishga tushirishni ta’minlaydi. Shu o’rinda savol tug’ilishi mumkin. Nega endi birdaniga  `_Layout.cshtml` faylini ishga tushirmaslik kerak ?

Sababi, barcha sahifalar `<!DOCTYPE html> …` kabi kod bilan boshlanishi mumkin, ammo ularning header va footer qismlarning tuzilishi va dizayni farq qilish ehtimoli ham yo’q emas. Shu sababdan avval qaysi layout viewni ishga tushirishni aniqlab, so’ng fayl ishga tushiriladi.
