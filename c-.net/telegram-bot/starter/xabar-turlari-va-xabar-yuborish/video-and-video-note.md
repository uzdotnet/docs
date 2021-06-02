---
description: Xondamir Abduxoshimov
---

# Video & Video Note

Agarda siz yubormoqchi bo'lgan fayl ko'rinishi MP4 formatda bo'lsa, ularni **video** yoki **video note** ko'rinishida yuborish imkoniyati mavjud. Boshqa turdagi formatlar esa, dokument sifatida yuboriladi. 

Quyidagi misolda videolarni qanday yuborish mumkinligini ko'rishingiz mumkin. 

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "video yubor")
    {
        using (var stream = System.IO.File.OpenRead("D:/video.mp4"))
        {
            await client.SendVideoAsync(
                chatId: e.Message.Chat.Id,
                video: stream,
                /*
                // zoom rasm
                thumb: "http://inordic.ru/images/news/2019/cs.jpg",                 
                duration: 30, // davomiyligi                
                height: 300, // balandligi                
                width: 300, // kengligi
                */                
                supportsStreaming: true, // videoni yuklash davomida ochish
                replyToMessageId: e.Message.MessageId,
                disableNotification: true
            );
        }
    }
}
```

**Natija:**

![](../../../../.gitbook/assets/image%20%2876%29.png)

Video fayllarda qo'shimcha tarzda **thumb** va **supportsStreaming** maydonlari mavjud. 

**thumb** - bu video yuklanishidan oldin video ustiga zoom holatda qo'yilgan rasm

![](../../../../.gitbook/assets/image%20%2849%29.png)

**supportsStreaming** - bu video yuklanmasdan ham uni ko'rish imkoniyati. Qiymat true bo'lsa ushbu imkoniyat amalga oshiriladi.

![](../../../../.gitbook/assets/image%20%2815%29.png)

**Video note** - bu telegramda aylana ko'rinishida taqdim etiladi, hamda uning davomiyligi 1 minut yoki undan ham kamroq bo'lishi mumkin. Ularni faqatgina, 2 xil holatda yuklash mumkin: lokal komputer yoki file\_id. Qaysidur HTTP so'rov orqali yuklash hozrda qo'llab quvvatlanmaydi.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "video yubor")
    {
        using (var stream = System.IO.File.OpenRead(@"D:\video.mp4"))
        {
            await client.SendVideoNoteAsync(
                chatId: e.Message.Chat.Id,
                videoNote: stream,                         
                duration: 30,               
                length: 360, // height va width                         
                replyToMessageId: e.Message.MessageId,
                disableNotification: true
            );
        }
    }
}
```

![](../../../../.gitbook/assets/image%20%285%29.png)

{% hint style="info" %}
E"tiborli bo'ling, video note xabar turkumida - yuboriladigan video o'lchamlari bir xil bo'lishi kerak.
{% endhint %}

