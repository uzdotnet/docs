---
description: Jasurbek Xasanboyev
---

# OrderBy va OrderByDescending

**OderBy** buyrug’I ma’lumotlarni o’sish tartibida saralab beradi:

Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Student> students = new List<Student>()
            {
                new Student() { Id = 1, Name = "Nodirbek", Result = 80},
                new Student() { Id = 2, Name = "Jasurbek", Result = 59},
                new Student() { Id = 3, Name = "Abdulloh", Result = 70}
            };
            var Passed = students.OrderBy(y => y.Result).Where(x => x.Result >= 60).Select(p => p.Name).ToList();
            foreach (var item in Passed)
            {
                Console.WriteLine(item);
            }
            // Output: Abdulloh, Nodirbek
        }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Result { get; set; }
}
```

Query syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Student> students = new List<Student>()
            {
                new Student() { Id = 1, Name = "Nodirbek", Result = 80},
                new Student() { Id = 2, Name = "Jasurbek", Result = 59},
                new Student() { Id = 3, Name = "Abdulloh", Result = 70}
            };
            var Passed = from std in students 
                         orderby std.Result
                         where std.Result >= 60
                         select std.Name;
            foreach (var item in Passed)
            {
                Console.WriteLine(item);
            }
            // Output: Abdulloh, Nodirbek
        }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Result { get; set; }
}
```

**OrderByDescending** ma’lumotlarni kamayish tartibida saralab beradi:

Method syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Student> students = new List<Student>()
            {
                new Student() { Id = 1, Name = "Nodirbek", Result = 80},
                new Student() { Id = 2, Name = "Jasurbek", Result = 59},
                new Student() { Id = 3, Name = "Abdulloh", Result = 70}
            };
            var Passed = students.OrderByDescending(x => x.Result).Where(x => x.Result >= 60).Select(x => x.Name);
            foreach (var item in Passed)
            {
                Console.WriteLine(item);
            }
            // Output: Nodirbek, Abdulloh
        }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Result { get; s
```

Query syntax:

```csharp
class Program
{
    static void Main(string[] args)
    {
            List<Student> students = new List<Student>()
            {
                new Student() { Id = 1, Name = "Nodirbek", Result = 80},
                new Student() { Id = 2, Name = "Jasurbek", Result = 59},
                new Student() { Id = 3, Name = "Abdulloh", Result = 70}
            };
            var Passed = from std in students
                         orderby std.Result descending
                         where std.Result >= 60
                         select std.Name;
            foreach (var item in Passed)
            {
                Console.WriteLine(item);
            }
            // Output: Nodirbek, Abdulloh
        }
}
class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Result { get; set; }
}
```

