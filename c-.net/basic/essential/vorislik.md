---
description: Xushnazarov Faxriddin
---

# Vorislik

Vorislik \(inheritance\) Obyektga Yonaltirilgan Dasturlash\(OYD\)ning muhim tamoyillaridan biridir. Voris orqali bir sinf boshqa sinfning funksionalligini o’zlashtirishi mumkin, ya’ni voris sinflar umumiy xususiyatlarni vorislik bilan olgan holda, ayrim xususiyatlarni qayta aniqlash orqali yoki yangi xususiyat kiritish orqali tayanch sinfga o’gartirish mumkin. Shu sababli hosilaviy sinflarni aniqlash sezilarli ravishda kamayadi, chunki unga tayanch sinfdan farqli elementlar qo’shiladi. Aytaylik, bizda alohida shaxsni tavsiflovchi quyidagi Person sinfi mavjud:

```csharp
class Person
{
    private string _name;
    public string Name
    {
        get { return _name; }
        set { _name = value; }
    }
    public void Display()
    {
        Console.WriteLine(Name);
    }
}
```

Ammo korxona ishchisini tavsiflovchi sinf kerak bo’lib qoldi deylik - bu Employee sinfi. Ushbu sinf Person sinfi bilan bir xil funktsiyani amalga oshirishi sababli, xodim ham o'z navbatida shaxs bo'lganligi sababli, Employee sinfini Person sinfining vorisi \(yoki sinf osti\) ga aylantirish mantiqan to'g'ri bo'ladi. Bu sinf o’z navbatida ajdod \(yoki superklass\) tayanch sinf deb nomlanadi:

```csharp
class Employee : Person
{

}
```

Ikki nuqtadan keyin ushbu sinf uchun tayanch sinfni ko'rsatiladi. Person sinfi Employee sinfi uchun tayanch sinf hisoblanadi, va shuning uchun Employee sinfi Person sinfining barcha barcha xususiyatlarni, metodlarni, maydonlarni meros qilib oladi. Meros bo’lib o'tmaydigan yagona narsa bu tayanch sinfning konstruktorlari. Shunday qilib, Vorislik is-a munosabatini amalga oshiradi, Employee sinfining ob'ekti o’z navbatida Person sinfining ham ob'ekti hisoblanadi

```csharp
static void Main(string[] args)
{
    Person p = new Person { Name = "Tom" };
    p.Display();
    p = new Employee { Name = "Sam" };
    p.Display();
    Console.Read();
}
```

Employee sinfining obyekti o’z navbatida Person sinfining ham obyekti bo’lganligi sababli, o'zgaruvchini quyidagicha aniqlay olamiz :

```csharp
Person p = new Employee();
```

Kelishuv bo’yicha, Vorislik oshkor ravishda ko’rsatilmasa ham, barcha sinflar **Object** tayanch sinfining vorisi hisoblanadi. Shuning uchun ham, yuqorida keltirilgan Person hamda Employee sinflari o'zlarining metodlaridan tashqari, Ob'ekt sinfining quyidagi metodlariga ham ega: ToString\(\), Equals\(\), GetHashCode\(\) va GetType\(\). Kelishuv bo'yicha barcha sinflar voris qilib olinishi mumkin. Biroq, bu yerda bir qator cheklovlar mavjud: Person va Employee

* To’plamli vorislik qo'llanilmaydi, sinf faqat bitta sinfdan voris olishi mumkin.
* Hosilaviy sinfni yaratishda tayanch sinfning kirish kaliti ham hisobga olinilishi zarur, yani hosilaviy sinfning kirish kaliti tayanch sinfniki bilan bir xil bo’lishi yoki undanda cheklovliroq bo'lishi talab etiladi. Ya'ni, agar tayanch sinf **internal** kirish kalitiga ega bo'lsa, hosilaviy sinf \(voris sinf\) ham **internal** yoki **private** kirish kalitiga ega bo’lishi mumkin, lekin **public** kirish kalitiga ega bo’lishi bo’la olmaydi.

  Shuni hisobga olish kerakki, agar tayanch va hosilaviy sinflar har xil loyihalarda bo'lsa, unda hosilaviy sinf faqat public modifikatorga ega bo'lgan sinfdan voris olinishi mumkin.

* Agar sinf **sealed** modifikator bilan e'lon qilingan bo'lsa, u holda ushbu sinfdan voris olib bo’lmaydi. Masalan, quyidagi sinfdan voris olib bo'lmaydi:

  ```csharp
  sealed class Admin
  {
  }
  ```

* Statik sinfdan voris olib bo’lmaydi.

