---
description: Sobirjonov O'tkirbek
---

# Textbox elementi

TextBox elementi WPF da tuzilgan dasturlarda asosiy kiritish elementi hisoblanadi. Ya’ni TextBox elementi bilan foydalanuvchiga matnlar kiritish, o’zgartirish, o’chirish va boshqa ko’p qulayliklarni yaratib beruvchi element hisoblanadi.

Avvalo oddiy misoldan boshlaymiz.

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
        <TextBox Height="25" FontSize="15" Width="200"/>
    </Grid>
</Window>

```

![](../../.gitbook/assets/image%20%28108%29.png)

![](../../.gitbook/assets/image%20%2869%29.png)

Shu ko’rinishda bo’ladi.TextBox lardan juda ko’p xollarda foydalangansiz ‘foydalanuvchi’ sifatida. Masalan qayerda? Biror bir saytga tashrif buyurganingizda albatta login va parol yozishingiz kerak bo’ladi, shu xollarda loginni kiritish uchun TextBox lar ishlatilgan. Nomi HTML kodida boshqa nomad bo’lishi mumkin lekin ma’nosi bir, Foydalanuvchi tomonidan matn ko’rinishidagi ma’lumotni olish uchun xizmat qiladi.

Agar siz TextBox ochilgan holatida unda qandaydir matn bo’lishini hohlasangiz uning **Text** Property siga o’zingiz kiritmoqchi bo’lgan matnni berib yuborasiz.

Ya’ni:

```aspnet
<TextBox Text="Salom!" Height="25" FontSize="15" Width="200"/>
```

  
Va oyna ochilganda TextBox elementida siz kiritgan matn hosil bo’ladi. TextBox-ga sichqonchaning o'ng tugmasini bosing. Sizga TextBox-dan Windows Clipboard-dan foydalanish imkoniyatini beradigan variantlar menyusi ochiladi. Va ushbu holatda siz tezkor tugmachalardan ham foydalanishingiz mumkin. \(Ctrl+X, Ctrl+C, Ctrl+V\) lar va hatto ortga qaytish \(Ctrl+Z\) ham ishlaydi

![](../../.gitbook/assets/image%20%28103%29.png)

Yuqorida ko’rgan TextBox elementimiz 1 qatorli TextBox edi, ya’ni ko’proq matn kiritilsa TextBox chapdan o’ngga ketma-ket kiritib boradi. Masalan:                                                                                            

TextBox ga ‘Sobirjonov O'tkirbek Sodiqjon o'g'li’ Matnini kiritilsa Biz kiritgan chegaralarga ko’ra quyidagicha joylashadi

![](../../.gitbook/assets/image%20%2835%29.png)

Endi esa keling shu TextBox imizni kattaroq matn kiritiladigan TextBoxga aylantiramiz.  Bu esa juda ham oson:

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
        <TextBox TextWrapping="Wrap" 
                 AcceptsReturn="True" 
                 FontSize="15" Margin="5"/>
    </Grid>
</Window>

```

![](../../.gitbook/assets/image%20%2823%29.png)

Biz ushbu ko’rinishda matn kiritish imkoniyatiga ega bo’ldik.

_TextWrapping="Wrap"_ – Matnni qatorlar bo’yicha kiritilishini ta’milaydi.

_AcceptsReturn="True"_- ‘Enter’ tugmasi boshqaruvi. MAtn kiritishda ‘Enter’ tugmasini bosganingizda keying qatorga tushishini ta’minlab beradi.

TextBox elementiga kiritiladigan belgilar sonini cheklash ham mumkin. _MaxLength="20"_  kiritilsa ushbu TextBox faqatgina 20 ta belgini kiritishga ruxsat beradi holos.

