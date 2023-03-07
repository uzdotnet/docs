---
description: Muzaffar Nurillayev
---

# Where

Bu kalit so'zning vazifasini bilish uchun avvalo **SELECT**, **UPDATE**, **DELETE** so'rovlarining to'liq vazifalarini bilishingiz talab qilinadi.

Bilganingizdek, select bizga ma'lumotlarni hech qanaqa saralashlarsiz qaytarar edi. Lekin biz hamma ma'lumotni emas faqat ma'lum bir holni qanoatlantirganlarinigina qaytishini xohlasak, where kerak bo'ladi.

Sintaksisi juda ham oddiy:
```sql
SELECT ... FROM jadval_nomi
WHERE true_yoki_false_qaytaradigan_shart;
```
WHERE'dan keyin biz kerakli filterni logikasini yozamiz va bu so'rov biz uchun jadvaldagi har bir ma'lumotni biz bergan shart bo'yicha tekshiradi va qanoatlantiradiganlarini qaytaradi.



**UPDATE** so'rovida:

Bu so'rovni ishlatyotgan paytda shartni qanoatlantiradigan qatorlardagi ma'lumotning ustida o'zgarish qilinadi. Ammo, ma'lum bir shart bo'lmasa demak jadvaldagi hamma qatorlarga ta'sir ko'rsatadi. 
```sql
UPDATE jadval_nomi
SET ...
WHERE ...;
```

**DELETE** so'rovi ham xuddi **UPDATE** kabi ishlaydi, ya'ni shart bermasak hamma qatorlarni o'chirib chiqadi.
```sql
DELETE FROM jadval_nomi
SET ...
WHERE ...;
```

WHERE'dan keyin yozishimiz mumkin bo'lgan tekshiruvlar quyidagicha bo'lishi mumkin:

* WHERE id NOT NULL;
* WHERE id > 10;
* WHERE id <> 10;
* WHERE id = 10;
* WHERE id IN (1, 54, 56);
* WHERE id BETWEEN 100 AND 200;

{% hint style="info" %}
Shuning uchun UPDATE va DELETE so'rovlari bilan WHERE'ni ishlatishni unutmang, aks holda bu so'rovlar jadvalning hammasiga ta'sir o'tkazadi.
{% endhint %}
