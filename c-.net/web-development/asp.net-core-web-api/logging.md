---
description: Muhammad Xodjayev
---

# Logging

**.NET’da log**  qilish (qayd qilish) oson ishlardan biri albatta. Lekin undan to’g’ri foydalana olish bu sizning darajangizni ham aniqlab berishi mumkin. Log qilishda ehtiyot bo’lish kerak, lekin qanday? Bugun **ILogger**  o’zi nima va qayerdan kelib qolyapti, uni qayerda va qanday holatda ishlatsak bo’ladi shularni batafsil ko’rib chiqamiz, kettik!

----------

### ILogger nima?

**ILogger — Microsoft.Extensions.Logging**  dan keladigan interface. U bizga **.NET’da**  oson yo’l bilan log qilishimizga imkon beradi.  **Dependency Injection (DI)** orqali biz ILogger’ni ishlatmoqchi bo’lgan Class’imizga Inject ya’ni ichiga kirg’izamiz:

```
using Microsoft.Extensions.Logging

public class MyService(ILogger<MyService> logger)
{
	public void DoWork()
    {
        logger.LogInformation("Doing work at {Time}", DateTime.UtcNow);
    }
}
```
----------

### Logging levels (Qayd qilishning darajalari)

_6 ta Log qilish darajasi (KETMA-KETLIKDA) bo’lib ular quyidagilar:_

-   **Trace**
-   **Debug**
-   **Information**
-   **Warning**
-   **Error**
-   **Critical**

----------

### Trace

**_Детальный_**  ma’lumotlarni qayd qilish uchun. Odatda  **debug** qilinayotganda yoki software qurilayotganda ishlatilinadi. Masalan har bir funksiya ishga tushganda uni ishga tushganini va nima parameter’lar bilan ishga tushganini qayd qilish:

```
logger.LogTrace("ProcessData metodi ishga tushyapti. Parameterlari: {Parameter1}, {Parameter2}", param1, param2);
```
----------

### Debug

**Log** qilishning bu darajasiham  **Trace’ga** o’xshab ketadi ya’ni biroz kamroq  **_детальный_**  ma’lumotlar bo’ladi ammo buniham  **debug** va dastur ishlab chiqarilayotganda ishlatilinadi.
```
logger.LogDebug("{Username} uchun user authentication boshlandi.", username);
```
----------

### Information

**Information** darajasi bo’lsa  **Trace** va  **Debug’dan** farqli o’laroq, umumiy ishlar natijasi uchun ishlatsak bo’ladi. Ya’ni  **детальный**-**детальный** ma’lumotlarni chiqarmasdan, umumiy masalan biror-bir ish bajarilib bo’lgandan so’ng ish yakunlanganini qayd qilib qo’yish uchun ishlatsak maqsadga muvofiq bo’ladi.
```
logger.LogInformation("{UserId} miqdordagi to'lov {Amount} uchun muvaffaqiyatli to'landi.", userId, amount);
```
----------

### Warning

**Warning** — qachonki kutilmagan voqea sodir bo’lsa, ogohlantirish ya’ni  **warning** darajasini ishlatsak bo’ladi. Masalan xotirada joy kam qolganini:
```
logger.LogWarning("{ServerId} mana shu server'da joy kam qolyabdi. Faqatgina {FreeSpace} GB joy qoldi!", serverId, freeSpace);
```
----------

### Error

**Error** — biror bir jiddiy voqea sodir bo’lsa-yu lekin dastur o’zini o’zi tiklay olib dastur ishlashdan to’xtamasa ishlatsak bo’ladi. Bu dasturni to’xtatmaydigan ammo e’tibor berishimiz majbur bo’ladigan voqea uchun ishlatilinadi.
```
logger.LogError(ex, "{UserId} uchun to'lov amalga oshirilayotganda muammoga duch kelindi. Exception: {ExceptionMessage}", userId, ex.Message);
```
----------

### Critical

**Bu qayd qilishning eng cho’qqisidagi daraja bo’lib, serverda xatolik yuz bersa, dastur ishdan chiqib ketsa (poyezd relsdan chiqib ketsa) va dastur qayta ishga tushirilishini talab qilsa ushanda ishlatilinadi.**
```
logger.LogCritical("Dastur ishga tushmadi. Configuration fayl topilmadi.");
```
----------

## Qayd qilishni sozlash

Biz qanday hohlasak shunday  **Log** (qayd) qilish imkoniyatlari bor, masalan faqatgina ma’lum bir  **Log Level’lar** qaydnomaga yoziladi. Va buni mana bunday amalga oshiramiz:

**Program.cs'da:**
```
builder.Logging.SetMinimumLevel(LogLevel.Warning); // Faqatgina Warning va undan baland bo'lgan qaydlar
```

Bu yerda biz  **SetMinimumLevel** ni ichiga qaysi  **Log Level’dan** yuqori bo’lgan qayd qilinishlarni beramiz. Agarda  **Warning** bersak undan yuqorilaridagilar chiqadi,  **Trace** bersak barchasi chiqadi chunki  **Trace** birinchi darajali qayd qilish hisoblanadi.

----------

## Diqqat!

E’tibor bergan bo’lsangiz log qilayotganimda **string interpolation’ga**  o’xshab ketadigan  **sytnax** ishlatdim ammo boshida  **$** mana bu belgi yo’q. O’ylagandursiz xato qilgan bo’lsa keraak deb, ammo hech ham unday emas.

Bunday formatda o’zgaruvchilarni qayd qilib ketsak keyin masalan  **Azure’da** shunday xizmatlar borki ular bilan mana shu  **{}** ni ichidagi nom bilan  **filter** qilib osonlikcha topib olsak bo’ladi. Agarda  **$**  bu belgi bilan  **string interpolation**  qiladigan bo’lsak, unday qilib  **filterlay** olmaymiz.

----------

## Diqqat #2

1.  **_Hamma narsani Information yoki Error qilib Log (qayd) qilavermang! Aniq-tiniq hamma narsani joyida ishlating!_**
2.  **_Hech qachon parollar, bank kartasi raqamlari, yoki shaxsiy ma’lumotlarni qayd qilmang!_**
3.  **_String interpolation o’rniga placeholder {} larni ishlating!_**

----------

### Shu Log (qayd) qilishlarni yaxshilab o’rganib olsak, anchagina debug-friendly (debug qilishga oson bo’lgan) dasturlarni qura olamiz.

----------

**_Xurmat bilan,_**

**_Muhammad Xodjayev._**
