---
description: Muzaffar Nurillayev
---

# Scheme

Kompyuteringizda biror bir faylni topish uchun uning aniq manzilini bilishingiz kerak. Fayllarni qayerda, qanday joylashtirish bo'yicha hamma o'zi qaror qabul qiladi. Masalan, har xil turdagi kontentlarni (video, proyekt, kitoblar, darslar) hammasini aralashtirib bitta joyda saqlasak ham bo'ladi, mavzusiga qarab har biri uchun alohida papka ochib, har birini o'z papkasiga joylash mumkin. Umuman olganda kompyuterga qizig'i yo'q qanday holatda saqlashimizning, lekin ma'lumotlarni tez topib olish uchun ikkinchi usulni foydalansak o'zimizga qulay bo'ladi, chalkashib ham ketmaymiz.

Schema'ni ham aynan papkaga o'xshatsak bo'ladi. Ya'ni database'ni kompyuter deb olsak jadvallarni to'g'ridan to'g'ri saqlasak ham bo'ladi, yoki schema'lar ochib alohida alohida saqlashimiz mumkin. Bundan kelib chiqadiki, schema bizga ma'lumotlarning umumiy strukturasini anglashga yordam beradi.

Biz to'g'ridan to'g'ri schema'lar ichida saqlaymiz. Keling amaliy misolda ko'rib chiqsak:

O'zimiz uchun database yaratib olamiz va unga bog'lanib olamiz.
```sql
create database schema_dnu;
\c schema_dnu;
```
Database'da mavjud bo'lgan schema'larni ko'rish uchun `\dn` buyrug'idan foydalanamiz.

![](https://user-images.githubusercontent.com/91861166/223293304-808cfdde-9743-4374-953c-51145c79b680.png)


Ko'rib turganingizdek bizda odatiy public nomli schema yaratilgan bo'ladi.

O'zimizning schema'mizni yaratish quyidagicha bo'ladi:

create schema test;
 Yana \dn buyrug'i bilan tekshirib ko'rsak endi bizda 2 ta schema bor:
```
schema_dnu=# \dn
   List of schemas
   Name |    Owner
--------+-------------------
 public | pg_database_owner
 test   | postgres
(2 rows)
```
O'zimiz yaratgan schema ichiga jadval yaratish uchun qaysi schemaligini belgilashimiz kerak, belgilamasak public schemasi ichida yaratiladi.

![student jadvali public nomli schema ichida yaratildi](https://user-images.githubusercontent.com/91861166/223293347-bba3c633-1314-424c-b13c-e80e9eccc0f2.png)

![student jadvali public nomli schema ichida yaratildi](https://user-images.githubusercontent.com/91861166/223293377-06526249-acda-4979-824e-fc0b0beee937.png)


Yuqoridagi yaratilgan 2 ta bir xil nomli table'lar har biri alohida. Chunki boshqa boshqa schemada joylashgan biri public, boshqa biri test.

{% hint style="info" %}
SELECT, DELETE, DROP kabi kalit so'zlar bilan ishlayotganda ham bir xil, to'liq qayerdaligini bersak aynan o'shanga boradi, bermasak public'ga.
{% endhint %}

Schema'ni o'chirish 2 xil bo'ladi:

1. Ichida hech nima bo'lmagan schema'ni o'chiradi.
```sql
drop schema schemaNomi;
```

2. Ichida table, view, funksiyalar bor schemani rekursiv - ichidagi ma'lumotlari bilan o'chiradi. 
```sql
drop schema schemaNomi cascade;
```
