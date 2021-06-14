---
description: Jasurbek Xasanboyev
---

# Select

Select operatori yordamida ma'lumotlar bazasidan ma'lumotlarni tanlab olib yangi to'plam hosil qilish uchun ishlatiladi. Yaratilgan yangi to'plam bilan bajarilgan holatlar ma'lumotlar bazasiga ta'sir o'tkazmaydi. Tanlashni bir necha usullarini ko'rib o'tamiz:

```csharp
class Program
    {
        static void Main(string[] args)
        {
            List<Employee> employees = new List<Employee>()
            {
                new Employee() { id = 1, name = "Zarif", email = "zarif@gmail.com"},
                new Employee() { id = 2, name = "Muhammadkarim", email = "muhammadkarim@gmail.com"},
                new Employee() { id = 3, name = "Xumoyun", email = "xumoyun@gmail.com"},
                new Employee() { id = 4, name = "Akrom", email = "akrom@gmail.com"},
                new Employee() { id = 5, name = "Jasur", email = "jasur@gmail.com"},
                new Employee() { id = 6, name = "Mirzo Ulug`bek", email = "mirzoulugbek@gmail.com"},
                new Employee() { id = 7, name = "Behzod", email = "behzod@gmail.com"}
            };

            var basicQuery = (from emp in employees
                              select emp).ToList();
            Console.WriteLine("Basic Query: ");
            foreach(var item in basicQuery)
            {
                Console.WriteLine($"Id = {item.id} Name: {item.name}");
            }

            Console.WriteLine("#--------#--------#---------#");

            //-----------------------------------------//

            var basicMethod = employees.ToList();
            Console.WriteLine("Basic Method: ");
            foreach (var item in basicMethod)
            {
                Console.WriteLine($"Id = {item.id} Name: {item.name}");
            }

            Console.WriteLine("#--------#---------#---------#");

            //-----------------------------------------//

            var basicPropQuery = (from emp in employees
                                 select emp.id).ToList();
            Console.WriteLine("Basic property query: ");
            foreach (var item in basicPropQuery)
            {
                Console.WriteLine($"Id = {item}");
            }

            Console.WriteLine("#--------#---------#---------#");

            //-----------------------------------------//

            var basicPropMethod = employees.Select(emp => emp.name);
            Console.WriteLine("Basic property method: ");
            foreach (var item in basicPropMethod)
            {
                Console.WriteLine($"Id = {item}");
            }

            Console.WriteLine("#--------#---------#---------#");

            //-----------------------------------------//

            var selectQuery = (from emp in employees
                               select new Student()
                               {
                                   stId = emp.id,
                                   stName = emp.name,
                                   stEmail = emp.email
                               }).ToList();
            Console.WriteLine("Select query: ");
            foreach (var item in selectQuery)
            {
                Console.WriteLine($"Id = {item.stId} Name: {item.stName}");
            }

            Console.WriteLine("#--------#---------#---------#");

            //-----------------------------------------//

            var selectMethod = (employees.Select(emp => new Student() { stId = emp.id, stName = emp.name, stEmail = emp.email })).ToList();

            Console.WriteLine("Select method: ");
            foreach (var item in selectMethod)
            {
                Console.WriteLine($"Id = {item.stId} Name: {item.stName}");
            }

            Console.WriteLine("#--------#---------#---------#");

            //-----------------------------------------//

            var query = employees.Select((emp, index) => new { Index = index, stName = emp.name }).ToList();

            // Bu query yozishning eng yaxshi ko`rinishlaridan biridir

        }
        class Employee
        {
            public int id { get; set; }
            public string name { get; set; }
            public string email { get; set; }
        }
        class Student
        {
            public int stId { get; set; }
            public string stName { get; set; }
            public string stEmail { get; set; }
        }
    }
```

