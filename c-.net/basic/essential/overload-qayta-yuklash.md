---
description: Sobirjonov O'tkirbek
---

# Overload \(Qayta yuklash\)
 
Siz OOP da methodlar bilan ishlayotganingizda sizga **Overloading** va **Overriding** degan so’zlarga duch kelishingiz mumkin. Bu ikki tushuncha odatda methodlar bilan o’z vazifasini amalga oshiradi. **Overloading** va **Overriding** polimorphizm ni amalga oshirishnining keng tarqalgan usuli hisoblanadi. Biz hozir **Overloading** (Qayta yuklash) haqida batafsil to’xtalib o’tamiz. 
   ### Overloading ishlatilmagandagi holat 
Avvaliga bir xato yo’l bilan dastur yozaylik, chunki bu tushunchalar va qayta yuklash amali nimaga kerakligini tushunish uchun avval xato yo’lni ko’ribgina xulosa olishingiz mumkin. 
Quyidagi dasturda 2-3-4 ta sonlardan eng kattasini topish dasturi yozilgan.
```csharp
using System;  
namespace ConsoleApp1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            double max1, max2; 
            max1 = GetMaxOf2Numbers(2, 3.3); 
            max2 = GetMaxOf3Numbers(4.7, 3.3, 48.0); 
 
            Console.WriteLine(max1); 
            Console.WriteLine(max2); 
        } 
 
        static double GetMaxOf2Numbers(double number1, double number2) 
        { 
            return (number1 > number2) ? number1 : number2; 
        } 
 
        static double GetMaxOf3Numbers(double number1,  
            double number2, double number3) 
        { 
            if (number1 > number2 && number1 > number3) return number1; 
            else if (number2 > number1 && number2 > number3) return number2; 
            else if (number3 > number2 && number3 > number1) return number3; 
            else return -1; 
        } 
    } 
} 
```
Natija :  
```
3.3 
48 
```
Yuqoridagi dasturda ko’rganingizdek 

`GetMaxOf2Numbers`

`GetMaxOf3Numbers`

Ushbu methodlar uchun kiruvchi parametrlariga qarab nom berdik, endi yana bir o’ylab ko’ring, agar massiv yoki int toifasidagi sonlar orasidan eng kattasini topish kerak bo’lsachi, quyidagi dasturda buni ham ko’rishingiz mumkin:
```csharp
using System;  
namespace ConsoleApp1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            double max1, max2, max3; 
             
            max1 = GetMaxOf2Numbers(2, 3.3); 
            max2 = GetMaxOf3Numbers(4.7, 3.3, 48.0); 
 
            double[] arr = new double[] 
            { 
                2, 3.3, 5, 5, 89.0, 112.2, 98, 77 
            }; 
            max3 = GetMaxOfArray(arr); 
 
            Console.WriteLine(max1); 
            Console.WriteLine(max2); 
            Console.WriteLine(max3); 
        } 
 
        static double GetMaxOf2Numbers(double number1, double number2) 
        { 
            return (number1 > number2) ? number1 : number2; 
        } 
 
        static double GetMaxOf3Numbers(double number1,  
            double number2, double number3) 
        { 
            if (number1 > number2 && number1 > number3) return number1; 
            else if (number2 > number1 && number2 > number3) return number2; 
            else if (number3 > number2 && number3 > number1) return number3; 
            else return -1; 
        } 
 
        static double GetMaxOfArray(double[] arr) 
        { 
            if (arr != null) 
            { 
                double max = arr[0]; 
                for(int i=1; i<arr.Length; i++) 
                { 
                    if (arr[i] > max) max = arr[i]; 
                } 
                return max; 
            } 
            else return -1; 
        } 
    } 
}
```
Natija :  
```
3.3 
48 
112.2 
```
 
Yuqorida guvoh bo’lganingizdek nom o’ylab topish va uni ishlatish sizga biroz qiyin bo’lib qolyapti, biz 2-3 ta method uchun nom oson topa olamiz, lekin 200-300 ta methodlar da xatoliklar va chigalliklar yuzaga keladi. Siz yozgan class lardagi methodlar nima amal bajarishini u class ni ishlatayotganda nechta qiymat qabul qiladi, qanday turga mansub bo’lishi kerak hammasini bilib keyingina u methodlardan foydalana olasiz. Buni qanday hal qilish mumkin?

