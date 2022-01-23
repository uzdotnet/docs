---
description: Ravshan Sodiqov
---
# Asinxron dasturlash

Asinxron dasturlash – bu asosiy dastur jarayonini bloklamagan holda, bajarilayotgan vazifalarni alohida bloklarga olish imkonini beradi. Dastur ishlashi foydalanuvchi so’rovlarini qayta ishlash, ma’lumotlar bazalariga va tarmoq resurlariga kirish kabi nisbatan ko’proq vaqt talab etiladigan vazifalardan iborat  bo’lganda, asosiy oqimni bloklab qo’ymaslik uchun asinxron usullardan foydalaniladi.

![](https://user-images.githubusercontent.com/91861166/150674299-01336b58-30c8-414f-89e5-0d31a2d9e618.png)

Masalan, hajm va matn jihatdan nisbatan kattaroq fayldan ma’lumotlarni o’qish dasturini qaraymiz:

Sinxron usul:
```csharp
private string ReadFile(string file)
{
    string content = string.Empty;
    using (StreamReader reader = new StreamReader(file))
    {
        content = reader.ReadToEnd();
    }
    return content;
}
```

Bunda **ReadFile()** funksiyasi toki fayldan ma’lumotlar o’qib bo’lingunga qadar asosiy dastur jarayoni bloklanib turadi. Chunki biz ma’lumotni o’qishda sinxron usuldan foydalandik, bu esa juda noqulay jarayon va dastur ishlash vaqtini ham sezilarli darajada oshib yuboradi. Endi ushbu muammolarni hal etish uchun dasturning asosiy jarayonini bloklamagan holda asinxron usuldan foydalanamiz:

Asinxron usul:
```csharp
private async Task<string> ReadFileAsync(string file)
{
    string content = string.Empty;

    using (StreamReader reader = new StreamReader(file))
    {
        content = await reader.ReadToEndAsync();
    }

    return content;
}
```
Endi ushbu holatda ma’lumotlarni o’qish uchun **ReadToEndAsync()** metodidan foydalandik va dastur jarayoni ham bloklab qo’yilmadi. 

E’tibor bering:  Biz asinxron usuldan foydalanish uchun **Task**, **async**, va **await** kabi yangi kalit so’zlardan foydalandik va ishlash jarayoni asinxron tarzda ekanligini anglatish uchun  **ReadFileAsync** nomidan foydalandik (o’zgartirmaslik ham mumkin edi, bu dasturchining ixtiyorida, prinsipial jihatdan aslida bu kerak emas).  **ReadToEndAsync()** metodi esa asinxron tarzda ishlaydigan maxsus metod.

Yodda tuting:  Asinxron usul quyidagi xususiyatlarga ega:

•	Umumiy jarayon bir yoki bir nechta asinxron metodlardan iborat bo’ladi.

•	Jarayon ichidagi har bir asinxron metodlar oldidan await kalit so’zi ishlatiladi.

•	Umumiy jarayon  bitta bo’lsa ham asinxron metodni o’z ichiga olsa, uning nomi oldidan async kalit so’zi ishlatiladi.

•	Jarayonning qiymat qaytarish turi ham bir necha usulda aniqlanadi:

   o	void

   o	Task

   o	Task<T>
  
   o	ValueTask<>
  
  Asinxron usullar doimgidek bir yoki bir nechta parametrlar qabul qilishi mumkin, ammo, parametrlarni **ref** va **out** modifikatorlari bilan aniqlab bo’lmaydi. Jarayon nomi oldidan **async** kalit so’zini ishlatish ham dasturni avtomatik tarzda asinxron usulga o’tkazmaydi, balki, bunda bir nechta asinxron metodlardan foydalanish imkonini yaratadi. Yuqoridagi **ReadToEndAsync()** metodi kabi .NET Core olamida asinxron tarzda ishlovchi metodlar mavjud va ular sinxron usulda ishlovchi metodlardan farqli ravishda *Async* qo’shimchasi bilan tugaydi. Biz har bir asinxron metodni chaqirishdan oldin **await** kalit so’zini ishlatishimiz mumkin. Endi yuqorida berilgan fayldagi ma’lumotlarni asinxron tarzda o’qish jarayonini Main metodi ichida qanday boshlash kerak ekanligini qaraymiz:
  
```csharp
namespace AsynAwaitDemo
{
    class Program
    {
        static async Task<string> ReadFileAsync(string file)
        {
            string content = string.Empty;

            using (StreamReader reader = new StreamReader(file))
            {
                content = await reader.ReadToEndAsync();
            }

            return content;
        }

        static async void ContentToConsole()
        {
            string readFileTask = await ReadFileAsync("c:\\temp\\file.txt");

            Console.WriteLine("Fayldagi ma'lumotlar:" + readFileTask);
        }

        static void Main(string[] args)
        {
            Task task = new Task(ContentToConsole);
            task.Start();
            task.Wait();
            Console.ReadLine();
        }
    }
}
```
  
Ushbu holatda Main metodi ichida **ContentToConsole** jarayonini boshlash uchun Task obyektidan foydalandik va parametr sifatida ushbu nom berildi. **ContentToConsole** o’z navbatida asinxron tarzda ishlovchi **ReadFileAsync()** metodini o’z ichiga olgan va ushbu metod qaytargan qiymatni Console ga chiqarishi bilan jarayon yakunlanadi. Biz asosiy dastur qismini bloklamagan holda nisbatan katta hajmdagi fayllardan ma’lumotlarni o’qish jarayoniga erishdik va bu dastur foydalanuvchisiga ham noqulaylik keltirib chiqarmaydi. 
  
  Asinxron dasturlashga bir hayotiy misol: siz yaxshi biladigan Telegram ilovasida ham asinxron dasturlashdan foydalanilgan. Shuning uchun Telegramga hajmi nisbatan kattaroq faylni yuklayotgan paytingizda bir vaqtning o'zida boshqa chatlardagi xabarlarni o'qish, yoki telegramda boshqa jarayonlarni amalga oshirish imkoni bor. Bu bir nechta jarayonlar asinxron tarzda ishlayveradi. Agar telegram dasturida asinxron emas, sinxron dasturlashdan foydalanilganida toki faylni to'la yuklab bo'lgunicha interfeys bloklanib, boshqa hech qanday amal bajarishning imkoni bo'lmasdi.
  
  Asinxron metodlar ko’pchilik holatlarda veb ilovalarda yangi foydalanuvchi yaratish so’rovi yuborilganda yoki ma’lumotlar bazasidan tegishli ma’lumotlarni o’qish jarayonidan ancha qo’l keladi va bu foydalanuvchi interfeysi bilan bog’liq muammolarni ham keltirib chiqarmaydi.
