---
description: Muzaffar Nurillayev
---

# And va Or

Bu ikki operator 2 va undan ortiq shartlarni o'zaro bog'lash uchun xizmat qiladi. Bular xuddi dasturlash tillaridagi and(&&) va or(||) bilan bir xil vazifa bajaradi va ularni so'rovning shart beryotgan qismida ishlata olamiz.

{% hint style="info" %}
HAVING, WHERE kalit so'zlaridan keyin ishlatiladi.
{% endhint %}

### AND operatori sintaksisi
```sql
SELECT ustun1, ustun2, ustunN
FROM jadval_nomi
WHERE [shart1] AND [shart2]...AND [shartN];
```
Bunaqa paytda hamma shartlar TRUE qiymat qaytarsa so'rov shu natijani qaytaradi. Bu yerda faqat SELECT so'rovi orqali misol ko'rsatilgan, UPDATE va DELETE so'rovlarida ham shunaqa bajariladi.

### OR operatori sintaksisi 
```sql
SELECT ustun1, ustun2, ustunN
FROM jadval_nomi
WHERE [shart1] OR [shart2]...OR [shartN];
```
Bunaqa paytda kamida bitta shart ham TRUE qaytarsa shu qator ustida so'rov bajariladi.

### Birga ishlatish sintaksisi
```sql
SELECT ustun1, ustun2, ustunN
FROM jadval_nomi
WHERE ([shart1] AND [shart2]) OR...[shartN];
```
Ularni birga ishlatish uchun qaysi shartlar o'zaro aloqadorligi bo'lsa bitta qavs ichida bo'lishi kerak. Bu readability'ni ham oshiradi va kattaroq va kengroq tekshiruvlar qilishda ham juda muhim hisoblanadi. Ba'zi paytlarda qavs qo'yish yoki qo'ymaslik bir xil natija berishi mumkin, lekin qavs qo'yish tavsiya beriladi.
