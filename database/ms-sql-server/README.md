---
description: Jahongir Temirov
---

# MS SQL Server

{% hint style="info" %}
DBMS — Database Managment Systems

MBBT — Ma'lumotlar bazasini boshqarish tizimi
{% endhint %}

![Types of DBMS](https://user-images.githubusercontent.com/91861166/187606178-ff53ac5a-14fa-4714-9b05-fb633d62ed05.png)

Ma'lumotlarni qay tartibda saqlashga ko'ra 4 xil DBSM(MBBT) mavjud. Ierarxik, Relatsion, Tarmoq va Ob'ektga yo'naltirilgan relyatsion ma'lumotlar bazasi. Hozir faqat RDBMS (Relational DBMS) haqida

MB ning Relatsion modeli — Ma'lumotlarning jadval ko'rinishida berilishi ma'lumotlarning relyatsion modeli deyiladi. Relyatsion modelli MBdagi malumotlar oddiy ikki o'lchovli jadvallarda saqlanadi va jadvallar o'zaro bir-biri bilan bog'lanadi.
Bunga misollar: Oracle, MySQL, Microsoft SQL Server...

Bular ichidan hozirda Microsoft SQL Server bilan tanishamiz


## Microsoft SQL Server
Boshqa RDBMS dasturlariga kabi, SQL Server aloqa ma'lumotlar bazalari bilan o'zaro ishlash uchun standart dasturlash tili bo'lgan SQL ustiga qurilgan. SQL Server Transact-SQL yoki T-SQL bilan bog'langan, Microsoft kompaniyasining SQL dasturi bo'lib, u xususiy dasturlash konstruksiyalari to'plamini qo'shadi.

Microsoft va Sybase 1989 yilda 1.0 versiyasini chiqardilar. Biroq, bu ikkisi o'rtasidagi hamkorlik 1990-yillarning boshida tugadi. Microsoft SQL Server nomiga egalik huquqini saqlab qoldi. 1990-yillardan boshlab SQL Serverning keyingi versiyalari chiqarildi, jumladan SQL Server 2000, 2005, 2008, 2012, 2014, 2016, 2017 va 2019.

**SQL** Server 20 yildan ortiq vaqt davomida faqat Windows muhitida ishladi. 2016-yilda Microsoft uni Linuxda taqdim etdi. **SQL Server 2017** 2016-yil oktyabr oyida Windows va Linux tizimlarida ishlay boshladi.

**SQL — Structured Query Language(Strukturaviy so'rovlar tili)** — standartlashtirilgan dasturlash tili bo'lib, relyatsion ma'lumotlar bazalarini boshqarish va ulardagi ma'lumotlar ustida turli operatsiyalarni bajarish uchun ishlatiladi.

**SQL** — kompyuter MB da saqlanuvchi ma'lumotlarni qayta ishlash va o'qish uchun mo'ljallangan instrument bo'lib, u faqat relyatsion MB bilan ishlaydi. Barcha relyatsion MBBTlar SQL tilini tushunadi.

**T-SQL — Transact-SQL ( T-SQL )** Microsoft va Sybasening relyatsion ma'lumotlar bazalari bilan o'zaro aloqada bo'lish uchun ishlatiladigan SQL uchun xususiy kengaytmasi hisoblanadi.U o'zgaruvchini e'lon qilish, istisnolarni qayta ishlash, saqlangan protsedura va boshqalarni qo'shimcha imkoniyatlar bilan ta'minlaydi.

![SQL Server Architecture](https://user-images.githubusercontent.com/91861166/187606956-5ba8f9ea-4825-4998-87a6-dad57a6bf0f6.png)

![Database Engine](https://user-images.githubusercontent.com/91861166/187607090-3f3a689a-d44c-4f31-aa58-f824ccae2b4d.png)

SQL Server quyidagi komponentlardan iborat:

### Database Engine
SQL Serverning asosiy komponenti Ma'lumotlar Bazasi Mexanizmi (Database Engine) hisoblanadi. DBE so'rovlarni qayta ishlaydigan Aloqa Mexanizmi(Relational Engine) va ma'lumotlar bazasi fayllari, sahifalari, indekslari va boshqalarni boshqaradigan Saqlash Mexanizmi(Storage Engine)dan iborat. Saqlangan protseduralar , ko'rinishlar va triggerlar kabi ma'lumotlar bazasi ob'ektlari ham DBE tomonidan yaratiladi va bajariladi.

### Relational Engine
Relational Engine so'rovni bajarishning eng yaxshi usulini aniqlaydigan komponentlarni o'z ichiga oladi. Relyatsion vosita so'rovlar protsessori sifatida ham tanilgan.

Relyatsion vosita kirish so'rovi asosida saqlash mexanizmidan ma'lumotlarni so'raydi va natijalarni qayta ishlaydi.

Relyatsion mexanizmning ba'zi vazifalari so'rovlarni qayta ishlash, xotirani boshqarish, mavzu va vazifalarni boshqarish, buferni boshqarish va taqsimlangan so'rovlarni qayta ishlashni o'z ichiga oladi.

### Storage Engine
Saqlash mexanizmi disklar va SAN kabi saqlash tizimlaridan ma'lumotlarni saqlash va olish uchun javobgardir.

### SQLOS
Relyatsion vosita va saqlash mexanizmi ostida SQL Server operatsion tizimi yoki SQLOS mavjud.
SQLOS xotira va kiritish-chiqarish boshqaruvi kabi ko'plab operatsion tizim xizmatlarini taqdim etadi. Boshqa xizmatlarga istisnolarni qayta ishlash va sinxronizatsiya xizmatlari kiradi.
SQL Server Arxitekturasi haqida yana alohida to'xtalamiz.
Microsoft SQL Server bilan qo'shimcha Business Intelligence ni ham taqdim etgan.

------------------------------------------------------------------------------------------------------------------------------------------------
Ikki xil atama bor. SQL Server va SSMS. Ikkisi ham ikki xil narsa.

**SQL Server** bu ma'lumotlar bazasi, **SQL Server Management Studio (SSMS)** foydalanuvchi tomonidan SQL Server ma'lumotlar bazasiga  SQL so'rovlarini yozish va bajarish uchun ishlatilishi mumkin bo'lgan vosita.

**SQL Server** — ma'lumotlarni saqlaydigan va ularga so'rov qilish imkonini beruvchi ma'lumotlar bazasi mexanizmi. **SQL Server Management Studio** — bu SQL Server ma'lumotlar bazasi serverlari bilan ishlash uchun grafik interfeysni ta'minlovchi boshqaruv vositasi. Agar siz ma'lumotlarni saqlamoqchi bo'lsangiz, sizga faqat SQL Server kerak bo'ladi, agar siz ma'lumotlarni GUI vositasi bilan boshqarmoqchi bo'lsangiz, boshqaruv studiyasi ham kerak bo'ladi.

**SSMS** siz ham ishlasa bo'ladi, masalan VSCode ni extensioni bor, Visual Studioni o'zini oynasi mavjud, ular bilan be'malol ishlasa bo'ladi. Lekin "Chumchuq so'ysa ham qassob so'ysin" deganlaridek SSMS dan foydalangan yaxshi.

Yuklab olish uchun link: 

[SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)   
[SSMS](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)

## SQL Server Management Studio yordamida SQL Serverga ulanish

![Connect to Server](https://user-images.githubusercontent.com/91861166/187608395-fe8bdbb1-9a7f-416c-9406-89b5f7c40bb5.png)

Dasturga kirganimizda yuqoridagi oyna chiqadi. 

Dastlab Server turlarini tanlashimiz lozim:
1) Database Engine 
2) Analysis Services (SSAS) 
3) Reporting Services (SSRS) 
4) Integration Services (SSIS)
Bular barchasi jamlanib **Microsoft Business Intelligence (MBSI)** deyiladi.

**SSAS (SQL Server Analysis Service)** — bu ma'lumotlarni 3 o'lchamli formatda saqlash uchun ma'lumotlarni saqlash/ma'lumotlarni qazib olish muhitida foydalaniladigan vositadir.

**SQL Server Reporting Service (SSRS)** — MS-Word fayl formati, MS-Excel formati, .pdf formati, XML formati, .tiff fayl formati va boshqalar kabi turli xil hisobotlarni yaratish uchun foydalaniladigan vositadir. Hisobot biznes bilan bog'liq ba'zi ma'lumotlarni saqlash uchun foydalaniladigan hujjatdir.

**SQL Server Integration Service (SSIS)** — bu bitta ma'lumotlar bazasi jadvallarini boshqa ma'lumotlar bazasi tushunarli formatiga aylantirish uchun ishlatiladigan vosita. Masalan, SQL Server ma'lumotlar bazasi jadvallari Oracle tushunadugan jadval formatiga aylantirish.

**Server nomi**

![Connect to Server](https://user-images.githubusercontent.com/91861166/187608857-bcdfbde9-d534-4559-a80e-2488af0e962f.png)

Localda bo'lsa "<Browse for more...>" tanlanib komputerdagi serverlarni tanlashingiz mumkin. Odatda komputer nomi yoziladi.
Hostda esa qaysi serverdaligiga qarab yoziladi.

## Autentifikatsiya
Localdan foydalanilganida Windows tanlanadi, username va password OS ni o'zida bajariladi. Boshqa tarmoqdan foydalanilganda turiga qarab tanlashingiz mumkin.
Masalan: SQL Server Authonticationda host da Database ochganingizda Serverdagi username va password.

Connect. Hammasi tayyor.

![Main window](https://user-images.githubusercontent.com/91861166/187609297-fd2847ea-452d-466c-942b-0e86c9324109.png)

**New Query** dan yangi *.sql file ochiladi va biz unda query(so'rov) lar yozishimiz mumkin.
