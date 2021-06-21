---
description: Nodirbek Abdulaxadov
---

# Delegatlar

_Agar funksiyani parametr sifatida uzatishni xohlasak nima bo'ladi?
Qanday qilib C# callback funktiyalari yoki event larni boshqaradi?_

Javob: **Delegat**

**Delegat** - bu metod imzosini belgilaydigan ma'lumot turi. Siz boshqa ma'lumotlar turi kabi delegatning o'zgaruvchilarini yaratishingiz mumkin va ular yordamida delegat bilan bir xil parametrga ega har qanday metodga murojaat qilishlari mumkin.

Delegatlar bilan ishlashda uchta bosqich mavjud:
* Delegatni e'lon qiling
* Kerakli metodni o'rnating
* Delegatni chaqiring

Delegat quyida ko'rsatilgandek , **_delegate_** kalit so'zdan keyin funksiya imzosi yordamida e'lon qilinishi mumkin:

```csharp
[access modifier] delegate [return type] [delegate name]([parameters])
```

Quyida MyDelegate nomlangan delegat e'lon qiladi:

```csharp
public delegate void MyDelegate(string msg);
```
