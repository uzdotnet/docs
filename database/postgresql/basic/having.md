---
description: Axmadjonov Abdulloh
---

# Having

PostgreSQL-da ma'lumotlar bilan ishlashda siz "**having**" atamasini uchratishingiz mumkin. “**having**” –  “**group by**” ishlatilganidan keyingi natijani filtrlash uchun ishlatilinadi. "**where**" ni bu yerda ishlatish esa mumkin emas. Shuning uchun "**having**" ishlatilinadi.

Boshqacha qilib aytganda , guruhlar tomonidan bajarilishi kerak bo'lgan shartlarni ko'rsatish orqali guruhlangan so'rov natijalarini filtrlash uchun "**having**" bandi ishlatiladi. Ushbu shartlar agregat funktsiyalar va qiymatlar o'rtasidagi taqqoslashni yoki agregat funktsiyalarning o'zlari o'rtasidagi taqqoslashni o'z ichiga olishi mumkin.

Misol uchun, sizda sotuvchi, mahsulot va sotuv miqdori ustunlari bo'lgan savdo ma'lumotlari jadvali bor deylik. Har bir sotuvchi uchun umumiy savdo miqdorini topish uchun quyidagi SQL so'rovidan foydalanishingiz mumkin:
```sql
SELECT sotuvchi, SUM(sotuv_summasi) as jami_sotuvlar
FROM sotuvlar                                                                                    
GROUP BY sotuvchi;                                                                         
```
Bu har bir sotuvchi va ularning umumiy savdo miqdori uchun bitta qatorli jadvalni qaytaradi. Biroq, agar siz faqat 1 000 000 so'mdan ortiq savdoga ega bo'lgan sotuvchilarni ko'rishni istasangiz, so'rovga "having" bandini qo'shishingiz mumkin:
```sql
SELECT sotuvchi, SUM(sotuv_summasi) as jami_sotuvlar
FROM sotuvlar                                                                                    
GROUP BY sotuvchi                                                                          
HAVING SUM(sotuv_summasi) > 1000000;                             
```
Bu faqat umumiy savdosi 1 000 000 so'mdan ortiq bo'lgan sotuvchilar jadvalini qaytaradi.

Xulosa qilib aytganda, "having" funksiyasi "group by" funksiyasi bilan belgilangan guruhlarga qo'llaniladigan shartlar asosida jamlangan so'rov natijalarini filtrlash uchun ishlatiladi.
