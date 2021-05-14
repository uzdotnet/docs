---
description: Xondamir Abduxoshimov
---

# ReplyKeyboardMarkup, KeyboardButton

**ReplyKeyboardMarkup** - qisqa qilib aytganda, xabar ko'rinishidagi shablonlar. Bu ko'rinishdagi klaviatura turlarida faqatgina matnlar ro'l o'ynaydi. Ya'ni, tugmalar bosilganda foydalanuvchi o'rniga kerakli matnni yuboradi.

Masalan, sizning botingiz foydalanuvchiga savol beradi va javoblar uchun variantlarni taqdim etadi. Foydalanuvchi javobni mustaqil tarzda yozishi yoki tayyor tugmani bosishi mumkin. Qaysidur ma'noda matnni o'zimiz yozgandan ko'ra tayyor tugmani bosish ancha qulaylik beradi.

![](../../../.gitbook/assets/image%20%28104%29.png)

**ReplyKeyboardMarkup** toifasidagi klaviaturani hosil qilishda **KeyboardButton** sinfiga mansub tugmalardan foydalaniladi. 

Keling yuqorida keltirilgan rasmdagi ko'rinishni qanday hosil qilishni ko'rib chiqamiz.

```csharp
// ReplyKeyboardMarkup obyekt olish
ReplyKeyboardMarkup markup = new ReplyKeyboardMarkup();
// Keyboard sinfiga oid jagged(massiv ichida massiv)
// masivini hosil qilish 
markup.Keyboard = new KeyboardButton[][]
{
      // 1 - qator
      new KeyboardButton[]
      {
         new KeyboardButton("A"),
         new KeyboardButton("B")
      },
      // 2 - qator
      new KeyboardButton[]
      {
         new KeyboardButton("C"),
         new KeyboardButton("D")
      }
 };
                
       await client.SendTextMessageAsync(
            chatId: e.Message.Chat.Id, 
            text: "1 - test",
            replyMarkup: markup
        );
```

Ko'rib turganingizdek, tugmalar massivini static holatda hosil qildik.

**ReplyKeyboardMarkup** sinfining yana qo'shimcha maydonlarni mavjud:

* OneTimeKeyboard - tugma foydalanilganidan so'ng uni yashirish
* ResizeKeyboard - Vertikal holatda formaga binoan moslashuvchanlik
* Selective - tugmani faqat ma'lum foydalanuchilarga ko'rsatish

**Keyboard** sinfiga mansub tugmalar orqali, foydalanuvchidan **Contact, Location, Poll** kabi xabarlarni yuborishni ham so'rash mumkin. 

Foydalanuvchidan Contact ma'lumotlarini yuborishni so'rash.

```csharp
if (e.Message.Text == "/start")
{
        ReplyKeyboardMarkup markup = 
                new ReplyKeyboardMarkup
                        (KeyboardButton.WithRequestContact("Contact yuborish"));
        markup.ResizeKeyboard = true;
        await client.SendTextMessageAsync(
                chatId: e.Message.Chat.Id, 
                text: "Contact",
                replyMarkup: markup
        );
}
```

![](../../../.gitbook/assets/image%20%282%29.png)

