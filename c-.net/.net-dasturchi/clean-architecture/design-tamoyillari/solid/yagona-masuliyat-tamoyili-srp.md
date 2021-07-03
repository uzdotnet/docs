---
description: Xondamir Abduxoshimov
---

# Yagona Mas'uliyat Tamoyili\(SRP\)

SOLID tamoyillari bilan tanishishni boshlaymiz. Birinchi navbatda **Yagona Mas'uliyat Tamoyili**, ya'ni **SIngle Responsibility Principle\(SRP\)**  to'g'risida suxbatlashamiz.

Tasavvur qiling siz bazm uyushtirmoqchisiz. Sizda bazm uchun olib kelinishi kerak bo'lgan narsalar ro'yxati bor va bu ishda sizga bir nechta do'stlaringiz yordam bermoqchi. Lekin siz vazifalarni do'stlaringiz o'rtasida aniq taqsimlab bermadingiz. Sababi, hamma bilsa kerak nima olib kelishini deb o'yladingiz. Afsuski bayram kuni ko'ribsizki, ko'pchilik bir xil narsa olib kelishgan. Demak, ishni taqsimlash jarayonida qandaydur kamchilik bo'lgan.

Oddiy hayotda bo'lgandek, dasturlashda ham SRP tamoyilini e'tiborsiz qoldirish ulkan muammolarni keltirib chiqarishi mumkin. Dasturning boshlanishida, yozilayotgan kod strukturasini boshqarish oson bo'lishi mumkin. Biroq, dastur kattalashgani va qilinadigan ishlar murakkablashgani sari, dasturni o'zgartirishda muammolar kelib chiqishi kuzatiladi.

### Yagona Mas'uliyat Tamoyili nima?

SRPni qo'llash bizga shuni eslatadiki, har bir modul yoki sinf yagona vazifani qilishga javob berishi kerak. 

{% hint style="info" %}
1 - qoida                                                                                              

**Sinfni o'zgartirish uchun faqat bitta sabab bo'lishi kerak**
{% endhint %}

Siz yaratgan sinf ichidagi metodlar yagona bir maqsad ostida birlashishi kerak. Endi yuqoridagi bitta sabab birikmasiga e'tibor qaratamiz.

Sizga mijoz dastur tuzib berishni iltimos qildi va siz taklifni qabul qilib, ishni boshladingiz. Bir yaxshi ishni qilib turgandiz, mijoz kelib sizga yana qo'shimcha ishlarni yuklab ketdi va bu sizni yaratib qo'ygan dasturizdagi sinflarni o'zgartirishga majbur qildi. Shoshib SRP qoidalarni esdan chiqardizda, mavjud sinflarga qo'shimcha mas'uliyat  yukladiz. Keyin yana mijoz keldi va sizga qo'shimcha bir dunyo qo'shilishi shart bo'lgan ishlarni aytib ketdi. Natijada siz sinflarga birdan ortiq mas'uliyat yuklaganingiz sababli, endi siz mavjud sinflarda bir emas, bir nechta o'zgartirishlarni kiritishingiz kerak. Bu esa yuqoridagi qoidani buzilishiga olib keladi. 

Endi SRPni qanday qo'llashni ko'rib chiqamiz.

#### 1 - misol

```csharp
public class Employee
{
    private String FirstName;
    private String LastName;
    private LocalDate HireDate;
    private HashSet<Employee> SubOrdinates;

    public Employee(String firstName, String lastName, LocalDate hireDate) {...}
    public void AddSubordinate(Employee subordinate) {...}
    public void RemoveAllSubordinates() {...}
    public void Print() {...}
}
```

Yuqorida **Employee** nomi bilan sinf e'lon qilinyabdi va unda bir nechta maydon va metodlar e'lon qilinyabdi:

* **Employee** - konstruktor, yangi kelgan ishchini yaratadi.
* **AddSubordinate** - Berilgan ishchiga yordamchi qo'shadi
* **RemoveAllSubordinates** - Berilgan yordamchidan barcha yordamchilarni o'chiradi.
* **Print** - Printerdan ma'lumotlarni chop etishga xizmat qiladi.

Ko'rib turganingizdek **Print** metodi Employee sinfiga ortiqcha mas'uliyat yuklamoqda. Nimaga desangiz, dasturda aynan shu servisni ishlatadigan boshqa toifaga mansub foydalanuvchilar ham bo'lishi mumkin.

### 2 - misol

```csharp
public class Account 
{
    public Double CalculateBalance() {...}
    public void Save() {...} 
}
```

Hisob kitob ishlarini ta'minlab beruvchi dasturimizda **Account** nomli sinf bor va 2 ta metoddan tashkil topgan:

* **CalculateBalance** - Tegishli userga mansub balansni hisoblab beradi
* **Save** - Hisoblarimizni bazaga saqlashga xizmat qiladi.

Buyerda Save metodi ortiqcha mas'uliyatni olib kelyabdi. SRPga amal qilish uchun, Save metodini alohida sinfga olib o'tishimiz lozim.

SRPni dasturda qo'llash, dasturingizni qanchalik tushunarli va toza\(clean\) bo'lishiga yordam beradi. 

