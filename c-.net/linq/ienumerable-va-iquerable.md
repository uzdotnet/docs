---
description: Jasurbek Xasanboyev
---

# IEnumerable va IQuerable


LINQ so\`rovlarda qaytish tipi aniq bo\`lmagan holatlarda ularni to\`plam holatida qabul qilib olish uchun IEnumerable interfeysidan foydalaniladi.   Ushbu interfeys System.Collection namespace da joylashgan. IEnumerable C\# dasturlash tilidagi barcha to\`plamlar bilan ishlay oladi. Ushbu toifadagi to\`plam elementlariga itteratorlik murojaat mavjud bo\`lgani uchun bemalol foreach takrorlanish operatori yordamida  elementlarni olishimiz mumkin bo\`ladi. IEnumerable umumiy tiplar uchun IEnumerable&lt;T&gt;  ko\`rinishda ham murojaat qilish mumkin.

```csharp
static void Main(string[] args)
{
    List<Employee> employees = new List<Employee>()
    {
        new Employee() { id = 1, name = "Jasurbek" },
        new Employee() { id = 2, name = "Muhammadkarim"}
    };
    IEnumerable<Employee> query = from emp in employees
                                  where emp.id == 1
                                  select emp;
    foreach(var item in query)
    {
        Console.WriteLine($"Id = {item.id} Name: {item.name}");
    }
}
class Employee
{
    public int id { get; set; }
    public string name { get; set; }
}

```

IQuerable ham  interfeys bo\`lib u System.Linq  namespace da joylashgan. IQuerable interfeysi IEnumerable interfeysidan olingan vorisdir. IQuerable Provayderlik hususiyatiga ham ega. Ushbu hususiyat IQueryProvider deb nomlanadi.IQueryProvider LinqProviders dan foydalanadi. IQuerable boshqa provayderlar bilan ishlash jarayonida eng yaxshi ko\`makchi bo\`la oladi(chunki tezlik jihatdan IEnumerable ko\`ra tezroq ishlaydi). 

```csharp
static void Main(string[] args)
{
    List<Employee> employees = new List<Employee>()
    {
        new Employee() { id = 1, name = "Jasurbek" },
        new Employee() { id = 2, name = "Muhammadkarim"}
    };

    IQueryable<Employee> query = employees.AsQueryable().Where(x => x.id == 1);

    foreach(var item in query)
    {
        Console.WriteLine($"Id = {item.id} Name: {item.name}");
    }
}
class Employee
{
    public int id { get; set; }
    public string name { get; set; }
}
```

