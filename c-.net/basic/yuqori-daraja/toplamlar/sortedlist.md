---
description: Tolibjonov Abdulloh
---

# SortedList

SortedList ham xuddi Listga o\`xshash to\`plam. Elementlarni qo\`shish, o\`chirish, saralash kabi funksiyalar SortedListda ham mavjud. Ammo Listdan farqi elementlar kalit/qiymat tarzida bo\`ladi. Bu qanday bo\`ladi deysizmi? Har bir element qiymatini o\`z kaliti bo\`ladi.

| **1** | **2** | **3** | **4** | **5** |
| :--- | :--- | :--- | :--- | :--- |
| Muhammad Karim | Xondamir | Jasur | Farruh | Abdulloh |

Masalan bu rasmda,

1 – kalitda Muhammad Karim

2 – kalitda Xondamir

3 – kalitda Jasur

4 – kalitda Farruh

5 – kalitda Abdulloh turadi degani.

####  MUHIM QOIDALAR !

* SortedListda elementga nafaqat indeksi orqali balki, kaliti orqali ham kirish mumkin
*  Kalit null qiymat qabul qilmaydi, ammo element null qiymatni qabul qiladi.
* Bir xil qiymatli elementlar bo\`lishi mumkin, ammo ularning kalitlari bir xil bo\`lmaydi
* Kalitlarni faqat sonlar emas balki ixtiyoriy tipda ham berishingiz mumkin, faqatgina kalitlarning hammasi bir xil tipda bo\`lishi kerak, aks holda kompilyator ishlamaydi

### **SortedListni qanday yaratamiz ?**

#### 1-bosqich ****

Kod yuqorisiga using System.Collections; ni yozib qo\`ying

#### 2-bosqich 

Berilgan sintaksis bo\`yicha SortedList yaratamiz 

```csharp
SortedList list_nomi = new SortedList();
```

list\_nomi degan joyga o\`zingiz ixtiyoriy nom berishingiz mumkin !

#### **3-bosqich Element qo\`shamiz 2 xil usulda :** 

1\) SortedListni yaratiboq elementlarni yoniga yozib qo\`ying \(xuddi massivdek\)

```csharp
SortedList list = new SortedList() 
{ 
    {1, "Abdullajon" }, 
    
    {2, "Shum bola" },
    
    {3, "Sariq dev" }  
};
```

  
Ahamiyat bersangiz elementlar ham jingalak qavs ichida yoziladi, sababi kompilyator kaliti qaysi qiymatga tegishli ekanini aniqlashda xato qilmasligi uchun.

2\) Add\(\) funksiyasi yordamida qo\`shish mumkin

```csharp
SortedList list = new SortedList();
list.Add(1, "Abdullajon");
list.Add(2, "Shum bola");
list.Add(3, "Sariq dev");
```

####  **4-bosqich**

**Elementlarga kirish GetKey\(\) va GetByIndex\(\)**

```csharp
SortedList list = new SortedList();
list.Add(1, "Abdullajon");
list.Add(2, "Shum bola");
list.Add(3, "Sariq dev");

for(int i = 0; i < list.Count; i++)
{
    Console.WriteLine($"{list.GetKey(i)} - {list.GetByIndex(i)}");
}
```

**Natija:**

![](../../../../.gitbook/assets/image%20%28109%29.png)

  
GetKey\(i\) – i element turgan indeksi, indeksiga qarab elementning kalitini aniqlab beradi**.** GetByIndex\(i\) – i indeksiga qarab element qiymatini aniqlab beradi

```csharp
SortedList list = new SortedList();
list.Add(1, "Abdullajon");
list.Add(2, "Shum bola");
list.Add(3, "Sariq dev");

string x = (string)list[2];

Console.WriteLine(x);
```

Natija:

![](../../../../.gitbook/assets/image%20%28107%29.png)

```csharp
SortedList list = new SortedList();

list.Add(1, "Abdullajon"); // pair
list.Add(2, "Shum bola"); // pair
list.Add(3, "Sariq dev");// pair

