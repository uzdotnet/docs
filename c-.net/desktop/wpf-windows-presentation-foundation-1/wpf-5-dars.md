---
description: CSharp N1 jamoasi
---

# Hodisalar

WPF dasturi zamonaviy interfeyslarning ramkalari hodisalarga asoslangan . Barcha boshqaruv elementlari, shu jumladan Window \(u ham Control sinfini meros qilib oladi\).

Ko'pgina boshqaruv elementlarida siz KeyDown, KeyUp, MouseDown, MouseEnter, MouseLeave, MouseUp va boshqa bir qator hodisalarni topasiz.

WPF-da hodisalar qanday ishlashini batafsil ko'rib chiqamiz, chunki bu juda murakkab mavzu, ammo hozircha siz XAML-dagi boshqarish hodisasini kod ortidagi faylingizdagi kod qismiga qanday bog'lashni bilishingiz kerak. Ushbu misolni ko'rib chiqing:

```markup
<Window x:Class="WpfTutorialSamples.XAML.EventsSample"

        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"

        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"

        Title="EventsSample" Height="300" Width="300">

 <Grid Name="pnlMainGrid" MouseUp="pnlMainGrid_MouseUp" Background="LightBlue">        

    </Grid>

</Window>
```

Metod nomini yozish orqali Gridning MouseUp hodisasiga qanday bog'langanimizga e'tibor bering. Ushbu usul hodisa ko'rinishlaridan foydalangan holda kod orqasida aniqlanishi kerak. Bunday holda u quyidagicha ko'rinishi kerak:

```csharp
private void pnlMainGrid_MouseUp(object sender, MouseButtonEventArgs e)

{

 MessageBox.Show("You clicked me at " + e.GetPosition(this).ToString());

}
```

MouseUp qo'llanilganda siz bog'langan bo'lgan **MouseButtonEventHandler** deb nomlangan **delegatdan** foydalaniladi. U ikkita parametrga ega: jo'natuvchi \(hodisani ko'targan boshqaruv\) va foydali ma'lumotlarni o'z ichiga olgan MouseButtonEventArgs ob'ekti. Sichqoncha kursori o'rnini olish va bu haqda foydalanuvchiga aytib berish uchun biz uni misolda ishlatamiz.

Bir nechta hodisalar bir xil delegate turidan foydalanishi mumkin - masalan, ikkala MouseUp va MouseDown **MouseButtonEventHandler** delegatedan, MouseMove hodisasi esa **MouseEventHandler** delegatedan foydalanadi. Hodisalarni qayta ishlash usulini belgilashda siz qaysi delegateni ishlatishini bilishingiz kerak va agar buni bilmasangiz, uni hujjatlarda qidirib topishingiz mumkin.

**&lt;New Event Handler&gt;** -ni tanlaganingizda Visual Studio sizning kodingiz orqasidagi faylda tegishli hodisa ishlovchilarini yaratadi. U &lt;control name&gt; \_ &lt;event name&gt; deb nomlanadi, bizning **holimizda esa pnlMainGrid\_MouseDown**  deb nomlanadi. Hodisalar nomini sichqonchaning o'ng tugmachasini bosing va hodisani qayta **ishlashga o'tish** -ni tanlang va VS sizni unga olib boradi.

## Code-behind-dan hodisaga bog'lanish

Hodisalarga bog'lanishning eng keng tarqalgan usuli yuqorida bayon qilingan, ammo siz hodisaga to'g'ridan-to'g'ri Code-behind orqali bog'lanishni istagan paytlar bo'lishi mumkin. Bu + = C \# sintaksisidan foydalangan holda amalga oshiriladi, bu erda hodisa ishlovchisini to'g'ridan-to'g'ri ob'ektga qo'shasiz. Buning to'liq izohi maxsus C \# misolida keltirilgan :

```csharp
using System;

using System.Windows;

using System.Windows.Input;

namespace WpfTutorialSamples.XAML

{

 public partial class EventsSample : Window

 {

  public EventsSample()

  {

   InitializeComponent();

   pnlMainGrid.MouseUp += new MouseButtonEventHandler(pnlMainGrid_MouseUp);

  }

  private void pnlMainGrid_MouseUp(object sender, MouseButtonEventArgs e)

  {

   MessageBox.Show("You clicked me at " + e.GetPosition(this).ToString());

  }

 }

}
```

Yana bir marta qaysi delegatdan foydalanilishini bilishingiz kerak va bu borada Visual Studio sizga yana bir bor yordam berishi mumkin.

pnlMainGrid.MouseDown + = Visual Studio o'z yordamini taklif qiladi:

![Amalga oshirishga tayyor bo&apos;lgan amaldagi usul ostida Visual Studio siz uchun to&apos;g&apos;ri hodisa ishlovchisini yaratishi uchun \[Tab\] tugmachasini ikki marta bosing.](../../../.gitbook/assets/wpf5.png)

