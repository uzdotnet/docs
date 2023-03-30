# Unit Test

Unit testlar yuqori sifatli .NET dasturlar yaratishning ajralmas qismi. Unit Test bu dasturni eng kichik komponentlarini ajratib olgan olda ularni to’g’ri ishlashini tekshirish. Bu komponentchalar odatda juda kichik va mustaqil bo’ladi. Ular birgalikda katta dasturni tashkil qiladi. Ushbu kichik komponent va qismlarni ajratib olib test qilish orqali ulardagi hatoliklar juda erta aniqlanadi va bu o’z navbatida katta vaqt va pul tejalishiga olib keladi.

Ushbu maqolada .NET dasturlar uchun unit testing asoslarini, unit testlarni qanday va nega yozilishi kerak ekanini o’rganamiz.

## `Unit Test`lar nega kerak?

Unit test juda ham muhim chunki ular defetlarni development siklining erta boshqichlarida aniqlashga yordam beradi. Unit test yozish orqali komponentdagi xatolarni bu komponentlar sistemani boshqa qismlariga ulanishidan oldin aniqlash mumkin. Bu juda ham katta vaqt va mablag’ tejaydi, sababi xatolarni komponentlar sistemaning boshqa qismlariga integratsiya qilinishdan avval aniqlash va tuzatish ancha osonroq.

Bundan tashqari unit testlar kodni modular bo’lishini ta’minlaydi. Kodni kichik komponentlarda mustaqil shaklda yozish uni keyinchalik kengaytirish va yangi featurelar osonlikcha qo’shish imkonini beradi. 

## `Unit Test`lar qanday yoziladi?

**.NET**da unit testlar **MSTest**, **NUnit** yoki **xUnit** kabi test freymvorklar orqali yoziladi tushiriladi. Ushbu freymvorklar unit testlar yozish va ishga tushirish uchun kerakli **tool**lar bilan ta’minlaydi. 

**Unit Test** yozish quyidagi qadamlardan iborat:

1. Test qilayotgan kodingiz mohiyatini tushinish: Unit Test yozishdan avval siz testlayotgan *method*, *funksiya* yoki *klas* aynan qanday ishlashi kerakligini avval bilishingiz kerak. Kod qanday ishlashi, *input* va *output*lar haqida to’liq ma’lumotga ega bo’lishingiz kerak.
2. Testni yozish: Nimani testlashni aniqlashtirib olgandan keyin test yozishni boshlasangiz bo’ladi. Unit Test odatda 3 qismdan iborat bo’ladi: **Tartiblash**, **Harakat**, **Tasdiqlash** *(Arrange, Act, Assert).*
    1. Tartiblash qismida test uchun kerak bo’ladigan obyekt va ma’lumotlar tayyorlanadi. 
    2. Harakat qismida esa test qilinayotgan funksiya yoki method chaqiriladi. Ya’ni test qilinayotgan kod ishga tushiriladi.
    3. Tekshirish qismida olingan natija kutilgan natijaga to’g’ri kelish kelmasligi tekshiriladi.

Quyidagi xUnit freymvork orqali kichik unit test misoli keltirilgan:

```csharp
using Xunit;

public class CalculatorTests
{
    [Fact]
    public void Add_WithPositiveNumbers_ReturnsCorrectSum()
    {
        // Arrange
        var calculator = new Calculator();
        int a = 2;
        int b = 3;
        
        // Act
        int result = calculator.Add(a, b);
        
        // Assert
        Assert.Equal(5, result);
    }
}

public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```

Yuqoridagi `Caculator` klasining bitta `Add` methodi bor. U ikkita son qabul qiladi va ularni yig’inidisini qaytaradi. Shu klasga yozilgan unit testni yuqorida ko’rishingiz mumkin.

`Add_WithPositiveNumbers_ReturnsCorrectSum` degan methodga ega `CalculatorTests` klasini yaratamiz. **Arrange** qismida `Calculator` klasidan obyekt yaratib olamiz. Keyin esa `a` va `b` inputlarni tayyorlaymiz. **Act** qismida `Add` methodini chaqirimiz. Natijani **Assert** qismida biz kutganday **5** ga teng ekanini tekshiramiz.

<aside>
💡 Test method ekanini anglatib turuvchi `[Fact]` atribyutiga e’tibor bering.

</aside>

## `Best Practice`lar

### 1. Alohida ajratilgan testlar yozish

Har bir unit test faqatgina bitta funksiyani testlashi kerak. Testlash jarayonida sistemaning testlanayotgan qismidan boshqa qismiga bog’liq bo’lmasligi shart. Bu testlarni izolatsiya qilishga va hatolarni tezroq topishga yordam beradi.

### 2. Ma’noli nomlar berish

Test klaslar va metodlarga ma’noli nomlar berish kerak. Bu orqali kod tushinarliroq bo’ladi va boshqa dasturchilar test ichida bemalolroq navigatsiya qilishadi.

### 3. Test freymvorklar ishlatish

Unit Testlar yozish va ularni ishga tushirish uchun MSTest, xUnit va NUnit kabi freymvorklardan foydalaning. Ushbu freymvorklar test yozish va uni ishga tushirishga kerakli qurilmalar bilan ta’minlaydi. Bunday tashqari ular test natijalari haqida reportlar va kodning qancha qismi testlar bilan qoplanganini ko’rsatib turadi.

### 4. Mock va Stub’lar ishlatish

Stub va mocklar orqali testlanayotgan kodni izolatsiya qilish va boshqa dependency larni simulatsiya qilish mumkin. Buning yordamida faqatgina testlanayotgan qism haqida qayg’urib boshqa dependencylarni shunchaki simulatsiya qilinadi. 

### 5. Hamma holatlarni testlash

Kodning har yo’lini testlashga harakat qiling. Bunga xato chiqishi mumkin bo’lgan barcha holatlar, edge case’lar va inputning barcha possible variantlari kiradi. 

### 6. Readable test yozish

Siz yozgan boshqalar uchun ham tushinarli bo’lishi uchun nomlashga va tushinarsiz qismlarga koment yozib chiqishga e’tibor bering. Teslanayotgan funksiya va testdan kutilayotgan natija nima ekani testni o’qiganda aniq bo’lishi kerak.

Hulosa qilib aytganda zomaniy dasturlarni yaratilish jarayonini Unit Testlarsiz tasavvur qilib bo’lmaydi. Har bir .NET dasturchi o’zining toolsetiga Unit Testing ko’nikmalarini qo’shib qo’yishi uning sifatli kod yozishiga yordam beradi.
