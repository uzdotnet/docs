---
description: Nodirbek Abdulaxadov
---

# Liskovning Almashtirish Tamoyili\(LSP\)

Obyektga yo'naltirilgan dasturlashdagi vorislik - bu tizim bo'ylab ota-sinfdan(base class) amalga oshirishni bolalar sinflari(child class) ichida qayta ishlatishga imkon beruvchi xususiyat bo'lib, bu vorislikning asosiy afzalliklaridan birini ifodalaydi. Ammo, biz hal qilmoqchi bo'lgan yoki mavhumlashtirmoqchi bo'lgan ma'lum bir domen(model) uchun sinflarni loyihalashda, ba'zi yaxshi amaliyotlar (yoki yomonlari) uzoq muddatda dasturiy ta'minotning umumiy barqarorligiga ta'sir qilishi mumkin.

Asosan, meros ushbu manbadan foydalanishni oqlash uchun etarlicha o'xshashliklarga ega bo'lgan sinflar o'rtasida foydalanish uchun mo'ljallangan. Agar bolalar sinflari(child class) ular uchun mantiqiy bo'lmagan xususiyat va metodlarga ega bo'lishni boshlasa, hatto ular ota-ona sinfidan(base class) bo'lsa ham, meros haqida yana bir bor o'ylab ko'rish vaqti keldi.

{% hint style="info" %}
**Liskov almashtirish printsipi (Liskov Substitution Principle)** - _yuqori sinf obyektlari dasturni buzmasdan uning kichik sinflari obyektlari bilan almashtirilishi kerak. Bu sizning pastki sinflaringiz obyektlari sizning yuqori sinfingiz obyektlari kabi harakat qilishini talab qiladi._
{% endhint %}

Yuqoridagi ta'riflar tushunish uchun ozgina qiyin bo'lishi mumkin. Shuning uchun keling bularni amalda qo'llab tushinishga harakat qilamiz.

Tasavvur qiling biz telegram guruhidagi a'zolar va adminlar uchun berilgan ruxsatlarni muhokama qilaylik. Bizda telegram foydalanuvchisi - TelegramUser, guruh a'zosi - GroupSubscriber va guruh admini - GroupAdmin sinflari bor.

## TelegramUser sinfi:

```csharp
    public class TelegramUser
    {
        public string FullName { get; set; } = string.Empty;
        public string Email { get; set; } = string.Empty;
        public string Password { get; set; } = string.Empty;

        public virtual void AccessToAddAdmin()
        {
            Console.WriteLine("Guruhga admin qo'shish uchun ruxsat berilgan");
        }

        public virtual void AccessToChangeGroupInfo()
        {
            Console.WriteLine("Guruh ma'lumotlarini o'zgartirish uchun ruxsat berilgan");
        }

        public virtual void AccessToReadMessages()
        {
            Console.WriteLine("Xabarlarni o'qish uchun ruxsat berilgan");
        }
        public virtual void AccessToRemoveMessages()
        {
            Console.WriteLine("Xabarlarni o'chirish uchun ruxsat berilgan");
        }
    }
```

## GroupSubscriber sinfi:

```csharp
    public class GroupSubscriber : TelegramUser
    {
        public override void AccessToAddAdmin()
        {
            throw new InvalidOperationException("Ruxsat berilmagan!");
        }

        public override void AccessToChangeGroupInfo()
        {
            throw new InvalidOperationException("Ruxsat berilmagan!");
        }

        public override void AccessToReadMessages()
        {
            base.AccessToRemoveMessages();
        }

        public override void AccessToRemoveMessages()
        {
            base.AccessToRemoveMessages();
        }
    }
```

## GroupAdmin sinfi:

```csharp
    public class GroupAdmin : TelegramUser
    {
        public override void AccessToAddAdmin()
        {
            base.AccessToAddAdmin();
        }

        public override void AccessToChangeGroupInfo()
        {
            base.AccessToChangeGroupInfo();
        }

        public override void AccessToReadMessages()
        {
            base.AccessToReadMessages();
        }

        public override void AccessToRemoveMessages()
        {
            base.AccessToRemoveMessages();
        }
    }
```

