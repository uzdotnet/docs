---
description: Xondamir Abduxoshimov
---

# Deployment

Shu mavzugacha bo'lgan davrda, dasturimizni faqatgina **localhost** da yurgazib keldik. Albatta bu dasturni tuzish davomida eng yaxshi yo'l hisoblanadi. Lekin dasturimiz ishlab turishi uchun, doimiy serverga joylashimiz lozim. 

ASP.NET Core dasturlarini support qiluvchi bir nechta cloud serverlar mavjud. Xususan: _Microsoft Azure_, _AWS\(Amazon Web Server\)_, _Microsoft IIS server_, _Heroku_ va h.k. 

Ushbu suxbatimiz davomida yaratgan botimizni Herokuga Windows OS tizimida deploy qilishni ko'rib chiqamiz.

## **Ilk qadam**:

* Herokudan ro'yxatdan o'ting:  [link](https://signup.heroku.com/)
* Git control tizimni yuklab, o'rnating: [link](https://git-scm.com/download/win)
* Heroku CLI\(Command Line Interface\) ni yuklab, o'rnating: [64 bit](https://cli-assets.heroku.com/heroku-x64.exe), [32 bit](https://cli-assets.heroku.com/heroku-x86.exe)

## **Asosiy qism:**

### CMD\(Command Prompt\) ni yurgazing

Foydalanayotgan OS da teminalni oching. Deploy qilmoqchi bo'lgan loyiha turgan joyga o'tish uchun **cd** buyrug'idan foydalaning.

```bash
cd loyiha_path
```

### Gitni initsalizatsiya qilish

Ushbu loyihani git repository sifatida lokal holatda initsalizatsiya qilish uchun quyidagi buyruqdan foydalaning

```csharp
git init
```

### Lokal repository hosil qilish

Loyihadagi barcha fayllarni lokal repository ga joylang.

```csharp
git add .
```

### Commit yozish

Yuklagan fayllaringiz uchun commit ham yozishingiz mumkin

```csharp
git commit -m "Herokuga botni deploy qilish"
```

### Heroku profilga bog'lanish

Yuqoridagi holatlardan so'ng loyiha fayllari lokal repository ga joylandi. Endi ularni herokuga o'tkazish uchun shaxsiy profilingizga bog'laning

```csharp
heroku login
```

![](../../../.gitbook/assets/image%20%2856%29.png)

Klaviaturadan biror-bir keyni bosing va sizda ushbu oyna ochiladi.

![](../../../.gitbook/assets/image%20%2842%29.png)

**Log in** tugamasini bosib o'zingizni profilingizga ulangandan so'ng, quyidagicha holat yuz beradi.

 

![](../../../.gitbook/assets/image%20%28102%29.png)

![](../../../.gitbook/assets/image%20%2868%29.png)

### Herokuda yangi app hosil qilish

Loyiha fayllarni herokuga yuklash uchun, yangi app hosil qiling.

```csharp
heroku create app_nomi
```

Agarda app ga berilgan nom unique bo'lsa quyidagicha ko'rinish taqdim etiladi.

![](../../../.gitbook/assets/image%20%2831%29.png)

![](../../../.gitbook/assets/image%20%2895%29.png)

app yaratilgandan keyin yuqoridagi oynada ko'rinish beradi.

### Yaratilingan app ga build pack o'rnatish

Herokuda to'g'ridan to'g'ri ASP.NET Core ga support yo'q. Shuning uchun uni qo'shimcha buildpack orqali qurish kerak. BuildPack ni o'rnatish uchun. Yaratgan app ichki parametrlaridan **settings** bo'limiga o'ting. 

![](../../../.gitbook/assets/image%20%2854%29.png)

Settings bo'limidan **Add buildPack** tugmasini toping.

![](../../../.gitbook/assets/image%20%2816%29.png)

Build pack qo'shish uchun, tugmani bosing va  [https://github.com/jincod/dotnetcore-buildpack](https://github.com/jincod/dotnetcore-buildpack) ushbu linkni keltirilgan oraliqqa joylashtirib, **Save changes** tugmasini bir marta chertib qo'ying.

![](../../../.gitbook/assets/image%20%2852%29.png)

### Yaratilingan appni remote qilish

Build pack o'rnatilgandan so'ng appni remote qiling.

```csharp
heroku git:remote -a app_nomi
```

![](../../../.gitbook/assets/image%20%2844%29.png)

### Appni herokuga yuklash

Endi fayllarni herokuga push qiling.

```csharp
git push heroku master
```

![](../../../.gitbook/assets/image%20%2896%29.png)

Demak, dasturimiz muvaffaqiyatli herokuga deploy qilindi. Sizga taqdimi etilgan https://app\_nomi.herokuapp.com/ domainida dastur ishga tushirilda. Endi botdan hamma foydalanishi mumkin.

Heroku serverini free holatda foydalansangiz, sizga 500 mb joy va har oy 550 soat taqdim etilinadi.

