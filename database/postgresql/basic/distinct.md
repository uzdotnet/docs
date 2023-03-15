---
description: Azim Ochilov
---

# Distinct

DISTINCT

PostgreSQL-dagi DISTINCT kalit so’zi SELECT bayonotining natijalar to'plamidan dublikatlarni olib tashlash uchun ishlatiladi. U SELECT roʻyxatidagi barcha ustunlarni taqqoslaydi va barcha ustunlarda bir xil qiymatga ega boʻlgan qatorlarni yoʻq qiladi.

SYNTAX:
```sql
SELECT DISTINCT column1, column2
FROM table_name;
```
Bu kodning natijasidan table_name ya’ni bu siz bergan table dan ichidagi ikkita column distinct qilib qaytaradi ya’ni dublikatlarni (bir necha marta qaytarilgan qiymatlarni) yo'qotadi.

Misol:
Keling, quyidagi ma'lumotlarga ega "xodimlar" nomli jadvalni ko'rib chiqaylik:
id | name   | salary
---|--------|-------
1  | John   | 50000
2  | Jack   | 55000
3  | John   | 60000
4  | Emily  | 65000
5  | Jack   | 70000

"Xodimlar" jadvalidan  (distinct) nomlar ro'yxatini olish uchun biz quyidagi so'rovdan foydalanishimiz mumkin:
```sql
SELECT DISTINCT name FROM employees;
```

Natija:
```
|name|  
-----
| John |
| Jack |
| Emily |
```
Xulosa qilib aytganda, PostgreSQL-dagi DISTINCT kalit so'zi jadvaldan qaytarilmas qiymatlarni olish uchun foydali vositadir. U bir yoki bir nechta ustunlar bilan ishlatilishi mumkin va natija to'plamidan dublikatlarni olib tashlaydi. Biroq, undan oqilona foydalanish kerak, chunki u katta ma'lumotlar to'plamlari bilan foydalanilganda so'rovlar ishlash tezligiga ta'sir qilishi mumkin.
