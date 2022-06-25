---
description: Xondamir Abduxoshimov
---

# Dokument fayllar

Bundan oldingi mavzularda sanab o'tilgan fayl formatlaridan tashqari fayllarni **SendDocumentAsync()** asinxron funksiyasidan foydalangan holda amalga oshirish mumkin.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "document yubor")
    {
        using (var stream = System.IO.File.OpenRead(@"D:\salom.txt"))
        {
            await client.SendDocumentAsync(
                chatId: e.Message.Chat.Id,
                document: stream,    
                caption: "Document file",
                replyToMessageId: e.Message.MessageId,
                disableNotification: true
            );
        }
    }
}
```

**Natija:**

![](<../../../../.gitbook/assets/image (107) (1) (1) (1) (1) (2) (2) (2) (2) (2) (1) (1) (1) (1) (1) (1).png>)
