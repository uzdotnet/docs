---
description: Ravshan Sodiqov
---
# View larni aniqlash yo'llari

Ma’lumki, ASP.NET Core MVC strukturasida Viewlar «Views» papkasida saqlanadi va ushbu viewlarni brauzerda aks ettirish uchun Controllerda ularning nomiga mos metod aniqlab qo’yiladi.  Masalan,  
Views → Home → Index.cshtml manzilida joylashgan ko’rinishni brauzerda ko’rsatish uchun HomeControllerda quyidagicha metodni yozamiz:
```csharp
	 public IActionResult Index()
    {
        return View();
    }
```
Dastur ishlash jarayonida yuqoridagi action metod Views → Home manzilidagi metod nomi bilan bir xil ko’rinishni ekranga chiqaradi.
 
## Agar metod nomi View nomi bilan bir xil bo’lmay qolsachi ?

Endi ushbu holatda metodga aynan qaysi View ni qaytarmoqchi ekanligini ko’rsatib o’tishimiz kerak bo’ladi:
```csharp
public IActionResult One()
    {
        return View("Index");
    }
```

Yuqoridagi holatda **One()** metodi ishlashi natijasida **Index View** brauzerda namoyon bo’ladi. 

## Controller dagi metod orqali boshqa Controllerning metodiga murojaat qilish

Faraz qilaylik, loyihamizning «Controllers» papkasida ikkita **HomeController** va **OtherController** lari mavjud bo’lsin va tabiiyki «Views» papkasida ham «**Home**» papkasi va «**Other**» papkalarini yaratamiz. Ularga mos ravishda **Index.cshtml** va **Contact.cshtml** razor view larini ham qo’shib qo’yamiz. Endigi navbat ushbu view larni brauzerda ko’rsatish uchun ularga mos controllerlarda ularni ishga tushuruvchi metodlarni aniqlaymiz:
```csharp
//HomeController da
    public IActionResult Index()
    {
        return View();
    }

//OtherController da
    public IActionResult Contact()
    {
        return View();
}
```

 Agar biz HomeControllerdagi **Index()** metodida OtherControllerdagi Contact View ni ishlatmoqchi bo’lsak, quyidagicha argument kiritishimiz kifoya: 
```csharp
//HomeController da
    public IActionResult Index()
    {
        return View("../Other/Contact");
    }
```
yoki teskari holat uchun, ya’ni OtherControllerdagi **Contact()** metodida HomeControllerdagi Index View ni ishlatish quyidagicha:
```csharp
//OtherController da
    public IActionResult Contact()
    {
        return View("../Home/Index");
    }
```
