---
description: Xondamir Abduxoshimov
---

# Polls

Guruh va kanallarda biror - bir mavzu to'g'risida so'rovnoma o'tkazishda **poll** xabar turidan foydalaniladi. 

![](../../../.gitbook/assets/image%20%289%29.png)

Poll ko'rinishidagi xabar turlari 2 xil bo'ladi.

* Oddiy poll
* Quiz poll

Demak, ilk qadamda oddiy pollar qanday yasalishini ko'rib chiqamiz.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "poll yubor")
    {
        await client.SendPollAsync(
            chatId: e.Message.Chat.Id,
            question: "C# qiziqroqmi?",
            options: new[]
            {
                "Ha",
                "Yo'q"
            }
        );                
    }
}
```

Natija

![](../../../.gitbook/assets/image%20%2879%29.png)

Oddiy pollarda bir nechta tanlovni ham amalga oshirish mumkin.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "poll yubor")
    {
        await client.SendPollAsync(
            chatId: e.Message.Chat.Id,
            question: "Qaysi dasturlash tillarni bilasiz?",
            options: new[]
            {
                "C++",
                "C#",
                "Java",
                "Kotlin",
                "Swift",
                "Javascript",
                "Python"
            },
            allowsMultipleAnswers: true,
            // so'rovnmoma qancha ochiq turishi
            openPeriod: 100 // sekundlarda amal qiladi
                
        );                
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%2817%29.png)

So'rovnomani test sifatidayam o'tkazish mumkin.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "poll yubor")
    {
        await client.SendPollAsync(
            chatId: e.Message.Chat.Id,
            question: "C# da i++ vazifasi nima?",
            options: new[]
            {
                "i ni qiymatini birga oshirish",
                "i ni qiymatini birga kamaytirish",
                "Hech qanday vazifa bajarmaydi"
            },
            type: Telegram.Bot.Types.Enums.PollType.Quiz,
            // to'g'ri javob idsi
            correctOptionId: 0, // 0 dan boshlanadi sanash 
            // so'rovnmoma qancha ochiq turishi
            openPeriod: 100 // sekundlarda amal qiladi
                    
        );                
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%2818%29.png)

