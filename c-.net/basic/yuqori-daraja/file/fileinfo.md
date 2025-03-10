---
description: Nodirbek Abdulaxadov
---

## FileInfo

[FileInfo](https://learn.microsoft.com/en-us/dotnet/api/system.io.fileinfo?view=net-7.0) sinfi - fayllarni yaratish, nusxalash, o'chirish, ko'chirish va ochish uchun property va metodlarni taqdim etadi. Shuningdek, [FileStream](https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream?view=net-5.0) obyektlarini yaratishda yordam beradi.


[**FileInfo propertylari:**](https://learn.microsoft.com/en-us/dotnet/api/system.io.fileinfo?view=net-7.0#properties)


| Property nomi | Xususiyati |
| :--- | :--- |
| Directory | Fayl joylashgan katalog nomini qaytaradi |
| DirectoryName | Fayl joylashgan to’liq katalog nomini qaytaradi |
| Exists | Fayl mavjudligini tekshiradi |
| Extension | Fayl turini\(kengaytmasini\) qaytaradi |
| FullName | Faylning to’liq manzilini qaytaradi |
| IsReadOnly | Fayl faqat o’qish uchun ekanligini tekshiradi |
| CreationTime | Fayl yaratilgan vaqtini qaytaradi |
| LastAccessTime | Fayl ishlatilgan oxirgi vaqtni qaytaradi |
| LastWriteTime | Faylning oxirgi o’zgartirilgan vaqtini qaytaradi |
| Length | Fayl hajmini qaytaradi \(baytlarda\) |
| Name | Fayl nomini qayatardi |


[**FileInfo metodlari:**](https://learn.microsoft.com/en-us/dotnet/api/system.io.fileinfo?view=net-7.0#methods)

| Metod nomi | Funksionalligi |
| :--- | :--- |
| AppendText | FileInfo ushbu nusxasi tomonidan taqdim etilgan faylga matn qo'shadigan StreamWriter yaratadi. |
| CopyTo | Mavjud faylning ustiga yozishni taqiqlab, mavjud faylni yangi faylga ko'chiradi. |
| Create | Fayl yaratadi |
| CreateText | Yangi matnli faylni yozadigan StreamWriter-ni yaratadi. |
| Delete | Belgilangan faylni o'chiradi. |
| MoveTo | Belgilangan faylni yangi joyga ko'chiradi va yangi fayl nomini ko'rsatish imkoniyatini beradi. |
| Open | Belgilangan FileMode-da ochadi. |
| OpenRead | Faqat o'qish uchun FileStream yaratadi. |
| OpenText | Mavjud matnli fayldan o'qiydigan UTF8 kodlash bilan StreamReader yaratadi. |
| OpenWrite | Faqat yozish uchun FileStream yaratadi. |

_FileInfo xususiyatlardan foydalanish:_

```csharp
//faylga joylashgan path
string path = @"C:\Users\user\Desktop\test.txt";

//FileInfo sinfidan yangi obyekt hosil qilish
FileInfo fileInfo = new FileInfo(path);

//Exist yordamida fayl mavjudligini tekshirish
if (fileInfo.Exists)
{
    //fayl xususiyatlarini chiqarish
    Console.WriteLine($"Fayl joylashgan katalog: \t{fileInfo.Directory}");
    Console.WriteLine($"Fayl kengaytmasi: \t{fileInfo.Extension}");
    Console.WriteLine($"Faylning to'liq nomi: \t{fileInfo.FullName}");
    Console.WriteLine($"Yaratilgan vaqti: \t{fileInfo.CreationTime}");
    Console.WriteLine($"Hajmi: \t{fileInfo.Length} bayt");
}
```

_FileInfo metodlaridan foydalanish:_

```csharp
string path = "Example.txt";
var fileInfo = new FileInfo(path);

try
{
    string path2 = "Example_copy.txt";

    // faylni pathdan path2 ga nusxalash
    fileInfo.CopyTo(path2);
    Console.WriteLine($"{path} fayl {path2} ga nusxalandi.");

    // faylni o'chiradi
    fileInfo.Delete();
    Console.WriteLine($"{path} fayl o'chirildi");
}
catch (Exception e)
{
    Console.WriteLine($"Xatolik sodir bo'ldi: {e.Message}");
}
```

**Izoh:**

Fayllarni ochish, yaratish, ko'chirish, nomini o'zgartirish va o'chirish kabi odatiy operatsiyalar uchun FileInfo sinfidan foydalanamiz. C# dasturlash tilida fayllar bilan ishlashni yanada osonlashtira oladigan **File** sinfi ham mavjud. Agar siz fayl ustida bir-nechta amallarni bajarmoqchi bo'lsangiz FileInfo sinfidan foydalanganingiz ma'qul.

## File

[**File**](https://learn.microsoft.com/en-us/dotnet/api/system.io.file.opentext?view=net-7.0) sinfi - FileInfo metodlari bilan bir xil funksionallikka ega metodlardan statik holatda foydalanishni ta'minlaydigan sinfdir.
File sinfi metodlari haqida batafsil ma'lumotni [bu yerdan](https://learn.microsoft.com/en-us/dotnet/api/system.io.file?view=net-7.0#methods) olishingiz mumkin.

Yuqoridagi kod qismini File sinfi yordamida alternativini yozishimishiz mumkin:

```csharp
string path = "Example.txt";
try
{
    string path2 = "Example_copy.txt";

    // faylni pathdan path2 ga nusxalash
    File.Copy(path, path2);
    Console.WriteLine($"{path} fayl {path2} ga nusxalandi.");

    //faylni o'chiradi
    File.Delete(path);
    Console.WriteLine($"{path} fayl o'chirildi");
}
catch (Exception e)
{
    Console.WriteLine($"Xatolik sodir bo'ldi: {e.Message}");
}
```
