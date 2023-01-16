---
description: (AlJavhar) Javohirbek Boyaliyev
---
# Inkapsulatsiya

"Inkapsulyatsiya" so'zi lotincha "in capsula" -  qobiqda joylashtirish so'zidan olingan. Shundan kelib chiqib inkapsulatsiyani izolyatsiyalash, atrof muhit ta'siridan himoya qilgan holda yopish, himoyalash, biror bir buyum, narsani qolib, kapsulaga solib qo'yish deb tushunish mumkin.

![](https://user-images.githubusercontent.com/91861166/212597878-c7ed3fd7-5a4e-4436-9da4-64983745bb9d.png)

Bu terminni saaaal dasturlashga bog'lab jaydaricha tushuntiradigan bo'lsak, o'zi inkapsulyatsiya dasturchilar o'z code larini boshqa dasturchilar tomonidan hurmat qilinishi va muhim qismlarini bilmasdan KATTA BUG gacham olib keladigan qilib o'zgartirib yubormasliklari uchun o'ylab topilgan QUROL!!!

![](https://user-images.githubusercontent.com/91861166/212598146-3da30f17-2f6d-47d7-a153-14ee396e88e4.png)

Endi ozmuncha bu masalaga ilmiy yondashamiz va bunga doir code ni ko'rib chiqamiz, shundan keyin ancha tushunarli bo'lib qoladi degan umididamiz.
Inkapsulyatsiyaning maqsadi - ob'ektning ichki holatini izchil bo'lishini ta'minlash. C# da inkapsulyatsiya uchun ob'ektning umumiy propertys (xususiyatlar) va methods (usullari) qo'llaniladi. Inkapsulyatsiyani oddiy misol bilan tasvirlash mumkin. Aytaylik, biz haqiqiy qiymatni va uning satr ko'rinishini saqlashimiz kerak (masalan, tez-tez foydalanilganda har safar konvertatsiya qilmaslik uchun). Buni avval Inkapsulyatsiyasiz amalga oshirish misolini ko'ramiz:

```csharp
class NoEncapsulation
    {
        public double ValueDouble;
        public string ValueString;
    }
```

Bu holatda biz Valuening o'zini ham, uning satr tasvirini ham alohida o'zgartirishimiz mumkin va ular qandaydir istisno holatida mos kelmay qolishligi mumkin. 

Endi huddi shu narsani Inkapsulyatsiya yordamida amalga oshirib ko'raylik, u holda:
```csharp
class EncapsulationExample
    {
        private double valueDouble;
        private string valueString;

        public double ValueDouble
        {
            get { return valueDouble; }
            set 
            {
                valueDouble = value;
                valueString = value.ToString();
            }
        }
```

```csharp
        public string ValueString
        {
            get { return valueString; }
            set 
            {
                double tmp_value = Convert.ToDouble(value); //здесь может возникнуть исключение
                valueDouble = tmp_value;
                valueString = value;
            }
        }
    }
```

Bu erda valueDouble va valueString o'zgaruvchilariga faqat ValueDouble va ValueString property (xususiyat)lari orqali kirish mumkin. Agar biz ValueString xususiyatiga yaroqsiz qatorni belgilashga harakat qilsak va konversiya vaqtida istisno yuzaga kelsa, u holda ichki o'zgaruvchilar bir xil, izchil holatda qoladi, chunki istisno protseduradan chiqishga sabab bo'ladi.
