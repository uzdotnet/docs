---
description: Xushnazarov Faxriddin
---

# Base

**base** kalit so’zini ishlatishni o’ragtish uchun biz ushbu maqolamizda Vorislik mavzusida yozgan maqolamizni davom ettiramiz.
```csharp
class Person
    {
        public string Name { get; set; }

        public Person(string name)
        {
            Name = name;
        }
        public void Display()
        {
            Console.WriteLine(Name);
        }
 }
	class Employee : Person
    {
        public string Company { get; set; }
        public Employee(string name, string company)
            : base(name)
        {
            Company = company;
        }
    }
```
Person sinfi Name xususiyatini o'rnatadigan konstruktorga ega. Employee sinfi Name xususiyatini voris qilib olganligi va o'rnatganligi sababli, o'rnatish kodini qayta qayta yozmasdan qandaydir tarzda Person sinfining tegishli kodini yozish mantiqan to'g'ri bo'ladi. Bundan tashqari, tayanch sinf konstruktorida o'rnatilishi kerak bo'lgan yana bir qancha xususiyatlar va parametrlar bo'lishi mumkin.
	**base** kalit so’zi yordamida biz tayanch sinfga murojaat qilishimiz mumkin. Bizning holatimizda "Employee" sinfining konstruktorida ism va kompaniyani belgilashimiz kerak. Ammo biz o'rnatish uchun ismni tayanch sinfning konstruktoriga, ya'ni Person sinfining konstruktoriga base(name) ifodasi yordamida uzatamiz.
```csharp
static void Main(string[] args)
{
    Person p = new Person("Bill");
    p.Display();
    Employee emp = new Employee("Tom", "Microsoft");
    emp.Display();
    Console.Read();
}
```
Konstruktorlar voris olayotganda voris sinfga o'tmaydi. Va agar tayanch sinfda kelishuv bo'yicha parametrsiz konstruktor aniqlanmagan, faqat parametrlarga ega bo'lgan konstruktorlar aniqlangan (Person bazaviy sinfda bo'lgani kabi) bo’lsa, u holda hosilaviy sinfda biz ushbu konstruktorlardan birini base kalit so'z yordamida chaqirishimiz kerak. Masalan, Employee sinfidan konstruktorni olib tashlimiz:
```csharp
class Employee : Person
    {
        public string Company { get; set; }
    }
```
Bu holda xatolik yuz beradi, chunki "Employee" sinfi "Person" sinfiga to'g'ri kelmaydi, ya'ni u tayanch sinfning konstruktorini chaqirmaydi. Agar bir xil xususiyatlarni o'rnatadigan biron bir konstruktorni qo'shsak ham, xatolik yuz beradi:
```csharp
    public Employee(string name, string company)
    {
        Name = name;
        Company = company;
    }
```
Ya'ni, Employee sinfida **base** kalit so'z orqali Person sinfining konstruktori oshkor ravishda chaqirilishi kerak:
```csharp
public Employee(string name, string company)
: base(name)
{
Company = company;
}
```
