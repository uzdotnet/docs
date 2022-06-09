---
description: Nodirbek Abdulaxadov
---

# Liskovning Almashtirish Tamoyili\(LSP\)

Obyektga yo'naltirilgan dasturlashdagi vorislik - bu tizim bo'ylab ota-sinfdan(base class) amalga oshirishni bolalar sinflari(child class) ichida qayta ishlatishga imkon beruvchi xususiyat bo'lib, bu vorislikning asosiy afzalliklaridan birini ifodalaydi. Ammo, biz hal qilmoqchi bo'lgan yoki mavhumlashtirmoqchi bo'lgan ma'lum bir domen(model) uchun sinflarni loyihalashda, ba'zi yaxshi amaliyotlar (yoki yomonlari) uzoq muddatda dasturiy ta'minotning umumiy barqarorligiga ta'sir qilishi mumkin.

Asosan, meros ushbu manbadan foydalanishni oqlash uchun etarlicha o'xshashliklarga ega bo'lgan sinflar o'rtasida foydalanish uchun mo'ljallangan. Agar bolalar sinflari(child class) ular uchun mantiqiy bo'lmagan xususiyat va usullarga ega bo'lishni boshlasa, hatto ular ota-ona sinfidan(base class) bo'lsa ham, meros haqida yana bir bor o'ylab ko'rish vaqti keldi.

{% hint style="info" %}
**Liskov almashtirish printsipi (Liskov Substitution Principle)** - _yuqori sinf obyektlari dasturni buzmasdan uning kichik sinflari obyektlari bilan almashtirilishi kerak. Bu sizning pastki sinflaringiz obyektlari sizning yuqori sinfingiz obyektlari kabi harakat qilishini talab qiladi._
{% endhint %}

Yuqoridagi so'zlar va ta'riflar tushunish uchun ozgina qiyin bo'lishi mumkin.
