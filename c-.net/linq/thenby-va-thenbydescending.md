---
description: Jasurbek Xasanboyev
---

# ThenBy va ThenByDescending

**ThenBy** ikkinchi tartibli saralash bo’lib avval saralangan ro’yhatni ikkinchi navbatda qaysi hususiyat bo’yicha sarlash kerak ekanligini bildiradi. Masalan avval familiya bo’yicha saralangan bo’lsa familiyasi bir xil insonlarni ismi bo’yicha saralash kerak bo’ladi shunday vaziyatlarda **ThenBy** dan foydalaniladi. 

Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Employee> employees = new List<Employee>()
            {
                new Employee() { Id = 1, FirstName = "Muhammadkarim", Lastname = "To'xtaboyev"},
                new Employee() { Id = 2, FirstName = "Zokirjon", Lastname = "Xasanboyev" },
                new Employee() { Id = 3, FirstName = "Jasurbek", Lastname = "Xasanboyev" }
            };

            var MethodSyntax = employees.OrderBy(x => x.Lastname).ThenBy(x => x.FirstName);
            foreach (var emp in MethodSyntax)
            {
                Console.WriteLine($"{emp.Id} {emp.Lastname} {emp.FirstName}");
            }
            /* Output: 1 To'xtaboyev Muhammadkarim
                       3 Xasanboyev Jasurbek
                       2 Xasanboyev Zokirjon
            */

        }
    }
class Employee
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string Lastname { get; set; }
}
```

Query syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Employee> employees = new List<Employee>()
            {
                new Employee() { Id = 1, FirstName = "Muhammadkarim", Lastname = "To'xtaboyev"},
                new Employee() { Id = 2, FirstName = "Zokirjon", Lastname = "Xasanboyev" },
                new Employee() { Id = 3, FirstName = "Jasurbek", Lastname = "Xasanboyev" }
            };

            var QuerySyntax = from emp in employees
                               orderby emp.Lastname,
                               emp.FirstName
                               select emp;
            foreach (var emp in QuerySyntax)
            {
                Console.WriteLine($"{emp.Id} {emp.Lastname} {emp.FirstName}");
            }
            /* Output: 1 To'xtaboyev Muhammadkarim
                       3 Xasanboyev Jasurbek
                       2 Xasanboyev Zokirjon
            */

        }
    }
class Employee
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string Lastname { get; set; }
}
```

ThenByDescending ham huddi shu tartibda ishlatiladi lekin u ma’lumotlarni kamayish tartibida saralaydi.

