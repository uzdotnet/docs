---
description: Muzaffar Nurillayev
---

# Constraint (cheklov) lar

Dasturlash sohasida hamma narsa aniqlik asosida qurilgan, ya'ni ma'lum bir chegaradan chiqib ketsak noaniqlik kelib chiqadi Compile-time yoki Run-time errorlar kelib chiqadi va bu bilan biz ishlatyotgan texnologiya bizga o'zi chizib qo'ygan aniq o'lchovlar va qadriyatlarni eslatib qo'yadi. 

Bu bir tomondan o'zimizga juda foydali, albatta tartib bor joyda natija kutilganidek bo'ladi.

Masalan, int turidagi o'zgaruvchiga string turidagi ma'lumotni o'zlashtirib bo'lmaydi, boolga decimalni va hokazo.

Database bilan ishlash ham xuddi shunga o'xshaydi va siz allaqachon o'z database'laringizda ma'lum cheklovlar yaratib bo'lgansiz. Ya'ni har doim table yaratyotganda biz uning column (ustunlari) qanaqa turdagi ma'lumot saqlashini belgilab berganmiz. Bu ham bir cheklovdir ya'ni endi ushbu ustunlarga umuman boshqa turdagi ma'lumotni saqlash imkonsizdir. 

Bulardan tashqari qo'shimcha cheklovlar ham kirita olamiz. Bu database'dagi ma'lumotlarning aniqligi va ishonchliligini ta'minlaydi.

Ikki xil darajadagi cheklovlar mavjud:

* Ustun darajasidagi;
* Table darajasidagi;

Ustun darajasidagi cheklovlar faqat bitta ustunga qo'llaniladi, jadval darajasidagi cheklovlar esa butun jadvalga qo'llaniladi. (masalan, ustun uchun ma'lumotlar turini belgilash aynan o'sha ustunga tegishli va ustun darajasidagi cheklov).

Quyida PostgreSQL'da keng tarqalgan cheklovlar:

* NOT NULL - ustun NULL qiymatiga ega bo'lmasligini ta'minlaydi.
* UNIQUE - ustundagi barcha qiymatlar takrorlanmas bo'lishini ta'minlaydi.
* PRIMARY KEY - ma'lumotlar bazasi jadvalidagi har bir qatorni/yozuvni o'ziga xos bo'lishini belgilaydi.
* FOREIGN - boshqa jadvallardagi ustunlar bilan bog'liqliligini tekshiradi.
* CHECK - ustundagi barcha qiymatlar ma'lum shartlarga javob berishini ta'minlaydi.
* EXCLUSION cheklovi – EXCLUDE cheklovi belgilangan operator(lar) yordamida belgilangan ustun(lar) yoki ifoda(lar)dagi ikkita satr solishtirilsa, bu taqqoslashlarning hammasi ham TRUE qiymatini qaytarmasligini ta’minlaydi (batafsil tushuntiraman)


## NOT NULL:
Biz table'ga ma'lumot qo'shyotgan paytimizda faqat ma'lum birlariga qo'shsak qolganlarni by default NULL bo'ladi va xatolik bermaydi. Lekin biz buni xohlamasak va o'sha ma'lumotni kiritishni majburiy qilib qo'ysak endilikda biz table'ga ma'lumot qo'shyotganda ma'lum bir belgilangan ustunlarda qiymat bo'lishi majburiy bo'ladi.
```sql
CREATE TABLE student(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50) NOT NULL,
   age INT NOT NULL,
   address VARCHAR(50),
);
```
Bu table'da name va age ustunlariga qiymat berish majburiy, address'ga qiymat berish yoki bermaslik ixtiyoriy.

## UNIQUE:
Bu cheklov ma'lum bir ustunda bir xil qiymatlarga ega bo'lishiga yo'l qo'ymaydi.
```sql
CREATE TABLE student1(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50) NOT NULL,
   username VARCHAR(50) NOT NULL UNIQUE,
   address VARCHAR(50),
);
```
Endi student1 table'ga ikkita bir xil username'ga ega ma'lumot qo'sha olmaymiz.

## PRIMARY KEY:

Bu cheklovning ustun darajasidagi vazifasi yuqoridagi UNIQUE bilan bir xil, lekin bu cheklov bitta jadval uchun faqat 1 dona bo'ladi ya'ni student1'da bir vaqtning o'zida username'ni ham, name'ni ham UNIQUE qilish mumkin, lekin 1 ta ustunni PRIMARY KEY qildikmi endi boshqasini bunaqa qilolmaymiz.
```sql
CREATE TABLE student1(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50) PRIMARY KEY,
   username VARCHAR(50) NOT NULL UNIQUE,
   address VARCHAR(50)
);
```
Bunaqa so'rov xatodir va bizga bitta table'da faqat bitta PRIMARY KEY bo'lishini anglatadi.

## FOREIGN KEY:

Bu cheklov ustundagi qiymatlar boshqa jadvalning qaysidir qatorida ko'rsatilgan qiymatlarga mos kelishi kerakligini bildiradi. Ya'ni ikkita jadval bog'liqlik bo'yicha qiymat qo'sha olamiz faqat va ishlatish uchun references kalit so'zidan foydalanamiz.

```sql
CREATE TABLE course(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE student2(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50),
   username VARCHAR(50) NOT NULL UNIQUE,
   address VARCHAR(50),
   course_id INT references course(id)
);
```
Bu yerda student2 table'ga qiymat qo'shyotgan payt course_id mavjud bo'lgan kursniki bo'lishi kerakligi tekshiriladi. Agar mavjud bo'lmagan kursning id'sini qo'shadigan bo'lsak xatolik yuzaga keladi.



## CHECK:

Bu cheklov orqali ma'lum filter qo'yib o'shandan o'ta olsa qo'shilishini belgilab beramiz, ma'lumot kelyotganda qo'shish paytida tekshirib olamiz va shartni qanoatlantirsa qo'shamiz.
```sql
CREATE TABLE student3(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50),
   username VARCHAR(50) NOT NULL UNIQUE,
   age int CHECK(age > 5),
   course_id INT references course(id)
);
```
Endilikda biz table'ga age 6 dan kichik kirita olmaymiz.



## EXCLUDE:

Bu cheklov table darajasida amal qiladi. Va o'ziga true yoki false qaytaradigan statementlar qabul qiladi. Va shu statementlardan eng kamida bittasi false qaytarishi kerak.
```sql
CREATE TABLE student4(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50),
   username VARCHAR(50) NOT NULL UNIQUE,
   age int CHECK(age > 5)
   EXCLUDE using gist
   (name =, username !=)
);
```
Bunda agar oldingiz ma'lumotlar bilan solishtirganda name'lar teng bo'lsa username'lar teng bo'lmasligi kerak yoki username'lar teng bo'lsa name'lar teng bo'lmasligi kerak yoki ikkovi ham teng bo'lmasligi kerak. Ikkovi bir vaqtning o'zida teng bo'lsa xatolik yuzaga keladi.

Tepadagi query ishlashi uchun avvalo extension qo'shib olamiz:
```sql
 CREATE EXTENSION btree_gist;
```

Cheklovni olib tashlash ham mumkin:
```sql
ALTER TABLE table_name DROP CONSTRAINT cheklov;
```
