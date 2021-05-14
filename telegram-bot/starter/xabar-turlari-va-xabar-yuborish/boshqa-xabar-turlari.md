---
description: Xondamir Abduxoshimov
---

# Contact , Location, Venue

Xabarlar orasida, yana e'tiborga olishimiz kerak bo'lgan turlar bu - **contact,** **location** va **venue**. Ushbu mavzuda shu kabi xabar turlari bilan ishlashni ko'rib chiqamiz.

Birinchi qadamda **contact** turi bilan tanishib chiqamiz.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "contact yubor")
    {
        await client.SendContactAsync(
            chatId: e.Message.Chat.Id,
            // telefon raqami
            phoneNumber: "+9981234567",
            // ismi
            firstName: "Khan",
            // familyasi
            lastName: "Blogs"
        );
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%2850%29.png)

Joylashuv  odatda koordinatalar\(kenglik\) ga nisbat topiladi. **Location** - toifasida ham 2 ta asosiy maydon mavjud **longitude** va **latitude**.Ma'lum bir manzilni joylashuvini ko'rsatish uchun, uning kengliklarini berish kifoya.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "lokatsiya yubor")
    {
        await client.SendLocationAsync(
            chatId: e.Message.Chat.Id,                                    
            latitude: 40.783368f,                                    
            longitude: 72.350654f,
            // qancha vaqt ko'rsatib turishi
            livePeriod: 100 // sekundlarda
        );
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%286%29.png)

{% hint style="info" %}
**livePeriod** - maydoni 60 dan 86400 gacha oraliqdagi qiymatni qabul qiladi.
{% endhint %}

**Venue** xabar turi ham joylashuvni belgilashda foydalaniladi. Undan qo'shimcha tarzda **title**, hamda **address** ni belgilash mumkin.

```csharp
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "lokatsiya yubor")
    {
        await client.SendVenueAsync(
            chatId: e.Message.Chat.Id, 
            latitude: 40.783368f,                                    
            longitude: 72.350654f,
            title: "Andijon",
            address: "Paxtaobod, Yangi yo'l"
        );
    }
}
```

![](../../../.gitbook/assets/image%20%2880%29.png)

