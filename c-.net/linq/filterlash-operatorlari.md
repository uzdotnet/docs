---
description: Xasanboyev Jasurbek
---
# Filterlash operatorlari

Filtrlash operatorlari ma’lumotlar ichidan o’zimiz uchun moslarini ajratib olish imkonini yaratadi. Misol uchun: bizda imtihon natijalari berilgan ro’yhat bor ushbu ro’yhatdan imtihondan o’tganlarni ajratib olishimiz kerak ya’ni 60% dan yuqarori natija ko’rsatganlarni o’tkazishimiz kerak shunday holatlarda filtirlash bizga qo’l keladi.
Ma’lumotlarni filtrlash uchun **where** kalit so’zi ishlatilinadi.
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
            var Passed = students.Where(x => x.Result >= 60).Select(p => p.Name).ToList();
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
