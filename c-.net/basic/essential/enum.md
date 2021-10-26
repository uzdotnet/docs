---
description: Xakimbekov Doniyorbek
---

# Enum

**enum** - bu o’zgarmaslarni ifodalovchi maxsus “sinf” (qiymati **o’zgarmaydigan** yoki bir so’z bilan aytganda **read-only** o’zgaruvchilar).
**enum** ni yaratish uchun __enum__ kalit so’zidan foydalanamiz (interfeys yoki sinf o’rniga) va enum elementlari vergul bilan ajratib yoziladi: 


Array abstrakt sinfi System nomlar fazosida joylashgan. Bu sinf metodlariga murojaat qilish uchun **Array** kalit so’zidan keyin nuqta qo’yib, metod nomini yozamiz. Masalan, **Array.Sort\(A\);**

## **Misol uchun:**

```csharp
using System;
namespace NewApplication
{
    enum Level 
    {
      Low,
      Medium,
      High
    }
}
```

{% hint style="info" %}
_**Eslatma:** **BinarySearch\(\)** metodi to’g’ri ishlashi uchun unga kiritilayotgan massiv o’sish tartibida tartiblangan bo’lishi shart !._
{% endhint %}
