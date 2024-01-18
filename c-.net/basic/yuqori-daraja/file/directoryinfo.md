---
description: Nodirbek Abdulaxadov
---

## DirectoryInfo

[**DirectoryInfo sinfi**](https://learn.microsoft.com/en-us/dotnet/api/system.io.directoryinfo?view=net-7.0) - papkalarni yaratish, ko'chirish va o'chirish uchun property va metodlarni taqdim etadi. DirectoryInfo sinfidan voris olish imkonsiz.


**[DirectoryInfo propertylari](https://learn.microsoft.com/en-us/dotnet/api/system.io.directoryinfo?view=net-7.0#properties):**


| Property nomi | Xususiyati |
| :--- | :--- |
| FullName | Papka joylashgan to’liq katalog nomini qaytaradi |
| Exists | Papka mavjudligini tekshiradi |
| CreationTime | Papka yaratilgan vaqtini qaytaradi |
| LastAccessTime | Papka ishlatilgan oxirgi vaqtni qaytaradi |
| LastWriteTime | Papkaning oxirgi o’zgartirilgan vaqtini qaytaradi |
| Name | Papka nomini qayatardi |
| Parent | Papka joylashgan papkani (katalog usti katalogni) qaytaradi |
| Root | Papka joylashgan root papkani (eng ustki katalogni) qaytaradi |


**[DirectoryInfo metodlari](https://learn.microsoft.com/en-us/dotnet/api/system.io.directoryinfo?view=net-7.0#methods):**

| Metod nomi | Funksionalligi |
| :--- | :--- |
| Create | Papka yaratadi |
| CreateSubdirectory | Papka ichiga papka(subdirectory) yaratadi. |
| GetDirectories | Papka ichidagi mavjud papkalarni qaytaradi |
| GetFiles | Papka ichidagi mavjud fayllarni qaytaradi |
| Delete | Belgilangan papkani o'chiradi. |
| MoveTo | Belgilangan papkani yangi joyga ko'chiradi va yangi papka nomini ko'rsatish imkoniyatini beradi. |
| Refresh | Papka holatini yangilaydi. |

_DirectoryInfo xususiyatlardan foydalanish:_

```csharp
string path = "C:\\Users\\Nodirbek";
var directoryInfo = new DirectoryInfo(path);

// papka mavjudligini tekshirish
if (directoryInfo.Exists)
{
    Console.WriteLine("Papka ichidagi mavjud papkalar:");
    foreach (var directory in directoryInfo.GetDirectories())
    {
        //papka nomi va yaratilgan vaqti
        Console.WriteLine(directory.Name.PadRight(30) + "\t" + directory.CreationTime);
    }
    Console.WriteLine();

    Console.WriteLine("Papka ichidagi mavjud fayllar:");
    foreach (var file in directoryInfo.GetFiles())
    {
        //fayl nomi
        Console.WriteLine(file.Name);
    }
}
else
{
    Console.WriteLine("Bunday papka mavjud emas!");
}
```

_DirectoryInfo metodlaridan foydalanish:_

```csharp
string path = "C:\\Users\\Nodirbek\\Desktop\\ExampleFolder";
string path2 = "C:\\Users\\Nodirbek\\Desktop\\ExampleFolder_Copy";
var directoryInfo = new DirectoryInfo(path);

try
{
    //papkani yaratish | agar mavjud bo'lsa xatolik sodir bo'ladi
    directoryInfo.Create();

    // faylni pathdan path2 ga ko'chirish
    directoryInfo.MoveTo(path2);
    Console.WriteLine($"{path} papka {path2} ga ko'chirildi.");

    // papkani o'chirish | papkani bo'sh ekanligiga ishonch hosil qiling
    directoryInfo.Delete();
    Console.WriteLine($"{path} papka o'chirildi");
}
catch (Exception e)
{
    Console.WriteLine($"Xatolik sodir bo'ldi: {e.Message}");
}
```

**Izohlar:**

Fayllarni yaratish, ko'chirish, tarkibidagi papka va fayllarni ko'rish kabi bir nechta amallarni bajarish uchun DirectoryInfo sinfidan foydalanamiz. Agar papka ustida birgina amalni bajarmoqchi yoki bitta xususiyatini olmoqchi bo'lsangiz **Directory** static sinfining tegishli metodlaridan foydalanishingiz mumkin.

## Directory

[**Directory**](https://learn.microsoft.com/en-us/dotnet/api/system.io.directory?view=net-7.0) sinfi - DirectoryInfo metodlari bilan bir xil funksionallikka ega metodlardan statik holatda foydalanishni ta'minlaydigan sinfdir.
Directory sinfi metodlari haqida batafsil ma'lumotni [bu yerdan](https://learn.microsoft.com/en-us/dotnet/api/system.io.directory?view=net-7.0#methods) olishingiz mumkin.

Yuqoridagi kod qismini Directory sinfi yordamida alternativini yozishimishiz mumkin:

```csharp
string path = "C:\\Users\\Nodirbek\\Desktop\\ExampleFolder";
string path2 = "C:\\Users\\Nodirbek\\Desktop\\ExampleFolder_Copy";

try
{
    //papkani yaratish | agar mavjud bo'lsa xatolik sodir bo'ladi
    Directory.CreateDirectory(path);

    // faylni pathdan path2 ga ko'chirish
    Directory.Move(path, path2);
    Console.WriteLine($"{path} papka {path2} ga ko'chirildi.");

    // papkani o'chirish | papkani bo'sh ekanligiga ishonch hosil qiling
    Directory.Delete(path);
    Console.WriteLine($"{path} papka o'chirildi");
}
catch (Exception e)
{
    Console.WriteLine($"Xatolik sodir bo'ldi: {e.Message}");
}
```
