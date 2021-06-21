---
description: Nodirbek Abdulaxadov
---

# Delegatlar

_Agar funksiyani parametr sifatida uzatishni xohlasak nima bo'ladi?
Qanday qilib C# callback funksiyalari yoki event larni boshqaradi?_

Javob: **Delegat**

**Delegat** - bu metod imzosini belgilaydigan ma'lumot turi. Siz boshqa ma'lumotlar turi kabi delegatning o'zgaruvchilarini yaratishingiz mumkin va ular yordamida delegat bilan bir xil parametrga ega har qanday metodga murojaat qilishingiz mumkin.

Delegatlar bilan ishlashda uchta bosqich mavjud:

1. Delegatni e'lon qiling

2. Kerakli metodni o'rnating

3. Delegatni chaqiring

Delegat quyida ko'rsatilgandek , **_delegate_** kalit so'zdan keyin funksiya imzosi yordamida e'lon qilinishi mumkin:

```csharp
[ruxsat modifikatori] delegate [qaytariluvchi tip] [delegat nomi]([parameterlar])
```

Quyida **MyDelegate** deb nomlangan delegat e'lon qilingan:

```csharp
public delegate void MyDelegate(string msg);
```
**...Information not finished yet!...**
