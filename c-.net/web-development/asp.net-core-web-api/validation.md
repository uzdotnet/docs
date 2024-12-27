---
description: Muhammad Khodjaev
---

# FluentValidation

Maqolani boshlashdan avval validatsiya o’zi nima ekanligi haqida bir og’iz:

> Validatsiya — bu, ma'lumotlarni saqlash yoki ishlashdan avval, belgilangan qoidalarga va cheklovlarga muvofiqligini tekshirish jarayonidir.

.NET’da ma’lumotlarni to’g’riligini tekshirishning (endi validatsiya deb yuritiladi) bir nechta yo’llari mavjud. Masalan ulardan biri bu [Data Annotation](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-aspnet-mvc3/cs/adding-validation-to-the-model?source=recommendations) [(batafsil:)](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-aspnet-mvc3/cs/adding-validation-to-the-model?source=recommendations). Va yana biri esa qo’shimcha package yordamida validatsiya qilish. Ushbu maqolada [Data Annotation](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-aspnet-mvc3/cs/adding-validation-to-the-model?source=recommendations) usuli bilan emas balki [FluentValidation (batafsil)](https://docs.fluentvalidation.net/en/latest/aspnet.html) package’i orqali validatsiyani amalga oshirishni ko’rib chiqamiz. Kettik!

----------

## Nega Data Annotation emas, Fluent Validation?

| Xususiyat                    | Fluent Validation                                                                                     | Data Annotation                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Sintaksis & O‘qishga qulayligi | Qiyin logikalar uchun oson, yaxshiroq o‘qiladi                                                       | Attribut orqali e’lon qilinadi                                                          |
| Testga oson/qiyinligi         | Unit test’lar uchun oson, chunki validatsiyalar qismi alohida klasslarda bo‘ladi                      | Test qilish uchun qiyinroq, chunki validatsiya qismlari alohida klassda emas balki Model class’ni o‘zida e’lon qilinadi |
| Qayta ishlatish mumkin yoki yo‘q | Beeemalol qayta ishlatsa bo‘ladi ya’ni validatsiya qismlari alohida klassda bo‘lganligi bois ularni turli xil project’lar-aro ishlatsak bo‘ladi | Modelda to‘g‘ridan-to‘g‘ri e’lon qilinganligi sababli, qayta ishlatish murakkabroq      |
| Xatoliklar haqida xabar berishi | O‘zimiz xohlagancha Error message’lar berishimiz mumkin                                            | Bazaviy (odatiy) error xabarlar.                                                        |


----------

# FluentValidation — ishni boshlaymiz

## Avval o’rnatib olamiz:

```bash
dotnet add package FluentValidation
```

## Validatorlar e’lon qilamiz

Bizga `AbstractValidator<T>`’dan meros oluvchi bitta class kerak bo’ladi va u class’ni ichiga ma’lumotlar uchun qoidalar/ma’lumotlar yozamiz. `AbstractValidator<T>` FluentValidation’dan keladi. Kettik:

```csharp
using FluentValidation;

public class UserValidator : AbstractValidator<User>
{
    public UserValidator()
    {
        RuleFor(user => user.Name)
            .NotEmpty()
            .WithMessage("Ismni kiritish majburiy!");

        RuleFor(user => user.Email)
            .EmailAddress()
            .WithMessage("Iltimos to'g'ri pochta manzilini kiriting!");

        RuleFor(user => user.Age)
            .InclusiveBetween(18, 60)
            .WithMessage("Yoshingiz 18 dan oshgan va 60 dan kichik bo'lishi kerak!");
    }
}
```

Demak `AbstractValidator<T>` ni ichiga biz cheklovlar o’rnatmoqchi bo’lgan Model Class’imizni nomini berib yuborar ekanmiz. Metodni ichida `RuleFor` kalit so’zi orqali turli-xil cheklovlar qo’ysak bo’ladi. `WithMessage()` orqali biz o’zimiz xohlagan error message’larni berib yuborsak bo’ladi. Aslida bermasak ham error message ko’rsatadi lekin o’zinikini ko’rsatadi ya’ni masalan “[user.Name](http://user.Name) mustn’t be null” bo’lishi mumkin.

## Ma’lumotni validator orqali tekshirish

Yuqorida ochgan class’imizga instance ochamiz va uni ichida `Validate()` degan method bor. Usha bilan ma’lumotimiz biz o’rnatgan qoidalarga tushadimi yo’qmi tekshiramiz:

```csharp
var user = new User { Name = "", Email = "invalid", Age = 17 };
var validator = new UserValidator();
var result = validator.Validate(user);

if (!result.IsValid)
{
    foreach (var error in result.Errors)
    {
        Console.WriteLine($"{error.PropertyName}: {error.ErrorMessage}");
    }
}
```

Demak `Validate()` method’i ichiga biz tekshirmoqchi bo’lgan ma’lumotlarimizni beramiz va uni biz o’rnatgan qoidalarga tushadimi yo’qmi tekshirib javobni `result` o’zgaruvchisiga solib qo’yadi. Uni ichida esa `isValid` bor va u `bool` qaytaradi. Agarda false bo’lsa demak biz o’rnatgan shartlar qanoatlantirilmagan bo’ladi. Tamom, Fluent Validation’ni oddiy ishlatilinishi shu qadar.

----------

# Fluent Validation’ni murakkabroq ishlatish

Yuqorida biz oddiy ishlatishni ko’rib chiqdik. U yerda bor narsalardan foydalandik ya’ni masalan:

```csharp
RuleFor(user => user.Name)
            .NotEmpty()
            .WithMessage("Ismni kiritish majburiy!");
```

Masalan bu yerda `.NotEmpty()` method’i o’zi bor va u string’ni bo’sh yoki yo’qligini tekshiradi. Lekin bizga murakkabroq tekshirishlar kerak, masalan string’imiz faqatgina katta harflardan tashkil topgan bo’lishi kerak bo’lsachi, nima qilamiz???

## Qoidalarga qoida qo’shish

Fluent Validation’ni ichida bor method’lardan tashqari o’zimiz ham qoidalar yozsak bo’ladi, albatta qoida yozish uchun ichidagi method’ni ishlatamiz 😃:

```csharp
RuleFor(user => user.Password)
    .NotEmpty()
    .MinimumLength(8)
    .Matches(@"[A-Z]").WithMessage("Parol faqatgina katta harflardan iborat bo'lishi shart!");

```

Bu yerda `.Matches` qilsak solishtiradi, agarda Matches shartiga tushmasa albatta bu `false` bo’ladi.

----------

```csharp
RuleFor(user => user.ConfirmPassword)
    .Equal(user => user.Password)
    .WithMessage("Parollar bir-biriga o'xshashi shart!");

```

Ma’lum bir ma’lumot boshqa ma’lumotga qaram bo’lishiham mumkin, masalan tasavur qiling yangi parol yozyapsiz va uni ikki martta yozasiz, ikkalasiham bir-biriga o’xshashi shart. Shunda ishlatsak bo’ladi.

----------

### Murakkabroq ishlatish — loyiha talabiga qarab o’zgarib ketaveradi. Ko’proq ma’lumot olish uchun albatta FluentValidation’ning rasmiy dokumentatsiyasini o’qib chiqishni qattiq tavsiya qilaman: [https://docs.fluentvalidation.net/en/latest/aspnet.html](https://docs.fluentvalidation.net/en/latest/aspnet.html**)

----------

**Xurmat bilan,**

**Muhammad Khodjaev**