foreach(DictionaryEntry pair in list)
{
    Console.WriteLine($"{pair.Key} - {pair.Value}");
}
```

Natija:

![](../../../../.gitbook/assets/image%20%28100%29.png)

### **SortedListga misollar**

```csharp
using System;
using System.Collections;

namespace ConsoleApp11
{
    class Program
    {
        static void Main(string[] args)
        {
            SortedList list = new SortedList();

            list.Add(1, "Lambo");
            list.Add(2, "Mercedes"); 
            list.Add(3, "BMW");
            list.Add(4, "RoLLs");
            list.Add(5, "BentLey");

            foreach (DictionaryEntry pair in list)
            {
                Console.WriteLine($"{pair.Key} - {pair.Value}");
            }
        }
    }
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2892%29.png)

### SortedList dan elementlarni o\`chirish

#### Clear\(\) Remove\(\) RemoveAt\(\) 

Clear\(\) - funksiyasi to'plamdagi barcha elementlarni o'chirib tashlaydi

```csharp
SortedList list = new SortedList();

list.Add(1, "Lambo");
list.Add(2, "Mercedes"); 
list.Add(3, "BMW");
list.Add(4, "RoLLs");
list.Add(5, "BentLey");

list.Clear();

foreach (DictionaryEntry pair in list)
{
    Console.WriteLine($"{pair.Key} - {pair.Value}");
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2898%29.png)

Remove\(T\) – T-da turgan elementni o\`chiradi, T-indeksda turgan elementni emas.

```csharp
SortedList list = new SortedList();

list.Add(1, "Lambo");
list.Add(2, "Mercedes"); 
list.Add(3, "BMW");
list.Add(4, "RoLLs");
list.Add(5, "BentLey");

list.Remove(3);// 3-elementni o`chiradi, 3-indeksdagini emas

foreach (DictionaryEntry pair in list)
{
    Console.WriteLine($"{pair.Key} - {pair.Value}");
}
```

Natija:

![](../../../../.gitbook/assets/image%20%28110%29.png)

#### RemoveAt\(\)

```csharp
SortedList list = new SortedList();

list.Add(1, "Lambo");
list.Add(2, "Mercedes"); 
list.Add(3, "BMW");
list.Add(4, "RoLLs");
list.Add(5, "BentLey");

list.RemoveAt(3);

foreach (DictionaryEntry pair in list)
{
    Console.WriteLine($"{pair.Key} - {pair.Value}");
}
```

Natija:

![](../../../../.gitbook/assets/image%20%2897%29.png)

{% hint style="info" %}
Eslatma! Remove\(\) bilan RemoveAt\(\) funksiyalarida qaysi element o\`chib ketganiga ahamiyat bering ular bir xil emas.
{% endhint %}

### Element bor yoki yo\`qligini tekshirish 

#### Contains\(\), ContainsKey\(\), ContainsValue\(\)

Contains\(\) va ContainsKey\(\) funksiyalari bir xil

```csharp
SortedList list = new SortedList();

list.Add(1, "Lambo");
list.Add(2, "Mercedes"); 
list.Add(3, "BMW");
list.Add(4, "RoLLs");
list.Add(5, "BentLey");

Console.WriteLine(list.Contains(3));//kaliti 3

```

Natija:

![](../../../../.gitbook/assets/image%20%28101%29.png)

Bu funksiya kaliti 3ga teng bo'lgan element bor yoki yo'qligini tekshirib beradi. Bor bo'lsa True, bo'lmasa False.

#### ContainsValue\(\)

```csharp
SortedList list = new SortedList();

list.Add(1, "Lambo");
list.Add(2, "Mercedes"); 
list.Add(3, "BMW");
list.Add(4, "RoLLs");
list.Add(5, "BentLey");

Console.WriteLine(list.ContainsValue("Porsche"));
```

Natija:

![](../../../../.gitbook/assets/image%20%28111%29.png)

Bu funksiya kalitni emas, berilgan qiymat bor yoki yo'qligini tekshiradi. Listda Porsche yo'q edi. Shu sababli False.

