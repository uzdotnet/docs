---
description: Shohruh Nosirov
---

# TakeWhile
Biz Take() operatori haqida bilib oldik endi uning akasi TakeWhile() haqida gaplashamiz. TakeWhile() bizga Take() qilolmaydigan ishlarni qilishga yordam beradi. Endi tasavvur qilamiz bizda qandaydir top’lam berilgan. Men shu to’plamdan boshidan boshlab nechtadir elementni emas qandaydir shartni qanoatlantiradiganlarini olishni hoxladim. Shunda bizga TakeWhile()  kerak buladi.<br/>
Masalan butun sonlardan iborat List berilgan men uning ichidan juft elementlarini olishni hoxladim.

```csharp
class Program
{
    static void Main(string[] args)
    {

          List<int> sonlar = new List<int>() { 2, 2, 3, 4, 5, 6, 7, 8, 9, 10 };


            //Ekranga chiqaramiz
            Console.WriteLine("Boshlangich elementlar:");
           foreach(var i in sonlar)
            {
                Console.Write(i + " ");
            }


            var yangisonlar = sonlar.TakeWhile(x=>x%2==0);
            Console.WriteLine("\nJuft elementlari:");

            foreach(var i in yangisonlar)
            {
                Console.Write(i + " ");
            }
            // 2 2

            Console.ReadKey();
 

```
  
Dastur natijasiga e’tibor bergan bulsayiz bizga 2 2 degan natija qayti ammo bizda yana juft sonlar bor ediku. TakeWhile() shart bajarilmay qolguncha ishlaydi xolos u avval 2 2 ni oldi undan sung bizda 3 elementi mavjud bulgani uchun shart bajarilmay qoldi. Agar bizda juft elementdan boshlanmaganda nima bulardi degan savol ham paydo buldi agar bunday bulganda hechqanday element qaytarmagan bulardi. Chunki shart boshida ishlamaydi. Huddiku TakeWhile() ga C# bir marttagina imkoniyat bergan xolosdek. Imkoniyati shart bajarilmay qolgan payti uchib ketadi.<br/>
Shu bilan TakeWhile() mavzuyimiz ham nihoyasiga yetdi.




