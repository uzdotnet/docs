---
description: Ravshan Sodiqov
---

# Model

**Model** - ASP.NET MVC strukturasida modellar biznes logikani saqlovchi sinflardir. Ushbu sinflar loyihalarda saqlanadigan har qanday ma’lumotlarning modellarini yaratgan holda ulardan osongina foydalanish imkonini beradi. Ya’ni, loyihada qanday ma’lumot almashinuvi mavjud bo’lmasin, ularning barchasi «Models» papkasida sinflar ko’rinishida saqlanadi.

Faraz qilaylik, loyihada foydalanuvchilarga hisob yaratish, yaratilgan hisob ma’lumotlarini tahrirlah va hisobdan chiqish imkoniyatlarini bersin. Bunda biz har bir foydalanuvchiga oid ma’lumotlar: ID, Firstname, Lastname, Email va Password kabi ma’lumotlarni saqlashimiz uchun, aynan mana shunday xususiyatlarga ega sinfni «Models» papkasida yaratishimiz kerak bo’ladi. 

```csharp
public class User
{
    public Guid Id  {get; set;}
    public string  Firstname { get; set; }
    public string  Lastname { get; set; }
    public string  Email { get; set; }
    public string Password  {get; set;}
}
```
Yuqoridagi sinf umumiy biznes logikani saqlab qolgan holda, foydalanuvchilar ma’lumotlarining oson almashuvini ta’minlashda yordam beradi.
