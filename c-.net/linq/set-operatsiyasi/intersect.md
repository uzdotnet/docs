# Intersect

# Intersect

Ikkita to'plamning kesishmasi deb, bu to'plamlarning har ikkalasida ham mavjud bo'lgan elementlardan tuzilgan to’plamga aytilishini siz yaxshi bilasiz. LINQdagi **Intersect** metodi bizga ikkita to’plamning kesishmasini, ya’ni bu to’plamlarning har ikkoviga ham tegishli elementlarni olish imkoniyatini beradi. 

Metod quyidagi ko'rinishda ishlatiladi:
```csharp
var kesishma=Birinchi_toplam.Intersect(Ikkinchi_toplam);
```
{% hint style="info" %}
  Eslatma: A ∩ B = B ∩ A bo’lgani uchun to’plamlarning qaysi biri avval, qaysi biri keyin yozilishining umuman ahamiyati yo’q, baribir natija bir xil bo’ladi.
{% endhint %}


**Intersect** metodiga parametr sifatida kiritilayotgan to’plamlarning biri yoki ikkalasi null ga teng bo’lganida `ArgumentNullExeption` xatoligi yuzaga keladi.

Keling, soddaroq misol sifatida ikkita sonlar to’plamining kesishmasini olib ko’ramiz:
```csharp 
using System;
using System.Linq;
class dotnetuz
{
    public static void Main()
    {
        int[] A = { 1, 2, 5, 13, 4, 7, 9 };
        int[] B = { 0, 2, 5, 7, 8, 9, 10, 11 };
        int[] C = A.Intersect(B).ToArray();
        foreach (int item in C)
        {
            Console.WriteLine(item);
        }
        Console.ReadKey();
    }
}
```
Natija:
```
2
5
7
9
```
Ko'rib turganimizdek, dastur ishlashi natijasida to'plamlarning har ikkalasida mavjud bo'lgan elementlargina ekranga chiqarildi.


Endi bu metodni bitta classga tegishli obyektlar ustida ishlatib ko’raylik. 

Keling, bitta hayotiy masala qo’yamiz: Aytaylik,  o’quv markazida ikki xil kurs bor. Bu kurslarga qatnashayotgan o’quvchilarning alohida ikkita ro’yxati berilgan va har ikkala kursga ham qatnashuvchi o’quvchilarni ajratib berishimiz so’ralgan bo’lsin. Bu masalani LINQdan foydalanib hal qilib ko’ramiz.

Buning uchun,  an’anaga sodiq qolgan holda qo’shimcha bitta *Comparer* sinf yaratib olamiz (aslida qanday nom berish ixtiyoringiz), va unga `IEqualityComparer` interfeysini implementatsiya qilib, **Equals()** va  **GetHashCode()** metodlarini qayta yozib olamiz:
```csharp
public class Pupil
    {
        public string Name { get; set; }
        public string SurName { get; set; }
    }

class PupilComparer : IEqualityComparer<Pupil>
    {
        // Ismi ham, familiyasi ham bir xil o'quvchilarni bitta o'quvchi deb hisoblaymiz
        public bool Equals(Pupil x, Pupil y)
        {

            //Obyektlar ikkalasi bitta havolaga murojaat qilayotganini tekshiramiz
            if (Object.ReferenceEquals(x, y)) return true;

            // Obyekt null emasligini tekshiramiz
            if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
                return false;

            // Ikkala obyekt tengligini tekshirib, bir xil bo'lsa true qaytaramiz
            return x.SurName == y.SurName && x.Name == y.Name;
        }

        // Agar Equals() metodi biror juftlik uchun true qiymat qaytarsa, GetHashCode() metodi 
        // ham bu juftlik uchun aynay bir xil HashCode qaytarishi kerak:

        public int GetHashCode(Pupil pupil)
        {
            // Obyekt null ga teng emasligini tekshirib olamiz
            if (Object.ReferenceEquals(pupil, null)) return 0;

            // Name maydoni null bo'lmasa, uning Hesh-kodini olamiz
            int hashPupilName = pupil.Name == null ? 0 : pupil.Name.GetHashCode();

            // SurName maydonining hesh-kodini olamiz
            int hashPupilCode = pupil.SurName.GetHashCode();

            // O'quvchining hesh-kodini hisoblaymiz
            return hashPupilName ^ hashPupilCode;
        }
    }
```

To’liq kod quyidagicha bo’ladi:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
namespace comparer
{
    class dotnetuz
    {
        public static void Main()
        {
           Pupil [] Maths={ 
                            new Pupil {Name="Anvar", SurName="Aliyev"},
                            new Pupil {Name="Abduolim", SurName="Ahmadjonov"},
                            new Pupil {Name="Sarvar", SurName="Valijonov"},
                            new Pupil {Name="Ali", SurName="Salimov"},
                            new Pupil {Name="Ali", SurName="Ganiyev"}
                          };

           Pupil[] Physics ={                                
                                new Pupil {Name="Sarvar", SurName="Valijonov"},
                                new Pupil {Name="Abduolim", SurName="Ahmadjonov"},
                                new Pupil {Name="Ali", SurName="Hakimov"},
                                new Pupil {Name="Ali", SurName="Salimov"}
                            };

            IEnumerable<Pupil> kesishma =
                Physics.Intersect(Maths, new PupilComparer());

            foreach (var pupil in kesishma)
                Console.WriteLine(pupil.Name + " " + pupil.SurName);

            Console.ReadKey();
        }
    }
    public class Pupil
    {
        public string Name { get; set; }
        public string SurName { get; set; }
    }

    class PupilComparer : IEqualityComparer<Pupil>
    {
        // Ismi ham, familiyasi ham bir xil o'quvchilarni bitta o'quvchi deb hisoblaymiz
        public bool Equals(Pupil x, Pupil y)
        {

            //Obyektlar ikkalasi bitta havolaga murojaat qilmayotganini tekshiramiz
            if (Object.ReferenceEquals(x, y)) return true;

            // Obyekt null emasligini tekshiramiz
            if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
                return false;

            // Ikkala obyekt tengligini tekshirib, bir xil bo'lsa true qaytaramiz
            return x.SurName == y.SurName && x.Name == y.Name;
        }

        // Agar Equals() metodi biror juftlik uchun true qiymat qaytarsa, GetHashCode() metodi 
        // ham bu juftlik uchun aynay bir xil HashCode qaytarishi kerak:

        public int GetHashCode(Pupil pupil)
        {
            // Obyekt null ga teng emasligini tekshirib olamiz
            if (Object.ReferenceEquals(pupil, null)) return 0;

            // Name maydoni null bo'lmasa, uning Hesh-kodini olamiz
            int hashPupilName = pupil.Name == null ? 0 : pupil.Name.GetHashCode();

            // SurName maydonining hesh-kodini olamiz
            int hashPupilCode = pupil.SurName.GetHashCode();

            // O'quvchining hesh-kodini hisoblaymiz
            return hashPupilName ^ hashPupilCode;
        }
    }
}
```
Natija:
```
Sarvar Valijonov
Abduolim Ahmadjonov
Ali Salimov
```
