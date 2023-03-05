---
description: Jamshid Sodiqov
---

# Union

Union operatori berilgan ikkita to’plamni qo’shib dublikatlardan holi bo’lgan yangi to’plam hosil qilish uchun ishlatiladi.

![](https://user-images.githubusercontent.com/91861166/222968134-954cfb45-f7b4-46e1-abca-5c2295851747.png)

Masalan:
```csharp
IList<string> strList1 = new List<string>() { "One", "Two", "three", "Four" };
IList<string> strList2 = new List<string>() { "Two", "THREE", "Four", "Five" };

var result = strList1.Union(strList2);

foreach(string str in result)
        Console.WriteLine(str);
```
Output:
```
One
Two
Three
THREE
Four 
Five
```

Union operatori murakkab datatypelar toʻplami uchun toʻgʻri natijani qaytarmaydi.

Bu shuni anglatadiki, biz murakkab ma'lumotlar turlari bilan ishlayotganimizda, kutilganidek natijani olish uchun **IEqualityComparer** interfeysini implement qilishimiz kerak.

Students class uchun IEqualityComparer interfeysini quyidagi tarzda implement qilish mumkin :
```csharp
public class Student 
{
    public int StudentID { get; set; }
    public string StudentName { get; set; }
    public int Age { get; set; }
}

class StudentComparer : IEqualityComparer<Student>
{
    public bool Equals(Student x, Student y)
    {
        if (x.StudentID == y.StudentID && x.StudentName.ToLower() == y.StudentName.ToLower())
            return true;

        return false;
    }

    public int GetHashCode(Student obj)
    {
        return obj.StudentID.GetHashCode();
    }
}
```

Endi to'g'ri natijaga erishish uchun Union metodi usulida StudentComparer sinfidan foydalanishimiz mumkin:
```csharp
IList<Student> studentList1 = new List<Student>() { 
        new Student() { StudentID = 1, StudentName = "John", Age = 18 } ,
        new Student() { StudentID = 2, StudentName = "Steve",  Age = 15 } ,
        new Student() { StudentID = 3, StudentName = "Bill",  Age = 25 } ,
        new Student() { StudentID = 5, StudentName = "Ron" , Age = 19 } 
    };

IList<Student> studentList2 = new List<Student>() { 
        new Student() { StudentID = 3, StudentName = "Bill",  Age = 25 } ,
        new Student() { StudentID = 5, StudentName = "Ron" , Age = 19 } 
    };

var resultedCol = studentList1.Union(studentList2, new StudentComparer()); 

foreach(Student std in resultedCol)
    Console.WriteLine(std.StudentName);
```

Output:
```
John
Steve
Bill
Ron
```

Union operatori C# va VB.Net Query sintaksisida qo'llab-quvvatlanmaydi.
