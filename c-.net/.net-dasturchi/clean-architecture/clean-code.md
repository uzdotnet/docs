---
description: Nodirbek Abdulaxadov
---

# Clean Kod

## Nomlash

**Qisqa nom ishlatishdan saqlaning**Yaxshi nom kodni ko'plab dasturchilar tomonidan ishlatishga imkon beradi. Nom nima qilayotganini aks ettirishi va kontekst berishi kerak.

**Yomon:**

```csharp
int n;
```

**Yaxshi:**

```csharp
int numberOfMembers;
```

**Adashtiruvchi nomlardan saqlaning**

O'zgaruvchini nima uchun ishlatilishini ko'rsatish uchun unga nom bering.

**Yomon:**

```csharp
var dataFromDb = db.GetFromService().ToList();
```

**Yaxshi:**

```csharp
var listOfEmployee = _employeeService.GetEmployees().ToList();
```

**Nomlashda izchillikka e'tibor bering**

Katta harflar sizga o'zgaruvchilar, funksiyalar va boshqalar haqida ko'p ma'lumot beradi. Siz qanday nom tanlashingizdan qat'iy nazar, nomlarning izchilligiga (bir xil qoida asosida) e'tibor bering. Xullas, bittasini katta harflarda, boshqasini kichkinada nomlab yurmang.

**Yomon:**

```csharp
const int DAYS_IN_WEEK = 7;
const int daysInMonth = 30;

var songs = new List<string> { 'Back In Black', 'Stairway to Heaven', 'Hey Jude' };
var Artists = new List<string> { 'ACDC', 'Led Zeppelin', 'The Beatles' };

bool EraseDatabase() {}
bool Restore_database() {}

class animal {}
class Alpaca {}
```

**Yaxshi:**

```csharp
const int DaysInWeek = 7;
const int DaysInMonth = 30;

var songs = new List<string> { 'Back In Black', 'Stairway to Heaven', 'Hey Jude' };
var artists = new List<string> { 'ACDC', 'Led Zeppelin', 'The Beatles' };

bool EraseDatabase() {}
bool RestoreDatabase() {}

class Animal {}
class Alpaca {}
```

**Tushunarli nomlardan foydalaning**

G'alati nomlarni vaqti kelsa o'zingiz ham tushunmay qolasiz.

**Yomon:**

```csharp
public class Employee
{
    public Datetime sWorkDate { get; set; } // G'irt tupoylik
    public Datetime modTime { get; set; }   // Bettayam shu
}
```

**Yaxshi:**

```csharp
public class Employee
{
    public Datetime StartWorkingDate { get; set; }
    public Datetime ModificationTime { get; set; }
}
```

**Camelcase dan foydalaning**

O'zgaruvchilar va metod parametrlari uchun [Camelcase Notation](https://en.wikipedia.org/wiki/Camel\_case) nomlashdan foydalaning.

**Yomon:**

```csharp
var employeephone;

public double CalculateSalary(int workingdays, int workinghours)
{
    // qandaydir kod
}
```

**Yaxshi:**

```csharp
var employeePhone;

public double CalculateSalary(int workingDays, int workingHours)
{
    // qandaydir kod
}
```

## O'zgaruvchilar

**Juda chuqurlashib ketmang**

Masalaga jiddiy qarab, if-else zanjirini ko'paytirib, chuqurlashtirib tashlamang. Oddiyroq kod bilan ham hal qilsa bo'ladi :)

**Yomon:**

```csharp
public bool IsShopOpen(string day)
{
    if (!string.IsNullOrEmpty(day))
    {
        day = day.ToLower();
        if (day == "friday")
        {
            return true;
        }
        else if (day == "saturday")
        {
            return true;
        }
        else if (day == "sunday")
        {
            return true;
        }
        else
        {
            return false;
        }
    }
    else
    {
        return false;
    }

}
```

**Yaxshi:**

```csharp
public bool IsShopOpen(string day)
{
    if (string.IsNullOrEmpty(day))
    {
        return false;
    }

    var openingDays = new[] { "friday", "saturday", "sunday" };
    return openingDays.Any(d => d == day.ToLower());
}
```

**Yomon:**

```csharp
public long Fibonacci(int n)
{
    if (n < 50)
    {
        if (n != 0)
        {
            if (n != 1)
            {
                return Fibonacci(n - 1) + Fibonacci(n - 2);
            }
            else
            {
                return 1;
            }
        }
        else
        {
            return 0;
        }
    }
    else
    {
        throw new System.Exception("Not supported");
    }
}
```

**Yaxshi:**

