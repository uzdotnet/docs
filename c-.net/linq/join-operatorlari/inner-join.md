---
description: Jasurbek Xasanboyev
---

# Inner Join
 ![image](https://user-images.githubusercontent.com/81855769/123627171-1d32e480-d82b-11eb-941a-443a3c13a3a8.png)

[To’plamlar](https://docs.dot-net.uz/c-.net/basic/yuqori-daraja/toplamlar) mavzusi orqali sizlar bilan C# dasturlash tilida to’plamlar qanday yaratilishi haqida gaplashgan edik. Avvalgi **LINQ** darslarda to’plam ustidagi amallarni ko’rib chiqqan edik. Endi esa bu mavzular asosan ikkita to’plam elementlarini birlashtirish haqida gaplashamiz.

**INNER JOIN** xuddi matematikada to’plamlar mavzusidan bizga tanish bo’lgan ikki to’plam birlashmasi kabi bo’ladi. Ya’ni ikki to’plamda ham mavjud elementlardan tashkil topadi: A = {1 , 2, 3, 4, 5}, B = {4, 5, 6, 7};  A ꓵ B = {4, 5}
{% hint style="info" %} Esda tuting! **INNER JOIN** ikkisida ham bor qism bo’yicha ikki to’plamni birlashtiradi. {% endhint %}
Query Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        var students = new List<Student>()
        {
            new Student() { Id = 1, Name = "Jasurbek", AddressId = 1},
            new Student() { Id = 2, Name = "Xondamir", AddressId = 1},
            new Student() { Id = 3, Name = "Shoxruh", AddressId = 3},
            new Student() { Id = 4, Name = "Shaxzod", AddressId = 4},
            new Student() { Id = 5, Name = "Abdulloh", AddressId = 2}
        };
        var addresses = new List<Address>()
        {
            new Address() {Id = 1, AddressLine = "Line 1"},
            new Address() {Id = 2, AddressLine = "Line 2"},
            new Address() {Id = 3, AddressLine = "Line 3"},
            new Address() {Id = 4, AddressLine = "Line 4"},
            new Address() {Id = 5, AddressLine = "Line 5"}
        };
        var QuerySyntax = (from student in students
                            join address in addresses
                            on student.AddressId equals address.Id
                            select new
                            {
                                StudentName = student.Name,
                                Line = address.AddressLine
                            }).ToList();
        foreach (var item in QuerySyntax)
        {
            Console.WriteLine($"Name: {item.StudentName} \tLine: {item.Line}");
        }
    /*OUTPUT: Name: Jasurbek  Line: Line 1
                Name: Xondamir Line: Line 1
                Name: Shoxruh Line: Line 3
                Name: Shaxzod Line: Line 4
                Name: Abdulloh Line: Line 2  */
    }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int AddressId { get; set; }
}
class Address
{
    public int Id { get; set; }
    public string AddressLine { get; set; }
}
```
Method Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        var students = new List<Student>()
        {
            new Student() { Id = 1, Name = "Jasurbek", AddressId = 1},
            new Student() { Id = 2, Name = "Xondamir", AddressId = 1},
            new Student() { Id = 3, Name = "Shoxruh", AddressId = 3},
            new Student() { Id = 4, Name = "Shaxzod", AddressId = 4},
            new Student() { Id = 5, Name = "Abdulloh", AddressId = 2}
        };
        var addresses = new List<Address>()
        {
            new Address() {Id = 1, AddressLine = "Line 1"},
            new Address() {Id = 2, AddressLine = "Line 2"},
            new Address() {Id = 3, AddressLine = "Line 3"},
            new Address() {Id = 4, AddressLine = "Line 4"},
            new Address() {Id = 5, AddressLine = "Line 5"}
        };
            var MethodSyntax = students.Join(addresses, std => std.AddressId,
                address => address.Id, 
                (std, address) => new {
                    StudentName = std.Name,
                    Line = address.AddressLine
                }).ToList();
        foreach (var item in MethodSyntax)
        {
            Console.WriteLine($"Name: {item.StudentName} \tLine: {item.Line}");
        }
    /*OUTPUT: Name: Jasurbek  Line: Line 1
                Name: Xondamir Line: Line 1
                Name: Shoxruh Line: Line 3
                Name: Shaxzod Line: Line 4
                Name: Abdulloh Line: Line 2  */
    }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int AddressId { get; set; }
}
class Address
{
    public int Id { get; set; }
    public string AddressLine { get; set; }
}
```
{% hint style="info" %} Bilib qo'ygan yaxshi! **INNER JOIN** orqali huddi shunday ketma-ketlikda 2dan ortiq to'plamlarni birlashtirish ham mumkin {% endhint %}
```csharp
class Program
{
    static void Main(string[] args)
    {
        var students = new List<Student>()
        {
            new Student() { Id = 1, Name = "Jasurbek", AddressId = 1},
            new Student() { Id = 2, Name = "Xondamir", AddressId = 1},
            new Student() { Id = 3, Name = "Shoxruh", AddressId = 3},
            new Student() { Id = 4, Name = "Shaxzod", AddressId = 4},
            new Student() { Id = 5, Name = "Abdulloh", AddressId = 2}
        };
        var addresses = new List<Address>()
        {
            new Address() {Id = 1, AddressLine = "Line 1"},
            new Address() {Id = 2, AddressLine = "Line 2"},
            new Address() {Id = 3, AddressLine = "Line 3"},
            new Address() {Id = 4, AddressLine = "Line 4"},
            new Address() {Id = 5, AddressLine = "Line 5"}
        };
        var marks = new List<Mark>()
        {
            new Mark() {Id = 1, StudentId = 1, TMarks = 80},
            new Mark() {Id = 2, StudentId = 2, TMarks = 85},
            new Mark() {Id = 3, StudentId = 3, TMarks = 75},
            new Mark() {Id = 4, StudentId = 4, TMarks = 90},
            new Mark() {Id = 5, StudentId = 5, TMarks = 85}
        };
        var QuerySyntax = from student in students
                            join address in addresses
                            on student.AddressId equals
                            address.Id
                            join mark in marks
                on student.Id equals mark.StudentId
                            select new
                            {
                                StudentName = student.Name,
                                Line = address.AddressLine,
                                TotalMarks = mark.TMarks
                            };
        foreach (var item in QuerySyntax)
        {
            Console.WriteLine($"Name: {item.StudentName} \tLine: {item.Line} \tMark={item.TotalMarks}");
        }
    /*OUTPUT: Name: Jasurbek  Line: Line 1    Mark=80
              Name: Xondamir  Line: Line 1    Mark=85
              Name: Shoxruh   Line: Line 3    Mark=75
              Name: Shaxzod   Line: Line 4    Mark=90
              Name: Abdulloh  Line: Line 2    Mark=85  */
    }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int AddressId { get; set; }
}
class Address
{
    public int Id { get; set; }
    public string AddressLine { get; set; }
}
class Mark
{
    public int Id { get; set; }
    public int StudentId { get; set; }
    public int TMarks { get; set; }
}
```

