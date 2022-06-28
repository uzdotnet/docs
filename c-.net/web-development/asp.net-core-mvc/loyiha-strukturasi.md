---
description: Temur G'aniyev, Ravshan Sodiqov
---

# Loyiha struktruasi

ASP.NET Core .NET ning dinamik veb saytlarni qurishda mo’ljallangan frameworki hisoblansa, ASP.NET Core MVC esa mana shu dinamik veb saytlarning arxitekturasi hisoblanadi. Ushbu MVC arxitekturasi veb saytni asosiy uch qismga ajratgan holda qurish imkonini beradi:

*	 Models
*	 Views
*	 Controllers

Loyiha yaratish uchun dastlab D: diskda **dotnetuz** nomli papka yaratamiz so\'ng va bu papkani vs code dasturi orqali kiramiz. MVC turidagi loyiha yaratish uchun terminalga kirib \( ctrl + ` \) ushbu kommandalarni kiritamiz:

**dotnet new mvc**

![](../../../.gitbook/assets/dotnet_new_mvc.png)

Natijada ushbu loyiha shabloni dotnet tomonidan yaratilib beriladi.

{% hint style="info" %}
Umuman olganda, loyihani ikki xil yo'l bilan yaratish mumkin:

  **dotnet new mvc** - da loyiha joylashgan papka nomi bilan ataladi;
  
  **dotnet new mvc -o <loyiha_nomi>** - da papka ichida boshqa nom ostida loyiha yaratish mumkin.
{% endhint %}

Loyihamiz quyidagi papkalardan tashkil topadi:

![](../../../.gitbook/assets/structure_of_mvc.png)

* /Controllers papkasi- Controller sinfdan voris olgan barcha controllerlarni saqlaydi.
* /Models papkasi- C# sinflaridan iborat bo\'lgan modellarni o'zida saqlaydi.
* /Properties papkasi- MVC loyihaning asosiy xususiyatlari va IIS,Kestrel sozlamalaridan iborat bo'ladi.
* /Views papkasi- Viewlarni o'zida saqlaydi.
* /wwwroot papkasi- statik fayllarni yani css,js va kutubxonalar jquery,bootstrap... 
* appsettings.json- barcha muhitlar uchun dastlabki sozlarmalar joylashadiga fayl.
* appsettings.{Muhit_nomi}.json- faqat {Muhit_nomi} da ko\'rsatilgan muhit uchun sozlamalar.
* {loyiha_nomi}.csproj- Loyihaning asosiy sozlamalar fayli.
* Program.cs- Dastlabki ishga tushuvchi fayl.
* Startup.cs- MVC loyihaning service larni, middleware larni va asosiy sozlamalarni o'zida jamlovchi Program.cs fayl tomonidan chaqiriluvchi fayli.



{% hint style="info" %}
DIQQAT !  .NET 5 muhitida yaratiladigan ASP.NET Core MVC loyihalarida loyiha uchun talab qilinadigan xizmatlar sozlamalari Startup.cs faylida, dasturni ishga tushirish kodi esa Program.cs faylida saqlanardi. .NET 6 da esa ushbu ikki fayl yagona Program.cs faylida saqlanadi.
{% endhint %}
