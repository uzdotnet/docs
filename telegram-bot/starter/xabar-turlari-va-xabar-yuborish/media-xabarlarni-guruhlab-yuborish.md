---
description: Xondamir Abduxoshimov
---

# Album\(Media Group\)

Xabarlarni guruh\(bir nechta\)lab yuborish faqat - media\(video, photo, audio, document\) fayllari uchun o'rinli. Lekin biz foydalanadigan **Telegram.Bot** namespace ida faqatgina photo va video larni guruhlab yuborish imkoniyati mavjud.

Media fayllarni guruhlab yuborishda - elementlar soni 2 tadan 10 tagacha bo'lishligi kerak bo'ladi.

Quyida ushbu amallarni qanday bajarishni ko'rishingiz mumkin.

```csharp
[System.Obsolete]
private async void Xabar_Kelganda(object sender, MessageEventArgs e)
{
    if (e.Message.Text == "rasmlarni yubor")
    {
        await client.SendMediaGroupAsync(
            chatId: e.Message.Chat.Id, 
            media: new[]
            {
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg"),
                new InputMediaPhoto("http://inordic.ru/images/news/2019/cs.jpg")
            }
        );
    }
}
```

**Natija:**

![](../../../.gitbook/assets/image%20%2837%29.png)

Yuqorida berilgan kodlarda sizlar uchun yangilik holat mavjud. Keling shu to'g'risida to'xtalib o'tamiz.

E'tibor bergan bo'lsangiz, **Xabar\_Kelganda\(\)** metodi yuqorisida **\[System.Obsolete\]** atributi mavjud. **SendMediaGroupAsync\(\)** funksiyasi bilan tanishish davomida bu funksiya, obsolete\(eskirgan\) ko'rinishida ekanligiga amin bo'ldim. Bu shuni anglatadiki, agarda dasturchi sinf maydonida biror - bir eskirgan metodni o'rniga yangi metod hosil qilib, lekin eskirgan metodniyam qolishini istasa, unga murojaat bo'lgan paytda, yangi metodga murojaat qilishini, hamda bu metod eskirganini bildirishi mumkin. Ushbu holat - funskiyani obselete ko'rinishi hisoblanadi.

