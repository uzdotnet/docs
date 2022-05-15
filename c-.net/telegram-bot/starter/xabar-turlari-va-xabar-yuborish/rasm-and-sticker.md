---
description: Xondamir Abduxoshimov
---

# Rasm & Sticker

Multimedia xabarlari (photo, video...) ni bir necha usul orqali telegramga yuklash mumkin.

* HTTP so'rov&#x20;
* Telegram serverdagi file\_id si &#x20;

Foydalanuvchiga yaratilgan bot orqali rasm fayllarni yuborish, **SendPhotoAsync()** asinxron funksiyasi yordamida amalga oshiriladi.&#x20;

Mavzuni **SendPhotoAsync()** metodi qabul qiladigan argumentlar, hamda yuqorida sanab o'tilgan ikki usul orqali, uning imkoniyatlarni sinash bilan davom ettiramiz.

Qabul qilinadigan argumentlar:

* chatId - foydalanuvchi ID si
* photo - yubormoqchi bo'lgan rasm
* caption - rasm tasnifi
* replyToMessageId - xabar ID si
* parseMode - matn formati
* disableNotification - ovoz bilan borishligi
* replyMarkup -  _InlineKeyboardMarkup_  yoki _ReplyKeyboardMarkup_ usulida belgilash

#### &#x20;HTTP so'rov orqali rasm yuborish

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "rasm yubor")
    {
        await client.SendPhotoAsync(
                    chatId: e.Message.Chat.Id,
                    photo: "https://www.pinclipart.com/picdir/middle/498-4987331_panda-cartoon-png-cute-cartoon-panda-bear-clipart.png",
                    caption: "Bu panda",
                    replyToMessageId: e.Message.MessageId,
                    parseMode: Telegram.Bot.Types.Enums.ParseMode.Markdown, 
                    disableNotification: true
                );
    }
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (28) (6) (1) (1) (1) (1).png>)

{% hint style="info" %}
Biz xabarlarni yuborishda foydalanayotgan funksiyalar ishni yakunlagandan so'ng, **Message** sinfiga mansub obyekt qaytaradi.
{% endhint %}

#### file\_id bo'yicha rasm yuborish

Har bir media xabar telegram severga yuborilgandan so'ng, unga qaytarilmaydigan **file\_id** taqdim etiladi. Agar yuborilgan fayl yana qayta yuklanishi kerak bo'lsa, telegram serveriga **file\_id** bo'yicha murojaat qilsak ham bo'ladi.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "rasm yubor")
    {
        Message msg = await client.SendPhotoAsync(
            chatId: e.Message.Chat.Id,
            photo: "https://www.pinclipart.com/picdir/middle/498-4987331_panda-cartoon-png-cute-cartoon-panda-bear-clipart.png",
            caption: "Bu panda",
            replyToMessageId: e.Message.MessageId,
            parseMode: Telegram.Bot.Types.Enums.ParseMode.Markdown, 
            disableNotification: true
        );
        
        await client.SendPhotoAsync(
            chatId: e.Message.Chat.Id,
            msg.Photo[0].FileId
        );
    }
}
```

**PhotoSize** sinfiga tegishli bo'lgan **msg.Photo** massivi **JSON(Javascript Object Notation)** toifasiga mansub qiymat qabul qiladi.&#x20;

```csharp
[    
    {
        "file_id": "AgADBAADDqgxG-QDDVCm5JVvld7MN0z6kBkABCQawlb-dBXqBZUEAAEC",
        "file_size": 1254,
        "width": 90,
        "height": 60
    }
]
```

Agarda siz uchun JSON tushunchasi yangilik bo'lsa, unda ushbu [video](https://youtu.be/j3acDpmZi2g?list=PLFE1Bk1-05KxJsD-ID7\_Q9HXb8hSeg53N) orqali u haqida ma'lumot olishingiz mumkin.

Sticker lar bilan ishlash ham unchalik qiyin emas, sxematikasi rasmlarnikiga o'xshash.



{% hint style="info" %}
Yuboriladigan sticker lar odatda, **.webp** kengaytmali bo'lishi talab etiladi. Sticker larda caption va parseMode tushunchalari mavjud emas.
{% endhint %}

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "sticker yubor")
    {
        Message msg = await client.SendStickerAsync(
            chatId: e.Message.Chat.Id,
            sticker: "https://chpic.su/_data/stickers/s/stickersonlyspack/stickersonlyspack_001.webp",
            replyToMessageId: e.Message.MessageId, 
            disableNotification: true
        );
        await client.SendStickerAsync(
            chatId: e.Message.Chat.Id,
            msg.Sticker.FileId
        );
    }
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (55).png>)

Lokal holatda komputerimizda joylashgan media fayllarni yuklashni, keyingi mavzuda ko'rib chiqamiz.
