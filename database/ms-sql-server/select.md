---
description: Jahongir Temirov
---

# Select

Jadvaldagi ma'lumotlarni so'rash uchun siz **SELECT** bayonotdan foydalanasiz. Quyidagilar **SELECT** bayonotning eng asosiy shaklini ko'rsatadi:

```sql
SELECT select_list FROM schema_name.table_name;
```
Ushbu sintaksisda:

* Birinchidan, banddagi ma'lumotlarni so'ramoqchi bo'lgan vergul bilan ajratilgan ustunlar ro'yxatini belgilang.
* Ikkinchidan, manba jadvalini va uning sxema nomini FROM  bandda belgilang.

Bayonotni qayta ishlashda **SELECT**, SQL Server  **SELECT** so'rovda birinchi bo'lib paydo bo'lishiga qaramay, avval **FROM**, keyin esa **SELECT** qayta ishlaydi.

```sql
SELECT id,name FROM Students;
```

![SELECT ishlashi](https://user-images.githubusercontent.com/91861166/187829258-a6124246-0a0e-4cfd-a425-6819ab952a5d.png)

SELECT da "*" yordamida barcha column belgilash mumkin. Lekin bu har doim ham yaxshimas. Ba'zi xollarda dasturni sekinlashtiradi, keraksiz ma'lumotlarni oladi. 

SELECT tartibi
* FROM
* ON
* JOIN
* WHERE
* GROUP BY
* WITH CUBE or WITH ROLLUP
* HAVING
* SELECT
* DISTINCT
* ORDER BY
* TOP

Misollar:
```sql
SELECT *  FROM DimEmployee  ORDER BY LastName;
SELECT e.*  FROM DimEmployee AS e ;
SELECT FirstName, LastName, StartDate AS FirstDay  FROM DimEmployee;
SELECT FirstName, LastName, BaseRate, BaseRate * 40 AS GrossPay  FROM DimEmployee ;
SELECT DISTINCT Title  FROM DimEmployee  ORDER BY Title;
```
DISTINCT turli nomlarni qaytaradi. ORDER BY tartiblaydi.
