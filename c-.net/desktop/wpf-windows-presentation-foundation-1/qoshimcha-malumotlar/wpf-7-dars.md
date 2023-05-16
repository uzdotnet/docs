---
description: CSharp N1 Jamoasi
---

# App.xaml

App.xaml ilovangizni boshlang'ich nuqtasi hisoblanadi. Visual Studio yangi loyiha boshlayotganingizda siz uchun bu faylni va unga bog'langan App.xaml.cs faylini avtomatik ravishda yasab beradi. Bu ikki fayl dastur oynasini hosil qilish uchun birgalikda ishlaydi, shuning uchun ham tiplari **partial** sifatida e'lon qilingan!

```csharp
public partial class App : Application
{
  
}
```

App.xaml.cs WPF Windows dasturining markaziy klassi bo'lib **Application** sinfini vorisi .NET buyrug'larni boshlash uchun ushbu sinfga o'tadi va kerakli oynani yoki sahifa o'sha joydan yuklanadi. Shuningdek, Dasturni ishga tushrishda, Ilovaning tashkil qiluvchi elementlar uchun xususiyatlar e'lon qilishmiz mumkin . Keyinchalik bu haqida ko'proq ma'lumot beramiz.\
App.xaml faylining eng ko'p ishlatiladigan xususiyatlaridan biri bu ishlatilishi va ishlatilishi mumkin bo'lgan global resurslarni e'lon qilish. Global resurslarni butun Ilovaning barcha elementlarni, har xil xususiyatlarni boshqarishingiz mumkin bo'ladi. Albatta global resurslar haqida ham batafsil to'xtalamiz.

## App.xaml tuzilishi

Yangi dastur yaratishda avtomatik ravishda yaratilgan App.xaml quyidagi ko'rinishga ega bo'ladi:

```markup
<Application x:Class="WpfTutorialSamples.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
{ Ushbu maydonda elementlar uchun xususyatlar yozladi.}

    </Application.Resources>
</Application>
```

Bu yerda e'tiborga olish kerak bo'lgan asosiy narsa **StartupUri** xususiyati. Bu aslida dastur ishga tushirilganda qaysi Oyna yoki Sahifani ishga tushirishni ko'rsatadigan qismdir. Bunday holda, **MainWindow.xaml** ishga tushiriladi, ammo boshlang'ich nuqtasi sifatida boshqa oynadan foydalanmoqchi bo'lsangiz, uni o'zgartirishingiz mumkin.\
Ba'zi hollarda, birinchi oyna qanday va qachon ko'rsatilishini ko'proq nazorat qilishni xohlaysiz. Bunday holda, siz **StartupUri** xususiyatini va qiymatini o'chirib tashlashingiz va buning o'rniga hammasini **Code-Backend**-dan qilishingiz mumkin.\


App.xaml.cs odatda yangi loyiha uchun shunday bo'ladi:

```csharp
using System;
using System.Collections.Generic;
using System.Windows;

namespace WpfTutorialSamples
{
 public partial class App : Application
 {

 }
}
```

Siz ushbu dastur sinfini qanday maqsadda foydalanasiz , Masalan, siz boshlang'ich oynangizni o'zingiz yaratishni hoxlasangiz Startup oynasiga ulanishni amalga oshrishingiz kerak. Bu qanday qilnadi?

```markup
<Application x:Class="WpfTutorialSamples.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             Startup="Application_Startup">
    <Application.Resources></Application.Resources>
</Application>
```



**XAML** da **StartupUri** o'rniga **Startup** orqali yangi oyna qanday qilib bog'lanishga e'tibor bering Code-Backend da siz quyidagi hodisadan foydalanishingiz mumkin:

```csharp
using System;

using System.Collections.Generic;

using System.Windows;



namespace WpfTutorialSamples
{
 public partial class App : Application
 {
  private void Application_Startup(object sender, StartupEventArgs e)
  {
   // Yangi StartUp oynasini yaratib olamiz
   MainWindow wnd = new MainWindow();
   // Yangi oynamizga biron saloha beramiz;
   wnd.Title = "Salom Uzbekiston";
   // Oynani e'lon qilamiz
   wnd.Show();
  }
 }
}
```

Faqatgina StartupUri xususiyatidan foydalanish bilan taqqoslaganda, ushbu misolning eng yaxshi tomoni shundaki, biz uni ishga tushirishdan oldin ishga tushirish oynasini boshqarishimiz kerak. Bunda biz uning nomini o'zgartiramiz, bu unchalik foydali emas, lekin siz ekranning ochilishini ko'rsatishingiz mumkin. Sizda barcha nazorat mavjud bo'ldi va ko'p imkoniyatlar mavjud. Ushbu Kanalimizni keyingi maqolalarida ularning bir nechtasini chuqurroq ko'rib chiqamiz!