Demak : Biz yuqorida tutgan yo’limiz xato ekanligini tushunib oldik. Siz yozgan kodlarni kompyuter tushunaveradi, lekin o’zingiz va boshqa dasturchilar qiynalib qolishlari mumkin. 
Endi esa to’g’ri yo’lni o’rganamiz 
           
### Overloading qo’llanilishi
Biz barcha methodlarga bir xil nom berishimiz kerak bo’ladi, qanday turdagi va nechta qiymat kirib kelishidan qat’iy nazar. 
```csharp
using System;  
namespace ConsoleApp1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            double max1, max2, max3; 
             
            max1 = Max(2, 3.3); 
            max2 = Max(4.7, 3.3, 48.0); 
 
            double[] arr = new double[] 
            { 
                2, 3.3, 5, 5, 89.0, 112.2, 98, 77 
            }; 
            max3 = Max(arr); 
 
            Console.WriteLine(max1); 
            Console.WriteLine(max2); 
            Console.WriteLine(max3); 
        } 
 
        static double Max(double number1, double number2) 
        { 
            return (number1 > number2) ? number1 : number2; 
        } 
 
        static double Max(double number1,  
            double number2, double number3) 
        { 
            if (number1 > number2 && number1 > number3) return number1; 
            else if (number2 > number1 && number2 > number3) return number2; 
            else if (number3 > number2 && number3 > number1) return number3; 
            else return -1; 
        } 
 
        static double Max(double[] arr) 
        { 
            if (arr != null) 
            { 
                double max = arr[0]; 
                for(int i=1; i<arr.Length; i++) 
                { 
                    if (arr[i] > max) max = arr[i]; 
                } 
                return max; 
            } 
            else return -1; 
        } 
    } 
 
}
```
 
Natija :  
```
3.3 
48 
112.2 
```
Guvohi bo’lganingizdek hamma method nomini Max ga o’zgartirdik va method **overloading** ni amalga oshirdik. 
**Overloading** ni qo’llaganimizdan so’ng kodlarimiz qisqaradi va yanada tushunarli bo’ladi, quyidagi dasturda yuqoridagi dasturni qisqargan holati ko’rsatib o’tilgan (Main methodiga e’tibor bering va solishtiring). 
```csharp
using System;  
namespace ConsoleApp1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            double[] arr = new double[] 
            { 
                2, 3.3, 5, 5, 89.0, 112.2, 98, 77 
            }; 
 
            Console.WriteLine(Max(2, 3.3)); 
            Console.WriteLine(Max(4.7, 3.3, 48.0)); 
            Console.WriteLine(Max(arr)); 
        } 
 
        static double Max(double number1, double number2) 
        { 
            return (number1 > number2) ? number1 : number2; 
        } 
         
        static double Max(double number1,  
            double number2, double number3) 
        { 
            if (number1 > number2 && number1 > number3) return number1; 
            else if (number2 > number1 && number2 > number3) return number2; 
            else if (number3 > number2 && number3 > number1) return number3; 
            else return -1; 
        } 
 
        static double Max(double[] arr) 
        { 
            if (arr != null) 
            { 
                double max = arr[0]; 
                for(int i=1; i<arr.Length; i++) 
                { 
                    if (arr[i] > max) max = arr[i]; 
                } 
                return max; 
            } 
            else return -1; 
        } 
    } 
}
```
Natija :  
```
3.3 
48 
112.2 
```
 
Bu bilan biz nimaga erishdik? 
1. Foydalanayotganda turi va nechta qiymat qabul qilishini o’ylab o’tirmasdan, eng kattasini topuvchi method Max ekanmi, demak har qanday turdagi va har qancha qiymat ichidan eng kattasini topib beradi degan fikr paydo bo’ladi , va oson foydalanadi. 
2. Siz nom berishda o’ylab o’tirmaysiz, vazifasi bir xil va qabul qiluvchi qiymatlari har xil bo’ladigan holatda method nomini bir nomga keltirib olasiz. 
3. Kodlaringiz qisqaradi va yanada tushunarliroq va aniqroq bo’ladi.
