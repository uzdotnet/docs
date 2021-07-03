---
description: Jasurbek Xasanboyev
---

# Group Join

[INNER JOIN](https://docs.dot-net.uz/c-.net/linq/join-operatorlari/inner-join) orqali to’plamlarni ulashda bizga kerakli qismlarni ajratib olib yangi to’plam hosil qilar edik. **GROUP JOIN** da esa avvalgidek bir xil qism bo’yicha qo’shadi lekin hamma parametrlar ko’chib o’tadi.

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
    };
        var MethodSyntax = addresses.GroupJoin(students, address => address.Id, 
        student => student.AddressId, (address, student) => new { address, student}).ToList();
        foreach (var item in MethodSyntax)
        {
            Console.WriteLine($"Line: {item.address.AddressLine}");
            foreach (var item2 in item.student)
            {
                Console.WriteLine($"Name: {item2.Name}");
            }
        }
        /*OUTPUT:   Line: Line 1
                    Name: Jasurbek
                    Name: Xondamir
                    Line: Line 2
                    Name: Abdulloh
                    Line: Line 3
                    Name: Shoxruh
                    Line: Line 4
                    Name: Shaxzod  */
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

Query Syntax

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
    };
        var QueerySyntax = from line in addresses
                            join std in students on
                            line.Id equals std.AddressId into stdGroup
                            select new { line, stdGroup};
        foreach (var item in QueerySyntax)
        {
            Console.WriteLine($"Line: {item.line.AddressLine}");
            foreach (var item2 in item.stdGroup)
            {
                Console.WriteLine($"Name: {item2.Name}");
            }
        }
        /*OUTPUT:   Line: Line 1
                    Name: Jasurbek
                    Name: Xondamir
                    Line: Line 2
                    Name: Abdulloh
                    Line: Line 3
                    Name: Shoxruh
                    Line: Line 4
                    Name: Shaxzod  */
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

