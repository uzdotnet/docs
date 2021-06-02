---
description: Ilyosxo'ja Sulaymonov
---

# Do-While sikl operatori

Assalomu alaykum hammaga derdimu ha mayli. Baribir assalomu alaykum. Xo’sh endi sizlr bilan do-while takrorlash operatori bilan tanishamizmi? Ha tanishamiz. Ketdik unda do-while xuddi for, while kabi takrorlash operatori bo’lib ulardan farqli ravishda avval amal bajarib so’ng shart tekshirarkan qoyilmisiz. Umumiy tuzilishi:  
_do {   
      Operatorlar;   
}_  
while\(shart\);   
Demak do-while , while dan farqli ravishda avval amalni bajarib so’ng shartni tekshiradi. Agar shart true bo’lsa takrorlashni bajaradi, aks holda takrorlashni tugatadi. Dastur ishga tushirsangiz kamida bitta amal bajaradi. To’g’risi hamda o’lay deb shuncha kod yozasiz u ishlamasa alam qiladimi? do-while o’sha alam qilishni oldini oladida. Quyidagi misolni ko’rsak, 1 dan 10 gacha sonlar yig’indisi

```csharp
int i = 1, s = 0;
do
{
    s = s + i;
    i = i + 1;
} while (i <= 10);
```

{} figurali qavslar do-while siklida shart bo’lmasada, lekin ularni ishlatish dastur kodini o’qishni osonlashtiradi va while siklidan farqlashga yordam beradi Shunday qilib do-while operatori bilan ham tanishib olibmiz. Keling unda yana bir misol ko’ramiz. Nima demadingiz: Berilgan uch xonali sonni raqamlarini teskari tartibda yozib ekranga chiqarsin hozir nima deganimni tushunganlar tushundi, ya’ni 986 yozsak bizga 689 ni hosil qilsin kelishdikmi? Kelishmasak ham shuda endi ko’naverasiz.

```csharp
class sikl
{
    static void Main(string[] args)
    {
        int num;
        int nextdigit;
        Console.Write("Son: ");
        num = Convert.ToInt32(Console.ReadLine());
        Console.Write("Soning raqamlari teskari tartibda: ");
        do
        {
            nextdigit = num % 10;
            Console.Write(nextdigit);
            num = num / 10;
        }while (num > 0);
        Console.WriteLine();
        Console.ReadLine();
    }
}	
```

mana azizlar sizlarga aytmoqchi e yog’ee yozmoqchi bo’lgan\(yozib bo’ldingku deydigan odam yo’g’aa\) ma’lumotlar qisqacha shular. Boshlashda qanday gaz bosgan bo’lsangiz buyog’iga ham shunday davom eting.

