---
description: Muzaffar Nurillayev
---

# Union

UNION so'rovi bir nechta SELECT so'rovidan qaytyotgan natijalarni takrorlanmasdan chiqarish uchun kerak bo'ladi. Lekin bu so'rov ishlashi uchun jadvallardan tanlab olingan ustunlar soni, ularning nomi, turi bir xil bo'lishi kerak.
{% hint style="info" %}
string ma'lumotlar varchar yoki text farq qilmaydi, varcharning o'lchami ham farq qilmaydi
{% endhint %}

Umumiy ko'rinishi quyidagicha bo'ladi:
```sql
SELECT ustun1 [, ustun2 ]
FROM jadval1 [, jadval2 ]
[WHERE shart]

UNION

SELECT ustun1 [, ustun2 ]
FROM jadval1 [, jadval2 ]
[WHERE shart]
```
Bizda 2 ta jadval bo'lsa:

1-jadval
```sql
CREATE TABLE company1_users(
id SERIAL PRIMARY KEY,
first_name VARCHAR(50),
last_name VARCHAR(60));
```
2-jadval
```sql
CREATE TABLE company2_users(
id SERIAL PRIMARY KEY,
first_name VARCHAR(100),
last_name VARCHAR(90));
```

Union ishlatilishi:
```sql
SELECT first_name, last_name FROM company1_users
   UNION
SELECT first_name, last_name FROM company2_users;
```
Bu so'rov ikkita jadvaldagi hamma qatorlarni oladida, har birining first_name va last_name bir vaqtning o'zida bir xil bo'lganlarini faqat 1 tasini qaytaradi.

Masalan, 'Muzaffar', 'Nurillayev' ikkita jadvalda ham bo'lsa faqat 1 ta bunaqa qator qaytariladi. Lekin 'Masud', 'Nurillayev' va 'Mahmud', 'Nurillayev' da first_name'lar bir xil bo'lmagani uchun ular qaytariladi.

Bundan bilib olishimiz mumkinki, UNION bu DISTINCT'ning kengaytirilgan varianti ekan.

### UNION ALL
Sintaksisi va talablari UNION bilan bir xil. Lekin ishlashida, qaytaradigan qiymatlarida boshqacha bo'ladi. UNION bizga takrorlanuvchilardan faqat bittasini qaytarsa, UNION ALL hamma natijalarni o'zgartirmay qaytaradi. Ya'ni yuqoridagi ikkita jadvaldagi 'Muzaffar', 'Nurillayev' larning ikkovi ham qaytariladi.