```csharp
public long Fibonacci(int n)
{
    if (n == 0)
    {
        return 0;
    }

    if (n == 1)
    {
        return 1;
    }

    if (n > 50)
    {
        throw new System.Exception("Not supported");
    }

    return Fibonacci(n - 1) + Fibonacci(n - 2);
}
```

**Ortiqcha logikadan foydalanmang**

Kimdir kodingizni o'qishi uchun o'rtada tarjimon bo'lib turishingiz kerak emas ;)

**Yomon:**

```csharp
var l = new[] { "Austin", "New York", "San Francisco" };

for (var i = 0; i < l.Count(); i++)
{
    var li = l[i];
    DoStuff();
    DoSomeOtherStuff();

    // ...
    // ...
    // ...
    // Wait, what is `li` for again?
    Dispatch(li);
}
```

**Yaxshi:**

```csharp
var locations = new[] { "Austin", "New York", "San Francisco" };

foreach (var location in locations)
{
    DoStuff();
    DoSomeOtherStuff();

    // ...
    // ...
    // ...
    Dispatch(location);
}
```

**"Sehrli" satrlardan foydalanmang**

"Sehrli" satrlar - bu dasturning ishlashiga ta'sir ko'rsatadigan, to'g'ridan-to'g'ri dastur kodida ko'rsatilgan satr qiymatlari. Ko'pincha, bunday satrlar kodda takrorlanadi va ularni avtomatik ravishda refaktoring asboblari yordamida yangilab bo'lmagani uchun, ba'zi satrlarga o'zgartirishlar kiritilganda, boshqalari o'zgarishsiz qoladi. Bu esa xatolarning keng tarqalgan manbaiga aylanadi.

**Yomon:**

```csharp
if (userRole == "Admin")
{
    // logic in here
}
```

**Yaxshi**

```csharp
const string ADMIN_ROLE = "Admin"
if (userRole == ADMIN_ROLE)
{
    // logic in here
}
```

_Bundan keyin bir o'q bilan bir nechta quyonni urish mumkin bo'ladi_ :)

**Keraksiz qo'shimchalarni qo'shmang**

Sinf yoki obyekt nomlarini o'zgaruvchilar nomlarida takrorlamang.

**Yomon:**

```csharp
public class Car
{
    public string CarMake { get; set; }
    public string CarModel { get; set; }
    public string CarColor { get; set; }

    //...
}
```

**Yaxshi:**

```csharp
public class Car
{
    public string Make { get; set; }
    public string Model { get; set; }
    public string Color { get; set; }

    //...
}
```

**Qidirsa bo'ladigan nomdan foydalaning (1-qism)**

Biz 5 minut yozgan kodimizni yillar davomida qayta-qayta o'qishimizga to'g'ri kelishi mumkin. Biz yozgan kod oson o'qilishi va qidirilishi juda muhim. Dasturimizni tushunish uchun ahamiyatli bo'lgan o'zgaruvchilarni nomlamasdan, biz kodni o'quvchilarni xunob qilamiz.

**Yomon:**

```csharp
// Betta data - qanaqa data o'zi???
var data = new { Name = "John", Age = 42 };

var stream1 = new MemoryStream();
var ser1 = new DataContractJsonSerializer(typeof(object));
ser1.WriteObject(stream1, data);

stream1.Position = 0;
var sr1 = new StreamReader(stream1);
Console.Write("JSON form of Data object: ");
Console.WriteLine(sr1.ReadToEnd());
```

**Yaxshi:**

```csharp
// mana bu Person modeli
var person = new Person
{
    Name = "John",
    Age = 42
};

var stream2 = new MemoryStream();
var ser2 = new DataContractJsonSerializer(typeof(Person));
ser2.WriteObject(stream2, data);

stream2.Position = 0;
var sr2 = new StreamReader(stream2);
Console.Write("JSON form of Data object: ");
Console.WriteLine(sr2.ReadToEnd());
```

**Qidirsa bo'ladigan nomdan foydalaning (2-qism)**

**Yomon:**

```csharp
var data = new { Name = "John", Age = 42, PersonAccess = 4};

// 4 nima ma'noni anglatadi???
if (data.PersonAccess == 4)
{
    // qandaydir kod ...
}
```

**Yaxshi:**

```csharp
public enum PersonAccess : int
{
    ACCESS_READ = 1,
    ACCESS_CREATE = 2,
    ACCESS_UPDATE = 4,
    ACCESS_DELETE = 8
}

var person = new Person
{
    Name = "John",
    Age = 42,
    PersonAccess= PersonAccess.ACCESS_CREATE
};

if (person.PersonAccess == PersonAccess.ACCESS_UPDATE)
{
    // qandaydir kod ...
}
```
