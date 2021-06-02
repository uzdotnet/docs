---
description: Nodirbek Abdulaxadov
---

# FileInfo

FileInfo sinfi - fayllarni yaratish, nusxalash, o'chirish, ko'chirish va ochish uchun xususiyatlar va metodlarni taqdim etadi. Shuningdek, [FileStream](https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream?view=net-5.0) obyektlarini yaratishda yordam beradi.

**FileInfo xususiyatlari:**

| Directory | Fayl joylashgan katalog nomini qaytaradi |
| :--- | :--- |
| DirectoryName | Fayl joylashgan to’liq katalog nomini qaytaradi |
| Exists | Fayl mavjudligini tekshiradi |
| Extension | Fayl turini\(kengaytmasini\) qaytaradi |
| FullName | Faylning to’liq manzilini qaytaradi |
| IsReadOnly | Fayl faqat o’qish uchunligini tekshiradi |
| CreationTime | Fayl yaratilgan vaqtini qaytaradi |
| LastAccessTime | Fayl ishlatilgan oxirgi vaqtni qaytaradi |
| LastWriteTime | Faylning oxirgi o’zgartirilgan vaqtini qaytaradi |
| Length | Fayl hajmini qaytaradi \(baytlarda\) |
| Name | Fayl nomini qayatardi |

**FileInfo metodlari:**

| AppendText | FileInfo ushbu nusxasi tomonidan taqdim etilgan faylga matn qo'shadigan StreamWriter yaratadi. |
| :--- | :--- |
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
using System;
using System.IO;

namespace FileInfo_examples
{
    class Program
    {
        static void Main(string[] args)
        {
            //faylga yo'l
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

            Console.ReadKey();
        }
    }
}
```

![](../../../.gitbook/assets/image%20%2824%29.png)

_FileInfo metodlaridan foydalanish:_

```csharp
using System;
using System.IO;
namespace FileInfo_Examples
{
    class Test
    {
        public static void Main()
        {
            string path = Path.GetTempFileName();
            var fi1 = new FileInfo(path);

            // Create a file to write to.
            using (StreamWriter sw = fi1.CreateText())
            {
                sw.WriteLine("Hello");
                sw.WriteLine("And");
                sw.WriteLine("Welcome");
            }

            // Open the file to read from.
            using (StreamReader sr = fi1.OpenText())
            {
                var s = "";
                while ((s = sr.ReadLine()) != null)
                {
                    Console.WriteLine(s);
                }
            }

            try
            {
                string path2 = Path.GetTempFileName();
                var fi2 = new FileInfo(path2);

                // Ensure that the target does not exist.
                fi2.Delete();

                // Copy the file.
                fi1.CopyTo(path2);
                Console.WriteLine($"{path} was copied to {path2}.");

                // Delete the newly created file.
                fi2.Delete();
                Console.WriteLine($"{path2} was successfully deleted.");
            }
            catch (Exception e)
            {
                Console.WriteLine($"The process failed: {e.ToString()}");
            }
            Console.ReadKey();
        }
    }
}
```

![](../../../.gitbook/assets/image%20%2883%29.png)

**Izohlar:**

Fayllarni ko'chirish, nomini o'zgartirish, yaratish, ochish, o'chirish va qo'shib qo'yish kabi odatiy operatsiyalar uchun FileInfo sinfidan foydalaning.

Agar bitta faylda bir nechta operatsiyalarni bajarayotgan bo'lsangiz , [File](https://docs.microsoft.com/en-us/dotnet/api/system.io.file?view=net-5.0) sinfining tegishli statik metodlari o'rniga [FileInfo](https://docs.microsoft.com/en-us/dotnet/api/system.io.fileinfo?view=net-5.0) instansiya metodlaridan foydalanish samaraliroq bo'lishi mumkin , chunki xavfsizlikni tekshirish har doim ham talab qilinmaydi. [FileInfo xususiyatlari va metodlari qo’llanishiga doir misollar](https://github.com/Nodirbek-Abdulaxadov/FileInfo-examples)

