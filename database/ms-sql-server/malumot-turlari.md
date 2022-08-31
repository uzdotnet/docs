---
description: Jahongir Temirov
---

# Ma'lumot turlari
{% hint style="info" %}
SQL Server kelajakdagi versiyasida ntext , text , va image ma'lumotlar turlarini olib tashlaydi. Shuning uchun siz ushbu ma'lumotlar turlaridan foydalanishdan qochishingiz kerak va o'rniga nvarchar(max) , varchar(max) va varbinary(max) ma'lumotlar turlaridan foydalaning
{% endhint %}

SQL tilida quyidagi ma'lumot turlari bor: 
1. Exact numerics:
* smallint
* int
* bigint
* tinyint
* bit
* decimal
* money
* numeric
* smallmoney
* tinyint
2. Approximate numerics:
* float
* real
3. Date and Time:
* date
* dateTime
* dateTime2
* dateTimeOffSet
* smallDateTime
* time
4. Character strings:
* char
* varchar
* text
5. Unicode Character strings:
* nchar
* nvarchar
* ntext
6. Binary strings:
* binary
* varbinary
* image
7. Other data types:
* cursor
* rowversion
* hierarchyid
* uniqueidentifier
* sql_variant
* xml
* Spatial Geometry Types
* Spatial Geography Types
* table

## Exact numerics
Ma'lumotlar bazasida bo'sh joyni tejash uchun barcha mumkin bo'lgan qiymatlarni ishonchli o'z ichiga oladigan eng kichik ma'lumotlar turidan foydalaning. Misol uchun, tinyint insonning yoshi uchun etarli bo'ladi, chunki hech kim 255 yoshdan ortiq yashamaydi. Ammo tinyint binoning yoshi uchun etarli bo'lmaydi, chunki binoning yoshi 255 yildan ortiq bo'lishi mumkin.

