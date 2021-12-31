---
description: Ravshan Sodiqov
---
# finally

  Bundan avvalgi  darslarimizda try/catch bloki haqida yaxshigina ma’lumotlarni qo’lga kiritigansiz degan umidda ushbu bloklarning finalini ta’minlovchi finally haqida so’z yuritamiz.
   Dasturlar ba’zida istisno holatlari bilan yakunlangan bo’lishi mumkin, ya’ni dastur tanasining  **try { ... }**  bloki bajarilmasdan aksincha, dastur **catch { ... }** bloki ichida yakunlangan. Ammo ba’zida dastur xatolik holatiga tushguniga qadar biror yopilishi kerak bo’lgan fayl yoki tarmoqni ochgan bo’lishi mumkin.  Bunday ochilgan tarmoq va fayllarni yopish uchun **finally { ... }** blokidan foydalaniladi.  
{% hint style="info" %}
  **finally** bloki har qanday istisno holati (catch) yoki try bloki bajarilishidan qat’iy nazar bajariladi.
{% endhint %}
“_Sizlar nima qilsangiz ham men baribir so’ngida o’z so’zimni aytaman_” shiori ostida ish ko’ruvchi blokni amaliy misollarda qaraymiz:
```csharp
try
{
    int a = 0;
    int b = 5;
    Console.WriteLine(b/a);
}

catch(DivideByZeroException)
{
    Console.WriteLine("0 ga bo'lish mumkin emas !");
}

finally
{
    Console.WriteLine("Dastur ishlashi tugallandi.");
} 
```
Yuqoridagi holatda dasturning istisno holati bajarilgach,  finally bloki ichidagi kod o’z ishini boshlaydi. Agar o’zgaruvchilarning qiymatlarini misol uchun a = 2, b = 4 tarzida o’zgartirsak, u holda, dasturning catch bloki bajarilmaydi, lekin so’ngida baribir finally bloki ichidagi kod bajarilishini ko’rish  mumkin.

Endi yana bir misolni qaraymiz. Faraz qilaylik, ma’lum katalogdagi fayldagi ma’lumotlarni boshqa faylning ma’lumotlariga qo’shish kerak:  
```csharp
StreamReader reader = null;
StreamWriter writer = null;
try
{
    reader = new StreamReader(File.Open(@"C:\Users\Public\Documents\file1.txt", FileMode.Open));
    writer = new StreamWriter(File.Open(@"C:\Users\Public\Documents\file2.txt", FileMode.Append, FileAccess.Write));
    while (reader.Peek() != -1)
    {
        writer.WriteLine(reader.ReadLine());
    }

}

catch(Exception ex)
{
     Console.WriteLine(ex);
}
```

Yuqoridagi holatda file1.txt faylining ma’lumotlari file2.txt ga qo’shilmoqda. Agar file1.txt dagi ma’lumotlarni o’qishda yoki file2.txt ga ma’lumotlarni yozishda qandaydir xatolik ro’y bersa, dasturning catch bloki bajariladi va xatolik to’g’risida xabar qilinadi. Lekin shuni unutmaslik kerak-ki, dastur catch holatiga tushganda ikkala fayllarning ham holati ochiq holda. Endi ushbu dasturga  finally  bloki ichida bu ikkala faylni ham yopuvchi kodni yozish eng to’g’ri qaror:
```csharp
StreamReader reader = null;
StreamWriter writer = null;
try
{
    reader = new StreamReader(File.Open(@"C:\Users\Public\Documents\file1.txt", FileMode.Open));
    writer = new StreamWriter(File.Open(@"C:\Users\Public\Documents\file2.txt", FileMode.Append, FileAccess.Write));
    while (reader.Peek() != -1)
    {
        writer.WriteLine(reader.ReadLine());
    }
}

catch(Exception ex)
{
    Console.WriteLine(ex);
}

finally
{
    if(reader != null)
    {
        reader.Close();
    }

    if(writer != null)
    {
        writer.Close();
    }
}

Console.ReadKey(); 
```
