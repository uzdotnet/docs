---
description: Xondamir Abduxoshimov
---

# InlineKeyboardMarkup, InlineKeyboardButton

**InlineKeyboardMarkup** - biroz boshqacharoq tushuncha. Uning yordami bilan biz murakkab amallarni bajarishimiz mumkin bo'ladi.

Bu turdagi klaviaturani hosil qilishda **InlineKeyboardButton** sinfiga mansub obyektlardan foydalaniladi. **InlineKeyboardButton** bir vaqtning o'zida ham tugma matnini, hamda unga biriktirilgan datani olib yuradi. Ya'ni, bu data orqali, botimizni keyingi vazifalarini belgilashimiz mumkin.

```csharp
public string Index()
{
    // yangi event_handler yasaldi
    client.OnMessage += Xabar_Kelganda;
    
    //inline button bosilganda hosil
    // bo'ladigan event_handler 
    client.OnCallbackQuery += CallBack;

    // xabar kelishini tasdiqlash
    client.StartReceiving();
    
    return "Bot hozr ishlamoqda";
}


// callbackquery event_hand
private async void CallBack(object sender, CallbackQueryEventArgs e)
{
     if(e.CallbackQuery.Data == "A bosildi")
         await client
            .SendTextMessageAsync(e.CallbackQuery.From.Id, e.CallbackQuery.Data);
}

private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "test")
    {
        var markup = new InlineKeyboardMarkup(
            new InlineKeyboardButton[][]
            {
                new InlineKeyboardButton[]
                {
                    InlineKeyboardButton
                        .WithCallbackData(text: "A", callbackData: "A bosildi"),
                    
                    InlineKeyboardButton
                        .WithCallbackData(text: "B", callbackData: "B bosildi")
                },
                new InlineKeyboardButton[]
                {
                    InlineKeyboardButton
                        .WithCallbackData(text: "C", callbackData: "C bosildi"),
                    InlineKeyboardButton
                        .WithCallbackData(text: "D", callbackData: "D bosildi")
                }
            }
        );

                await client.SendTextMessageAsync(
                        chatId: e.Message.Chat.Id, 
                        text: "1 - test",
                        replyMarkup: markup
                    );            
            }
        }
```

**Natija:**

![](<../../../../.gitbook/assets/image (67).png>)

**OnCallBackQuery** - InlineKeyboardButton bosilganda hosil bo'ladigan xodisa hisoblanadi. Ko'rib turganingizdek biz ham bu xodisa ishlagan paytda, **CallBack()** deb nomlangan event\_handler funksiyaga murojaat qilishni ko'rsatib qo'ydik.

InlineKeyboardButton sinfiga mansub bir nechta metodlar mavjud, yuqoridagi misolda **WithCallbackData()** ko'rinishidan foydalanildi. Ushbu metoddan joy olgan **callbackData** maydoni orqali keyingi vazifani belgilashga muvaffaq bo'ldik.

{% hint style="info" %}
E'tiborli bo'ling, callbackdata maydoni - 1 - 64 baytgacha bo'lgan oraliqni qabul qila oladi.
{% endhint %}

Endigi navbatda, tugmalarni dinamik holatda hosil qilishni ko'rib chiqamiz.

```csharp
if (e.Message.Text == "tugmalar")
{
    // jagged massivini hosil qilish
    InlineKeyboardButton[][] button = new InlineKeyboardButton[2][];
    button[0] = new InlineKeyboardButton[5];
    button[1] = new InlineKeyboardButton[5];
    for (int i = 0; i < 10; i++)
    {
        if (i < button[0].Length)
        {
            // 1 - massiv
            button[0][i] = new InlineKeyboardButton
                            { 
                                Text = (i + 1).ToString(), 
                                CallbackData = (i + 1).ToString() 
                            };
        }
        else
        {
            // 2 - massiv
            button[1][i - button[0].Length] = new InlineKeyboardButton 
                                                { 
                                                    Text = (i + 1).ToString(), 
                                                    CallbackData = (i + 1).ToString()
                                                 };
        }
    }
    var markup = new InlineKeyboardMarkup(button);

    await client.SendTextMessageAsync(
        chatId: e.Message.Chat.Id, 
        text: "Tugmalar",
        replyMarkup: markup
    );            
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (87).png>)

Tugmalarni 2 ta ustunda ham hosil qilishimiz mumkin. Endi, boshqacharoq yo'l bilan hosil qilib ko'ramiz

```csharp
if (e.Message.Text == "tugmalar")
{
    List<InlineKeyboardButton> buttons = new List<InlineKeyboardButton>();
    for (int i = 0; i < 10; i++)
    {
        buttons.Add(new InlineKeyboardButton 
                    { 
                        Text = (i + 1).ToString(), 
                        CallbackData = (i + 1).ToString()
                    });
    }

    var twoMenu = new List<InlineKeyboardButton[]>();
    for (var i = 0; i < buttons.Count; i ++)
    {
        if (buttons.Count - 1 == i)
        {
            twoMenu.Add(new[] { buttons[i] });
        }
        else
            twoMenu.Add(new[] { buttons[i], buttons[i + 1] });
        i++;
    }
                
    var markup = new InlineKeyboardMarkup(twoMenu.ToArray());
                
    await client.SendTextMessageAsync(
        chatId: e.Message.Chat.Id, 
        text: "Tugmalar",
        replyMarkup: markup
    );            
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (59).png>)