![Exavt numerics ©️ sqlservertutorial.net](https://user-images.githubusercontent.com/91861166/187736438-a45ef5b0-b3b3-440d-9374-9170777e8d91.png)

* Bit - 0/1/null oladi. Agar jadvalda 8 yoki undan kam bit ustunlar mavjud bo'lsa, ustunlar 1 bayt sifatida saqlanadi. Agar 9 dan 16 bitgacha bo'lgan ustunlar mavjud bo'lsa, ustunlar 2 bayt sifatida saqlanadi va hokazo. TRUE va FALSE qator qiymatlari bit qiymatlariga aylantirilishi mumkin: TRUE 1 ga, FALSE esa 0 ga aylantiriladi. 0 ga teng bo'lmagan har qanday qiymatni 1 deb oladi.
* decimal va numeric funksional bir xil (p[,s]) da ishlaydi. Precision(Aniqlik) va Scale(Masshtab).
P - saqlanishi kerak bo'lgan o'nlik raqamlar soni, 1 dan 38 gacha, default 18.
S - kasrning o'ng tomonida saqlanadigan raqamlar soni. 0 <= s <= p. default 0.

![decimal example](https://user-images.githubusercontent.com/91861166/187736126-d23b3632-a612-4d2b-8e30-f2446b31fb20.png)

![](https://user-images.githubusercontent.com/91861166/187736069-fcc666f6-0f71-4e94-94b6-e2d057f382d1.png)

Money va smallmoney ko'proq valyuta qiymatlari uchun ishlatiladi.

![Money & smallmoney shularni support qiladi.](https://user-images.githubusercontent.com/91861166/187735943-f61e285b-f900-4eec-9b5a-9819a2d14542.png)

## Approximate numeric
Taxminiy raqamlar ko'proq ilmiy hisoblarda ishlatiladi.

![Approximate numeric](https://user-images.githubusercontent.com/91861166/187734825-ee0eb89a-264a-46c6-86ea-cb2af5aa6f62.png)

* real - float bilan deyarli bir xil. ISO standartida real float(24); 
* float [ ( n ) ] Bu erda n - float raqamining mantissini ilmiy yozuvda saqlash uchun ishlatiladigan bitlar soni va shuning uchun aniqlik va saqlash hajmini belgilaydi. n 1 dan 53 gacha, deafault qiymati 53 dir . [1,24] uchun 24, [25,53] uchun 53 oladi.

## Date and Time types

![Date and Time types](https://user-images.githubusercontent.com/91861166/187734697-8bc06927-2a08-4bdf-a782-ebdeb2036ec4.png)

* date - standart string 'YYYY-MM-DD'. satr uzunligi 10 belgi. Default qiymati 1900-01-01. date faqat sanalatni oladi, vaqtni olmaydi.

{% hint style="info" %}
Yangi ishlaringizda time, date, datetime2 va datetimeoffset maʼlumotlar turlaridan foydalaning. Ushbu turlar SQL standartiga mos keladi. Ular ko'proq portativdir. time , datetime2 va datetimeoffset ko'proq soniya aniqligini ta'minlaydi. datetimeoffset global o'rnatilgan ilovalar uchun vaqt mintaqasini qo'llab-quvvatlaydi.
{% endhint %}
![Data types](https://user-images.githubusercontent.com/91861166/187734420-be61e941-602b-4262-9070-caf7002b083d.png)

* datetime -  standart string yo'q. 1 kun 00:00:00 dan 23:59:59.997 gacha. Default qiymati 1900-01-01 00:00:00. Millisekundlar 001 ga farq qilishi mumkin.
* datetime2 - kengroq sana diapazoni, kattaroq standart kasr aniqligi va ixtiyoriy foydalanuvchi tomonidan belgilangan aniqlikka ega bo'lgan mavjud sana turining kengaytmasi sifatida ko'rib chiqilishi mumkin .
Standart string YYYY-MM-DD hh:mm:ss[.fractional seconds].
1kun 00:00:00 dan 23:59:59.9999999 gacha.
19 belgidan max 27tagacha. E'lon qilishda millisekundlarni ixtiyoriy belgilashi mumkin. 0 dan 9999999 xonalari soniga qarab. datetime2(7).
Xotira: 3 dan kam aniqlik uchun 6 bayt. 3 yoki 4 aniqlik uchun 7 bayt. Boshqa barcha aniqliklar uchun 8 bayt kerak. Default qiymati 1900-01-01 00:00:00.
* datetimeoffset - Datetime2 kabi 24 soatlik soat asosida kunning vaqti bilan birlashtirilgan sanani belgilaydi va UTC (Umumjahon vaqt koordinatasi yoki Grinvich vaqti) asosida vaqt mintaqasi xabardorligini qo'shadi.
Standart string YYYY-MM-DD hs:dd:ss[.nnnnnnn] [{+|-}ss:mm].
26 belgidan max 34 tagacha.

Xotira:

![](https://user-images.githubusercontent.com/91861166/187734226-9d083c6e-b278-4409-b9ef-ddd4d5ee004a.png)

* smalldatetime - Kunning vaqti bilan birlashtirilgan sanani belgilaydi. Vaqt 24 soatlik kunga asoslanadi, soniyalar har doim nolga (:00) va kasr soniyalarsiz. Max belgi 19. Standart string yo'q. default 1900-01-01 00:00:00. Size: 4bite.
* time - Kunning vaqti qismi faqat, sanalar yo'q. Standart string hh:mm:ss[.nnnnnnn]. Default 00:00:00.

## Character strings
* Character strings typelari (char, varchar,text) Unicode bo'lmagan tarzda saqlaydigan datatype hisoblanadi. Ya'ni 1 belgi uchun 1 bayt ajratadi. VAR - VARYING - o'zgaruvchi ma'nosida.

![Character strings](https://user-images.githubusercontent.com/91861166/187733851-6bc7258a-b16d-496f-b973-3dd50698ffab.png)

* CHAR - max uzunligi 1 dan 8000 baytgacha. E'lon qilinishi char(n). Default 1.
Agar belgilangan o'lchamdan kam ma'lumot kiritilsa SQL unga bo'sh [" "] qo'shadi. So'raganingizda qaytarishdan oldin ularni olib tashlaydi. Uzun bo'lsa xato beradi.
* VARCHAR/VARCHAR(max) - max uzunligi 1 dan 8000 baytgacha. VARCHAR(max) uzunligi 2^31-1 bayt(2 GB,2,147,483,647). Xotirada n + 2 olishi mumkin.Bu o'zgaruvchan kenglikdagi belgilar qatori. Dinamic type hisoblanadi. CHAR kabi kam belgiga qo'shilmaydi.
* TEXT - varchar(max) kabi, xotirada n+ 4 oladi.

{% hint style="info" %}
Ustun ma'lumotlarining o'lchamlari bir xil bo'lganda char dan foydalaning .
Ustun ma'lumotlari yozuvlarining o'lchamlari sezilarli darajada farq qilganda varchar dan foydalaning .
Ustun ma'lumotlari yozuvlarining o'lchamlari sezilarli darajada farq qilganda va satr uzunligi 8000 baytdan oshib ketganda varchar(max) dan foydalaning.
{% endhint %}

## Unicode Character Strings
Bu typedagilar (nchar, nvarchar, ntext) saqlashda Unicode tarzda saqlaydi.1ta belgi uchun 2 bayt ajratadi. Belgilar boshidagi n harfi "National" ma'nosini beradi. Asosan boshqa tillar(japan, korea..)dagi belgilarni ham saqlaydi. Shuning uchun 2 baytdan ajratadi. Xotirada ham 2n oladi. Agar sizda bir nechta tillarni qo'llab-quvvatlaydigan saytlar bo'lsa ushbu type lardan foydalanganingiz yaxshi.

![Unicode character string data types](https://user-images.githubusercontent.com/91861166/187733528-7ca9cc1f-474b-48ed-a184-a6473a90c8d5.png)

* NCHAR - 1-4000 belgigacha, default 1.
* NVARCHAR(n)/NTEXT - n 1-4000 belgigacha, max - 2^30-1 byte(1,073,741,823). Default 1.

## Binary Strings
![Binary string data types](https://user-images.githubusercontent.com/91861166/187733351-d9411659-1127-4b02-b259-432751b893e1.png)

binary [ ( n ) ] n bayt boʻlgan qattiq uzunlikdagi ikkilik maʼlumotlar , bu yerda n 1 dan 8000 gacha boʻlgan qiymatdir. Saqlash hajmi n bayt.
varbinary [ ( n | max ) ] Oʻzgaruvchan uzunlikdagi ikkilik maʼlumotlar. n 1 dan 8000 gacha bo'lgan qiymat bo'lishi mumkin. max maksimal saqlash hajmi 2^31-1 bayt ekanligini ko'rsatadi. Saqlash hajmi - kiritilgan ma'lumotlarning haqiqiy uzunligi + 2 bayt. Kiritilgan ma'lumotlar uzunligi 0 bayt bo'lishi mumkin. 
image - 0 dan 2^31-1 (2,147,483,647) baytgacha bo'lgan o'zgaruvchan uzunlikdagi ikkilik ma'lumotlar.
## Other data types
![](https://user-images.githubusercontent.com/91861166/187733156-906bca90-2c2d-4926-9f53-357575b36b0f.png)
