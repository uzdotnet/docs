---
description: Xondamir Abduxoshimov
---

# Audio & voice

Bu 2 xabar turlari ham bir - biriga o'xshash hisoblanadi. Audiolar odatda **.mp3** formatda, voice lar esa, **.ogg** formatda bo'ladi.

Birinchi navbatda Audio xabarlari imkoniyatlarini sinab ko'ramiz.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "audio yubor")
    {
        Message msg = await client.SendAudioAsync(
            chatId: e.Message.Chat.Id,
            audio: "https://w1.musify.club/track/dl/942785/sting-shape-of-my-heart-from-the-professional-leon-and-three-of-hearts.mp3",
            /*caption: "Video fayl",
            title: "Shape of my heart", // sarlavhasi
            duration: 20, // davomiyligi sekundlarda
            performer: "Sting", // author 
            */
            replyToMessageId: e.Message.MessageId, 
            disableNotification: true
        );
        await client.SendAudioAsync(
            chatId: e.Message.Chat.Id,
            msg.Audio.FileId
        );
    }
}
```

Yuqoridagi berilgan kodlar telegramga MP3 soundlarini yuborishga xizmat qiladi. Ajablanayotgan bo'lsangiz kerak, nima uchun ba'zi maydonlar izohga olinganligiga. Bunga asosiy sabab, MP3 fayllarida ham **metadata**\(boshqa ma'lumotlarni tavsiflovchi ma'lumotlar\) ko'rinishi mavjud va telegram bu holatni qo'llab quvvatlaydi.

**Natija:**

![](../../../.gitbook/assets/image%20%2826%29.png)

**SendAudioAsync\(\)** asinxron funksiyasidan bizga **Message** sinfiga mansub obyekt qaytadi. Uning **msg.Audio** maydoni quyidagicha ko'rinishda bo'ladi.

```csharp
{
  "duration": 20,
  "mime_type": "audio/mpeg",
  "title": "Shape of my heart",
  "performer": "Sting",
  "file_id": "CQADBAADKQADA3oUUKalqDOOcqesAg",
  "file_size": 1102154
}
```

**Voice** xabarlari OGG fayllar turkumiga mansub. Keling ularni yuborishni biroz boshqacharoq yo'l bilan yuborishni ko'rib o'tamiz. Ya'ni hech qanday HTTP so'rovsiz, shunchaki o'zimizning lokal kompyuterdan. 

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if(e.Message.Text == "voice yubor")
    {
        Message msg;
        // lokal d: diskdan voice.ogg faylni o'qish        
        using (var stream = System.IO.File.OpenRead("D:/voice.ogg"))
        {
            msg = await client.SendVoiceAsync(
                chatId: e.Message.Chat.Id,
                voice: stream,
                duration: 20,
                caption: "voice fayl",
                replyToMessageId: e.Message.MessageId,
                disableNotification: true
            );
        }

        await client.SendVoiceAsync(
            chatId: e.Message.Chat.Id,
            msg.Voice.FileId
        );
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%2851%29.png)

