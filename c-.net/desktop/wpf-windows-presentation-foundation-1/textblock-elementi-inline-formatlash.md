---
description: Sobirjonov O'tkirbek
---

# TextBlock elementi – Inline formatlash

TextBlock elementi bilan ishlashni avvalgi darsda o’rganib chiqdik, ushbu darsda esa Inline formatlash va Textblock elementiga qo’llanilishini o’rganamiz.

Siz [wikipedia ](https://www.wikipedia.org/)yoki shunga o’xshash saytlardan foydalangan bo’lsangiz unda ba’zi so’zlarni rangi boshqa rangda ajratib ko’rsatilgan, yoki yozuvga tag chizig’ qo’yilgan, yoki Giperhavolalar qo’yilgan holatlarga ko’p ko’zingiz tushgani aniq. Huddi shundek yozuvlar formatlarini Textblock elementida qo’llanilishini ko’rib chiqamiz.

```aspnet
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        xmlns:sys="clr-namespace:System;assembly=mscorlib"
        Title="MainWindow" Height="150" Width="300">
    <Grid>
        <TextBlock Margin="10" TextWrapping="Wrap">
             TextBlock with <Bold>bold</Bold>, 
             <Italic>italic</Italic> and 
             <Underline>underlined</Underline> text.
        </TextBlock>
    </Grid>
</Window>

```

![](../../../.gitbook/assets/image%20%2894%29.png)

Ko’rib turganingizdek

**&lt;Bold&gt; &lt;/Bold&gt;**  teglari orasida yozilgan so’zlar qalin holatga o’tadi.                                                                           **&lt;Italic&gt; &lt;/Italic&gt;**  teglari orasida yozilgan so’zlar yotiqroq va qo’l yozmaga o’xshaganroq yozuvga  o’tadi.**&lt;Underline&gt; &lt;/Underline&gt;**  teglari orasida yozilgan so’zlar tag chiziqqa ega bo’ladi. Xuddi HTML kabi, siz qanday matn olishni hohlasangiz, matn yorlig'i bilan o'rab olasiz va hokazo.  Bu sizning ilovalaringizda turli xil matnlarni yaratishni va ko'rsatishni juda osonlashtiradi.

Ushbu uchta teg ham Span elementining oddiy sinflari bo'lib, ularning har biri kerakli effekt yaratish uchun Span elementida o'ziga xos xususiyatni o'rnatadi. Masalan, Bold yorlig'i faqat asosiy Span elementida FontWeight xususiyatini o'rnatadi, Italic elementi FontStyle-ni o'rnatadi va hokazo.

Ya’ngi satrga o’tish uchun esa  **&lt;LineBreak/&gt;**  tegidan foydalaniladi. Siz dasturlash bilan avval shug’ullangan bo’lsangiz **‘\n’** bilan ko’p ishlagan bo’lishingiz kerak. LineBreak ham huddi shunga o’xshaydi.

### Giperhavolalar

Matn bilan ishlash davomida siz giperhavolalar bilan ishlashingiz ham mumkin.Misol uchun:

```aspnet
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        xmlns:sys="clr-namespace:System;assembly=mscorlib"
        Title="MainWindow" Height="150" Width="300">
    <Grid>
        <TextBlock Margin="10" TextWrapping="Wrap">
			        This text has a 
			        <Hyperlink 
			            RequestNavigate="Hyperlink_RequestNavigate" 
			            NavigateUri="https://www.google.com">link
			        </Hyperlink> in it.
        </TextBlock>
    </Grid>
</Window>

```

Va C\# faylida ushbu havola bosilganda nima bo’lishini yozib ketishimiz kerak bo’ladi.

```csharp
using System.Windows;
using System.Windows.Navigation;

namespace WpfApp1
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Hyperlink_RequestNavigate(object sender, RequestNavigateEventArgs e)
        {
            System.Diagnostics.Process.Start(e.Uri.AbsoluteUri);
        }
    }
}

```

Natija esa :

![](../../../.gitbook/assets/image%20%2889%29.png)

Ushbu link giperhavolasi bosilganda, kompyuteringizga o’rnatilgan asosiy brauzer siz kiritgan manzilga olib boradi.

