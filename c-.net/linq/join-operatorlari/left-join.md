---
description: Jasurbek Xasanboyev
---
# Left Join
Avvalgi **JOIN** tularidan farqli tomoni **LEFT JOIN** da maydon bo’sh bo’lishi ham mumkin. Ikki ro’yhatni birlashtirish vaqtida agar to’g’ri keladigan maydon topilmasa uni bo’sh holatda (null) tashlab ketadi. Buning uchun **DefaultEmpty** metodidan foydalanamiz:

Query Syntax:
```csharp
class Program
{
    static void Main(string[] args)
    {
        var students = new List<Student>()
    {
        new Student() { Id = 1, Name = "Jasurbek", AddressId = 1},
        new Student() { Id = 2, Name = "Xondamir", AddressId = 5},
        new Student() { Id = 3, Name = "Shoxruh", AddressId = 3},
        new Student() { Id = 4, Name = "Shaxzod", AddressId = 4},
        new Student() { Id = 5, Name = "Abdulloh"}
    };
        var addresses = new List<Address>()
    {
        new Address() {Id = 1, AddressLine = "Line 1"},
        new Address() {Id = 2, AddressLine = "Line 2"},
        new Address() {Id = 3, AddressLine = "Line 3"},
        new Address() {Id = 4, AddressLine = "Line 4"},
    };
        var QueerySyntax = from std in students
                            join add in addresses on
                            std.AddressId equals add.Id into
                            stdAddress
                            from studentAddress in stdAddress.DefaultIfEmpty()
                            select new { Name = std.Name, StudentAddress = studentAddress != null ? studentAddress.AddressLine : "Empty"};
        foreach (var item in QueerySyntax)
        {
                
            Console.WriteLine($"Name: {item.Name} Line: {item.StudentAddress}");
        }
        /*OUTPUT:   Name: Jasurbek Line: Line 1
                    Name: Xondamir Line: Empty
                    Name: Shoxruh Line: Line 3
                    Name: Shaxzod Line: Line 4
                    Name: Abdulloh Line: Empty  */
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
        new Student() { Id = 2, Name = "Xondamir", AddressId = 5},
        new Student() { Id = 3, Name = "Shoxruh", AddressId = 3},
        new Student() { Id = 4, Name = "Shaxzod", AddressId = 4},
        new Student() { Id = 5, Name = "Abdulloh"}
    };
        var addresses = new List<Address>()
    {
        new Address() {Id = 1, AddressLine = "Line 1"},
        new Address() {Id = 2, AddressLine = "Line 2"},
        new Address() {Id = 3, AddressLine = "Line 3"},
        new Address() {Id = 4, AddressLine = "Line 4"},
    };
            var MethodSyntax = students.GroupJoin(addresses, std => std.AddressId, add => add.Id,
                (std, add) => new { std, add }).SelectMany(x => x.add.DefaultIfEmpty(), 
                (StudentData, AddressData) => new { Name = StudentData.std.Name, Line = AddressData != null ? AddressData.AddressLine : "Empty"});
        foreach (var item in MethodSyntax)
        {
                
            Console.WriteLine($"Name: {item.Name} Line: {item.Line}");
        }
        /*OUTPUT:   Name: Jasurbek Line: Line 1
                    Name: Xondamir Line: Empty
                    Name: Shoxruh Line: Line 3
                    Name: Shaxzod Line: Line 4
                    Name: Abdulloh Line: Empty  */
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


