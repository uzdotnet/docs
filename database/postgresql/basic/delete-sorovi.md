---
description: Muzaffar Nurillayev
---

# Delete so'rovi

DELETE so'rovi ma'lum bir jadvalda mavjud bo'lgan qatorlarni o'chirish uchun xizmat qiladi. Bu so'rov tanlangan qatorlarning hammasini o'chiradi, shuning uchun ehtiyot bo'lib ishlating va doim WHERE bilan ishlatish maqsadga muvofiq.

Sintaksis unchalik qiyin emas:
```sql
DELETE FROM jadval_nomi;
```
Jadvalda nima bo'lsa hammasini o'chirib tashlaydi va natijadi jadvalimiz bo'shab qoladi. Bunday qilishning DROP so'rovi bilan aloqasi yo'q, chunki bunday qilganimizda jadvalning o'zi, strukturasi to'liq saqlanib qoladi.
```sql
DELETE FROM jadval_nomi
WHERE [shart];
```
Bu so'rov faqat shartni qanoatlantiradigan qatorlarni o'chirib tashlaydi.

Agar shartni qanoatlantiradigan birorta ham qator bo'lmasa, xatolik bermaydi va hech qanday o'chirish amali bajarilmaydi.

Kattaroq va murakkabroq so'rovlarda DELETE bilan ham subQuerylar ishlatish mumkin:
```sql
DELETE FROM company
WHERE id IN (SELECT id ROM company WHERE id IN (8, 9));
```
Odatda bunday qilinmaydi, lekin qanday qilishni bilish zarar qilmaydi.

Amaliy misolda ko'rib chiqsak:

![](https://user-images.githubusercontent.com/91861166/223755207-789220af-0634-4a43-96c0-9f5cd9501868.png)

Tepadagi so'rov shartni qanoatlantirganlarni hammasini jadvaldan o'chirdi. 
