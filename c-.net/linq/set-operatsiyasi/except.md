---
decription: Ravshan Sodiqov
---
# Except

Algebra kursining to’plamlar mavzusidan shunisi ma’lumki, bizga quyidagicha  A = {2,  3 , 5, 6, 8}  va  B={2, 3, 4, 7, 8} to’plamlar berilgan bo’lsa, A/B to’plam A to’plamdan  ikki to’plamning kesishmasidagi sonlarning olib tashlanganiga teng bo’ladi, ya’ni  A/B = {5, 6}. 

LINQ metodlari ichida **Except** bizga xuddi mana shu imkoniyatni taqdim etadi. Demak, **Except()** metodi birinchi to’plamdagi ikkinchi to’plamda mavjud bo’lmagan yangi to’plamni qaytaradi.

Method syntax: 
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
class Program
{
    static void Main(string[] args)
    {
        List<int> list1 = new List<int>() { 2, 3, 5, 6, 8 };

        List<int> list2 = new List<int>() { 2, 3, 4, 7, 8 };

        //Method syntax
        var result1 = list1.Except(list2).ToList();

        foreach (var i in result1)
        {
            Console.WriteLine(i);
        }

        //Output: 5  6

    }
}
```

Query syntax:
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
class Program
{
    static void Main(string[] args)
    {
        List<int> list1 = new List<int>() { 2, 3, 5, 6, 8 };

        List<int> list2 = new List<int>() { 2, 3, 4, 7, 8 };

        //Query syntax
        var result2 = (from item in list1 select item).Except(list2).ToList();
        foreach (var i in result2)
        {
            Console.WriteLine(i);
        }

        //Output: 5  6
    }
}
```


Endi esa bir sinfga tegishli bo’lgan ikkita object ni qanday taqqoslash mumkinligi haqida bosh qotirsak. Masalan, bu muammoni *“ Car ”* sinfiga tegishli bo’lgan ikkita object ustida qanday hal etish mumkin ?  Bu sinfga tegishli bo’lgan mashinalarimiz *“Id”* va *“Name”* xususiyatlariga ega bo’lsin.
```csharp
public class Car
{
        public int Id { get; set; }
        public string Name { get; set; }
}
```

Endigi navbat bu objectlarni taqqoslash uchun asosiy *“CarsComparer”* sinfini yaratish. Bu sinfga  `IEqualityComparer<Cars>` interfeysini implementatsiya qilamiz va ushbu interfeysga tegishli Equals() va GetHashCode() metodlarini qayta yuklaymiz:
```csharp
public class CarComparer : IEqualityComparer<Car>
{
    public bool Equals(Car x, Car y)
    {

        //Taqqoslangan objectlar bir xil ma'lumotlarga murojaat qilishini tekshirish.
        if (Object.ReferenceEquals(x, y)) return true;

        //Object larni null qiymatga tekshirish
        if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
            return false;

        //Object larning xususiyatlarini taqqoslash
        return x.Id == y.Id && x.Name == y.Name;
    }

    public int GetHashCode(Car obj)
    {
        //Obyektni null qiymatga tekshirish
        if (Object.ReferenceEquals(obj, null)) return 0;

        //Obyektning Id xususiyati uchun HashCode ni hisoblash
        int hashCarId = obj.Id.GetHashCode();

        //Obyektning Name xususiyati uchun HashCode ni hisoblash
        int hashCarName = obj.Name == null ? 0 : obj.Name.GetHashCode();

        //Obyektning HashCode ni qaytarish 
        return hashCarName ^ hashCarId;
    }

}
```
Nega aynan bunday yozdik va bu qanday ishlaydi? **GetHashCode()** orqali *Car* sinfiga tegishli bo’lgan obyektimizning Id va Name xususiyatlari uchun HashCode ni hisoblab, Obyektimizning HashCode ni qaytardik. **Equals()** metodi orqali esa taqqoslanadigan obyektlarning bir xil ma’lumotga ega ekanligi, ulardan birortasi null qiymatga teng ekanligini va ularni xususiyatlari bo’yicha taqqoslash imkoniga ega bo’ldik. 

Oxirgi bosqich: “Biz kutgan onlar yetib keldi” : 
So’ngida esa *Car* sinfiga tegishli obyektlarni o’zida jamlagan ikki massiv yaratib o’zaro farqli elemantlarni  taqqoslashni ko’rib chiqamiz  
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
namespace exept
{
    class program
    {

        public static void Main(string[] args)
        {
            //Birinchi to'plam
            Car[] cars1 =
            {
                new Car{ Id= 1, Name="BMW"},
                new Car{ Id = 2, Name="RollsRoys"},
                new Car{ Id = 3, Name="Wolskvagen"}
            };

            //Ikkinchi to'plam
            Car[] cars2 =
            {
                new Car{ Id = 1, Name="Lacetti"},
                new Car{ Id = 2, Name="RollsRoys" }
            };

            //To'plamlarni taqqoslash
            IEnumerable<Car> result = cars1.Except(cars2, new CarComparer());

            foreach (var item in result)
                Console.WriteLine(item.Id + " " + item.Name);

            //Output: 1  BMW
            //        2  Wolksvagen

            Console.ReadKey();
        }
    }


    public class CarComparer : IEqualityComparer<Car>
    {
        public bool Equals(Car x, Car y)
        {

            //Taqqoslangan objectlar bir xil ma'lumotlarga murojaat qilishini tekshirish.
            if (Object.ReferenceEquals(x, y)) return true;

            //Object larni null qiymatga tekshirish
            if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
                return false;

            //Object larning xususiyatlarini taqqoslash
            return x.Id == y.Id && x.Name == y.Name;
        }

        public int GetHashCode(Car obj)
        {
            //Obyektni null qiymatga tekshirish
            if (Object.ReferenceEquals(obj, null)) return 0;

            //Obyektning Id xususiyati uchun HashCode ni hisoblash
            int hashCarId = obj.Id.GetHashCode();

            //Obyektning Name xususiyati uchun HashCode ni hisoblash
            int hashCarName = obj.Name == null ? 0 : obj.Name.GetHashCode();

            //Obyektning HashCode ni qaytarish 
            return hashCarName ^ hashCarId;
        }

    }

    public class Car
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }
}
```
Natijada esa *“cars1”* to’plamiga tegishli bo’lgan “RollsRoys” obyekti barcha xususiyatlari bo’yicha *“cars2”* da ham saqlangani uchun *“cars1”* dan olib tashlanganini ko’rish mumkin.

“Bizni kutar biz kutgan kodlar”   :)