Yuqorida ko'rib turganingizdek, ikkala bola sinf(child class) ham TelegramUser sinfidan meros qilib olinyapti. GroupSubscriber(guruh a'zosi)ga guruh ma'lumotlarini o'zgartirish va admin qo'shish kabi xususiyatlar xos emas. Demak, TelegramUser bu ikki sinf uchun umumiy bo'la olmadi.


{% hint style="info" %}
Liskov printsipini qo'llash uchun ikkita yondashuv mavjud:
    1. Ota-sinfda faqat umumiy xususiyatlar va metodlarni belgilang, har qanday o'ziga xoslikni bolalar sinflariga qoldiring.
    2. Ota-sinfni bola sinflari o'ziga xosliklarini to'g'ri taqsimlaydigan bir nechta interfeyslarda  ajrating.
{% endhint %}

## 1-usul - o'ziga xos bo'lgan xususiyatlar va metodlar o'sha sinfning o'zida e'lon qilinadi:

```csharp
    public class TelegramUser
    {
        public string FullName { get; set; } = string.Empty;
        public string Email { get; set; } = string.Empty;
        public string Password { get; set; } = string.Empty;
    }

    public class GroupSubscriber : TelegramUser
    {
        public virtual void AccessToReadMessages()
        {
            Console.WriteLine("Xabarlarni o'qish uchun ruxsat berilgan");
        }
        public virtual void AccessToRemoveMessages()
        {
            Console.WriteLine("Xabarlarni o'chirish uchun ruxsat berilgan");
        }
    }

    public class GroupAdmin : TelegramUser
    {        
        public virtual void AccessToAddAdmin()
        {
            Console.WriteLine("Guruhga admin qo'shish uchun ruxsat berilgan");
        }

        public virtual void AccessToChangeGroupInfo()
        {
            Console.WriteLine("Guruh ma'lumotlarini o'zgartirish uchun ruxsat berilgan");
        }
        
        public virtual void AccessToReadMessages()
        {
            Console.WriteLine("Xabarlarni o'qish uchun ruxsat berilgan");
        }
        
        public virtual void AccessToRemoveMessages()
        {
            Console.WriteLine("Xabarlarni o'chirish uchun ruxsat berilgan");
        }
    }
```

## 2-usul - quyida ko'rsatilganidek, har bir holat uchun maxsus interfeyslarni yaratishdir:

```csharp
    public interface IGroupUser
    {
        void AccessToReadMessages();
        void AccessToRemoveMessages();
    }

    public interface IGroupAdmin
    {
        void AccessToAddAdmin();
        void AccessToChangeGroupInfo();
    }

    public class TelegramUser
    {
        public string FullName { get; set; } = string.Empty;
        public string Email { get; set; } = string.Empty;
        public string Password { get; set; } = string.Empty;
    }

    public class GroupSubscriber : TelegramUser, IGroupUser
    {
        public virtual void AccessToReadMessages()
        {
            Console.WriteLine("Xabarlarni o'qish uchun ruxsat berilgan");
        }
        public virtual void AccessToRemoveMessages()
        {
            Console.WriteLine("Xabarlarni o'chirish uchun ruxsat berilgan");
        }
    }

    public class GroupAdmin : TelegramUser, IGroupUser, IGroupAdmin
    {
        public void AccessToAddAdmin()
        {
            Console.WriteLine("Admin qo'shish uchun ruxsat berilgan");
        }

        public void AccessToChangeGroupInfo()
        {
            Console.WriteLine("Guruh ma'lumotlarini o'zgartirish uchun ruxsat berilgan");
        }

        public virtual void AccessToReadMessages()
        {
            Console.WriteLine("Xabarlarni o'qish uchun ruxsat berilgan");
        }
        public virtual void AccessToRemoveMessages()
        {
            Console.WriteLine("Xabarlarni o'chirish uchun ruxsat berilgan");
        }
    }
```

{% hint style="success" %}
    Agar sizning kodingiz Liskov almashtirish printsipiga rioya qilsa, sizda ko'p afzalliklar mavjud. Bularga quyidagilar kiradi: kodni qayta ishlatish, qisqartirilgan ulanish va oson texnik xizmat ko'rsatish.
{% endhint %}
