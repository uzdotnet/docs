---
description: Sobirjonov O'tkirbek
---

# Label elementi

Label elementidan sodda holda foydalanilsa Textblock elementiga juda o’xshab ketadi, faqatgina TextBlock elementida siz **Text** Property dan foydalansangiz, Label elementida esa **Content** Property dan foydalanasiz. Label elementi ichiga boshqa elementlarni joylashtirishingiz mumkin, va shu bilan TextBlock elementidan ajralib turadi. Label elementi – yorliqlar uchun foydalaniladi.

Buni oddiy misolda ko’rib o’tsak:

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
        <Label Content="Bu Label elementi"/>
    </Grid>
</Window>

```

![](<../../../.gitbook/assets/image (99).png>)

### TextBlock vs Label orasidagi farqlar    &#x20;

#### TextBlock elementi afzalliklari:

1. TextBlock elementida TextWrapping va boshqa shunga o’xshash matnlar bilan ishlashda ishlatiladigan Property lari mavjud.Va katta matnlar bilan ishlashda juda qo’l keladi.
2. Dasturda matn bilan ishlash vaqtida siz TextBlocklardan foydalaning, chunki TextBlock tezroq va yaxshiroq ishlaydi. Label elementi yorliq sifatida ishlatiladi. Shuning uchun oddiy matn va kattaroq hajmdagi matnlar bilan ishlaganingizda TextBlock dan foydalanganingiz ma’qul.

#### &#xD;&#xD;Label elementi afzalliklari:

1. Label elementida e’tibor bergan bo’lsangiz yuqori va chap qismlaridan ajratilibroq ko’rsatilmoqda, ya’ni Default holatda padding berib qoyilgan, TextBlockda esa unday emas.

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
    <StackPanel>
        <Label Content="Bu Label elementi" FontSize="15"/>
        <TextBlock Text="Bu TextBlock elementi" FontSize="15"/>
    </StackPanel>
</Window>

```

![](<../../../.gitbook/assets/image (25).png>)

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
    <StackPanel>
        <Label Content="Bu Label elementi" FontSize="15" Background="RoyalBlue"/>
        <TextBlock Text="Bu TextBlock elementi" FontSize="15" Background="Coral"/>
    </StackPanel>
</Window>

```

![](<../../../.gitbook/assets/image (1).png>)

2\. Label elementi Content Property siga matn berilgan holda Label Textblock yaratadi va ko’rsatadi, ya’ni matnlar bilan ishlashda Label elementi Textblock elementidan foydalanadi.

3\. Label elementida BorderBrush va BorderThickness Property lari mavjud. Ya’ni dasturda Chegaralar bilan ishlash imkoniyatlarini beradi.

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
        <Label BorderBrush="Gray" BorderThickness="2" FontSize="15" 
               Content="Label elementi" Width="110" Height="35"/>
    </Grid>
</Window>

```

![](<../../../.gitbook/assets/image (71).png>)

4\. Label elementi o’z ichida boshqa elementlarni ham saqlay oladi.Masalan : Image, TextBlock, StackPanel, Grid, ….

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
    <StackPanel Margin="10">
        <Label Target="{Binding ElementName=txtName}">
            <StackPanel Orientation="Horizontal">
                <Image     Source="http://cdn1.iconfinder.com/data/icons/fatcow/16/bullet_green.png" />
                <AccessText Text="_Nomi:" />
            </StackPanel>
        </Label>
        <TextBox Name="txtName" />
        <Label Target="{Binding ElementName=txtMail}">
            <StackPanel Orientation="Horizontal">
                <Image Source="http://cdn1.iconfinder.com/data/icons/fatcow/16/bullet_blue.png" />
                <AccessText Text="_Pochta:" />
            </StackPanel>
        </Label>
        <TextBox Name="txtMail" />
    </StackPanel>
</Window>

```

![](<../../../.gitbook/assets/image (90).png>)

Label elementiga qayta Template yozishingiz mumkin.Odatda yorliqlar ko’p ishlatiladi va ular turli xil Style da bo’lishi va turli dizaynda bo’lishi va ko’p dizaynlar bir xil bo’lishi mumkin. Ya’ni bir xil yozliqlar ko’p marta qo’llanilishi va har qo’llanilganda unga ko’p xususiyatlarni qayta o’rnatish ortiqcha ish albatta. Shu hollarda Style yozishingiz ham qo’l kelmasligi mumkin bunday hollarda Template yoziladi. TextBlock elementiga Style yozish mumkin lekin Template yozish mumkin emas, Label elementida esa bu imkoniyat mavjud.

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
    <Window.Resources>
        <Style TargetType="{x:Type TextBlock}">
        </Style>
        <Style TargetType="{x:Type Label}">
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="{x:Type Label}">
                        <Border Background="#A9BEFF" CornerRadius="5">
                            <StackPanel Orientation="Horizontal">
                                <Image Source="http://cdn1.iconfinder.com/data/icons/fatcow/16/bullet_blue.png" />
                                <TextBlock HorizontalAlignment="Left" FontSize="16" VerticalAlignment="Center" Margin="5" FontFamily="Sitka Text">
                                    <ContentPresenter />
                                </TextBlock>
                            </StackPanel>
                        </Border>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </Window.Resources>
    <StackPanel Margin="10">
        <Label Content="Assalomu alaykum" />
    </StackPanel>
</Window>

```

![](<../../../.gitbook/assets/image (40).png>)
