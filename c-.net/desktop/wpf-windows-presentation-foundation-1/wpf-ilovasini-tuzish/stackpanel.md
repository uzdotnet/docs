---
description: Sarvarbek Mumtozbekov
---

# StackPanel

StackPanel  - eng oddiy konpanovka konteynerlaridan biri. U bolalarini(children) bitta ustun yoki bitta qator qilib joylashtiradi. Misol uchun, quyidagi oynani ko‘ramiz:
```csharp
<Window
    x:Class="Test.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="StackPanel"
    Width="400"
    Height="250">
    <Window.Resources />
    <StackPanel>
        <Label>User ma’lumotlari</Label>
        <Label>Login:</Label>
        <TextBox></TextBox>
        <Label>Parol:</Label>
        <TextBox></TextBox>
        <Button>Saqlash</Button>
    </StackPanel>
    
</Window>
```

![](https://user-images.githubusercontent.com/91861166/220124438-7ad2dbd3-9b69-47b4-ae75-170250ba5bab.png)

Oddiy holda StackPanel ichidagi elementlarni tepadan pasga qarab joylashtiradi. Yuqoridagi misolda ko’rishimiz mumkunki, StackPanel elementlarni bo’yini minimum berib tepadan pasga qarab joylashtirgan, elementlarni eniga bo’lsa o’zini to’ldirguncha cho’zgan.


StackPanelning **Orientation** nomli xususiyatini o’zgartirish orqali elementlarni gorizontal joylashtirish mumkin. Bu holda esa elementlar eni minimum eni esa maximum bo’ladi:
```csharp
<StackPanel Orientation="Horizontal">
```

StackPanel konteyner bo’lgani bilan ichidagi elementlar ham o’z so’zini ayta oladi. Ichki elementlarni o’ziga xos xususiyatlarini o’zgartirish orqali ularni StackPanel ichida joylashuvini boshqarsa bo’ladi:

![](https://user-images.githubusercontent.com/91861166/220124578-d8cbcf77-3fac-4366-bda5-8afcdd7cede1.png)
