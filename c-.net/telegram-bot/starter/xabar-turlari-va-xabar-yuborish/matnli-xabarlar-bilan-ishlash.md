---
description: Xondamir Abduxoshimov
---

# Matnli xabarlar bilan ishlash

Matnli xabar - bu bot strukturasi uchun yaxshi interfeys va odatda ko'p foydalaniladi. Matnli xabarlarni yuborish oson, shuningdek internet tezligi pastroq bo'lgan qurilmalarda tez namoyish qilinadi.&#x20;

Birinchi foydalanuvchidan kelgan xabarlarni qaysi turga mansubligini, so'ngra xabarlar ketma-ketligiga xos holda matnlarni yuborishni ko'rib chiqamiz.

## Kelgan xabarlarni tekshirish

Xabarlarni qaysi xabar turiga tegishlik ekanligini tekshirish uchun **Telegram.Bot.Types.Enums** namespace iga mansub **MessageType** enum ma'lumotlar toifasidan foydalanishimiz mumkin. Ya'ni:

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Type == Telegram.Bot.Types.Enums.MessageType.Text)
    {
        // amallar
    }
}
```

Kelgan xabar turi matn ko'rinishida bo'lsa vazifalarni belgilashimiz mumkin.&#x20;

Yana bir e'tiborga olishimiz kerak bo'lgan jihat bor. U shundan iboratki, yuqoridagi holatda istalgan matnli xabar kelganda berilgan shart o'rinli bo'ladi. Demak, biz nafaqat kelgan xabar turi, balkim unda kelgan matnni ham tekshirishimiz zarur.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Type == Telegram.Bot.Types.Enums.MessageType.Text)
    {
        if(e.Message.Text == "/start")
        {
            // amalllar
        }
    }
}
```

Qisqacha ko'rinishda quyidagicha yozib qo'yish ham mumkin.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "/start")
    {
        // amalllar
    }
}
```

Kelgan xabarni tekshirishni ko'rdik, navbat endi ularga mos holatda matnlarni yuborish. Matnli xabarlarni yuborish uchun **SendTextMessageAsync()** asinxron funksiyasidan foydalaniladi. Ushbu finksiyada quyidagicha parametrlar mavjud:

* chatId - foydalanuvchi ID si
* text - yubormoqchi bo'lgan xabar
* replyToMessageId - xabar ID si
* parseMode - matn formati
* disableNotification - ovoz bilan borishligi
* replyMarkup -  _InlineKeyboardMarkup_  yoki _ReplyKeyboardMarkup_ usulida belgilash

Keling endi bir misol ko'ramiz

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "salom")
    {
        await client.SendTextMessageAsync(
                        chatId: e.Message.Chat.Id,
                        text: "*Assalomu alaykum*",
                        replyToMessageId: e.Message.MessageId,
                        parseMode: Telegram.Bot.Types.Enums.ParseMode.Markdown, 
                        disableNotification: true
                    );
    }
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (7) (4) (4) (1) (1) (1) (1) (1) (1) (1) (2) (1) (1).png>)

Matnli xabarlarni doimo bir xil usulda taqdim etish bu foydalanuvchini zeriktiradi. Bu holatda matnni formatlangan ko'rinishlarda tadim etish, samarali yo'l hisoblanadi. Odatda 2 xil formatlash usuli mavjud:&#x20;

1. Markdown
2. HTML

Yuqorida keltirilgan misolda Markdown usulidan foydalanilgan. Formatlash usullarini [shu yerdan](https://sourceforge.net/p/telegram-bot/wiki/markdown\_syntax/) olishingiz mumkin
