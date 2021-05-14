---
description: Sobirjonov O'tkirbek
---

# Son va Vaqtni Formatlash

Siz ko’p xollarda sonlarni quidagi ko’rinishlarda ko’rgansiz:

* RUSSIA 123 345 456 122.89
* USA 123,145,456,122.89
* Germany 123.145.456.122,89

Bunday ko’rinishlar ko’p davlatlarda farqli bo’ladi.  Siz agar dasturingizda bularni davlatga mos xolda chiqarishni xoxlashingiz mumkin. Va vaqtlarni ham shunga mos qilsangiz bo’ladi.

* RUSSIA           14.02.2020 23:30
* USA                  2/14/2020 11:30 PM
* Germany         14.02.2020 23:30

Bu xolda formatlash aslida ko’p ish bo’lishi mumkin, ammo .NET bizga tayyor classlarni taklif qiladi. Bunda bizga _CultureInfo_ classi kerak bo’ladi.

Avvalo **System.Globalization** Kutubxonasini chaqirib qo’yishimiz kerak bo’ladi.1- WPF da ko’rinishni kiritib olishimiz kerak.

```aspnet
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="400">
    <StackPanel TextElement.FontSize="20" Margin="20">
        <DockPanel>
            <TextBlock>Sonlar : </TextBlock>
            <TextBlock x:Name="sonlar" Margin="50 0 0 0" Text="123145456122.89"/>
        </DockPanel>
        <DockPanel Margin="0 20 0 0">
            <TextBlock>Sonlar :</TextBlock>
            <TextBlock x:Name="vaqt" Margin="50 0 0 0" Text="2-14-2020 11:28"/>
        </DockPanel>
        <Button Margin="0 20 0 0" Tag="en" Content="USA" Click="Button_Click"/>
        <Button Margin="0 20 0 0" Tag="ru" Content="Russia" Click="Button_Click"/>
        <Button Margin="0 20 0 0" Tag="de" Content="Germany" Click="Button_Click"/>
    </StackPanel>
</Window>

```

Endi esa Tugma bosilish xodisasiga formatlarni o’zgarishini qo’llab qo’yamiz.

```csharp
using System;
using System.Globalization;
using System.Threading;
using System.Windows;
using System.Windows.Controls;

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
        private void Button_Click(object sender, RoutedEventArgs e)
        {
            double son = 123145456122.89;
            Thread.CurrentThread.CurrentCulture = new CultureInfo((sender as Button).Tag.ToString());
            sonlar.Text = son.ToString("n2");
            vaqt.Text = DateTime.Now.ToString();
        }
    }
}

```

 Natijani ko’rishingiz mumkin:                                       

![default holatida](../../.gitbook/assets/image%20%2853%29.png)

![USA tugmachasini bosilganda](../../.gitbook/assets/image%20%2814%29.png)

Ko’rib turganingizdek sonlar formati o’zgardi. Ya’ni davlatda ishlatiladigan formatga qarab o’zgaradi. Odatda bunday usul dasturni o’rnatayotgan vaqtda sistemada tanlangan davlatga qarab son va vaqtni formatlash amalga oshiriladi

