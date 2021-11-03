---
description: Faxriddin Xushnazarov
---
# Funksiyalarda massivdan foydalanish

Hozir biz siz bilan funksiyalarda massivlardan foydalanishning bir nechta hollarini ko’rib chiqamiz. 
1.  Keling Python dasturlash tilidagi *range()* funksiyasiga o’xshash funksiyani biz C# dasturash tilida tuzib ko’ramiz. 
Izoh: *range()* – asosan ikkita argument qabul qiladi aytaylik n va m, ushbu funksiyaning vazifasi n dan m gacha bo’lgan butun sonli array ni qaytaradi(m kirmaydi). 
```csharp
  static int[] Range(int n, int m) 
    { 
        int[] range = new int[m - n]; 
        int k = 0; 
        for(int i=n; i<m; i++) 
            range[k++] = i; 
        return range; 
    } 
```

Bu yerda biz *Range* funksiyasining type sifatida *int[]* massiv typeni berdik. Endi ushbu funksiyadan foydalanib n dan m gacha bo’lgan butun sonlar yig’indisini hisoblaymiz: 
```csharp
using C=System.Console; 
using System.Linq; 
public class Program 
{ 
    public static int[] Range(int n, int m) 
    { 
        int[] range = new int[m - n]; 
        int k = 0; 
        for(int i=n; i<m; i++) 
            range[k++] = i; 
        return range; 
    } 
    public static void Main(string[] args) 
    { 
        int n,m; 
        C.Write("n="); 
        n = int.Parse(C.ReadLine()); 
        C.Write("m="); 
        m = int.Parse(C.ReadLine()); 
        C.WriteLine($"{n} dan {m} gacha bo'lgan yig'indi={Range(n,m+1).Sum()}"); 
    } 
} 
 ```
 
2.  Endi funksiyaning argumentlariga massivlardan foydalanishni ko’rsak.   
Funksiyaning argumentiga massiv ham xuddi o’zgaruvchidek ishlatiladi 
Misol uchun: `<type> funksiyaNomi(int[] x, string[] y){}`

Keling biz **System** nomlar fazosidagi **Array** classining **Sort()** metodiga o’xshash funksiya yaratib ko’ramiz. 
Izoh: **Array.Sort**  metodinig argumentiga massivni bersak ushbu metod bizga bergan massiv elementlarini o’sish tartibida tartiblaydi. 
Biz faqat *int* typedagi massivni sort qiladigan funksiya yozamiz! 
  ```csharp 
  static void Sort(ref int[] massiv) 
    { 
        int x; 
        for(int i=0; i<massiv.Length-1; i++) 
            for(int j=i+1; j<massiv.Length; j++) 
            { 
                if (massiv[j] < massiv[i]) 
                { 
                    x = massiv[i]; 
                    massiv[i] = massiv[j]; 
                    massiv[j] = x; 
                } 
            } 
    } 
   ```
Xop bu funksiyani endi ishlatib ko’ramiz: 
 ```csharp
    static void Main(string[] args) 
    { 
        int[] mas = { 5, 4, 2, 1, 7, 45, 41, 6, 3, 4 }; 
        Sort(ref mas); 
        foreach (int x in mas) 
            Console.Write(x+", "); 
    } 
  ```
Natija: `1, 2, 3, 4, 4, 5, 6, 7, 41, 45, `
                                          
Endi biz ushbu funksiya yordamida massivdagi eng katta va eng kichik elementni ham topishimiz mumkin: 
```csharp
static void Main(string[] args) 
{ 
 int[] mas = { 5, 4, 2, 1, 7, 45, 41, 6, 3, 4 }; 
 Sort(ref mas); 
 Console.WriteLine($"eng kichigi: {mas[0]}, eng kattasi: {mas[mas.Length - 1]}"); 
} 
```
Natija: `eng kichigi: 1, eng kattasi: 45`   
                                          
Demak biz funksiyalarning type va ularning argumentlarida bemalol massiv typelaridan foydalana olar ekanmiz.
