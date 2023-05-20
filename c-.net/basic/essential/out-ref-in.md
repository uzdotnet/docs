---
description: Wahid Abduhakimov
---

# in, ref, out ni bilib oling!

C# dagi `ref`, `out`, `in` kalit so’zlari metod parametrlarni manipulatsiya qilishda ishlatiladi va jo’natilgan argumentlarga turlicha hususiyatlar beradi. Ularni har birini oson va qisqa misollar bilan tushintirib beraman.

## 1. `out`

`out` kalit so’zi parametrni reference shaklida jo’natadi va ushbu parametr metodni *output*i (natijasi) ekanini anglatadi. Bu orqali jo’natilgan parametrning qiymatini shu chaqirilgan metod ichida o’zgartirish imkoni bo’ladi. 

> 💡 `out` kalit so’zi bilan jo’natilgan parametr chaqirilgan metod ichida yangi qiymat o’zlashtirilishi shart.

```csharp
public void Bolish(int bolinuvchi, int boluvchi, out int bolinma, out int qoldiq)
{
    bolinma = bolinuvchi/ boluvchi;
    qoldiq = bolinuvchi % boluvchi;
}

// Ishlatish:
int bolinuvchi = 10;
int boluvchi = 3;
int bolinma, qoldiq;
Bolish(bolinuvchi, boluvchi, out bolinma, out qoldiq);
Console.WriteLine($"Bolinma: {bolinma}, Qoldiq: {qoldiq}");  
// Natija: Bolinma: 3, Qoldiq: 1
```

## 2. `ref`

`ref` kalit so’zi metodga parametrlarni reference orqali jo’natish imkonini beradi. ref orqali jo’natilgan argumentlar , chaqiruvchi methodagi asl o’zgaruvchi qiymati ham o’zgaradi. Metod ichida shu argument bo’lgan har qanday o’zgarishlar chaqiruvchida ham aks etadi. 

> 💡 `ref` parametri metodga jo’natishdan avval qiymat o’zlashtirilgan (intialize qilingan) bo’lishi shart.

```csharp
public void Oshirish(ref int son)
{
    son++;
}

// Ishlatilishi:
int qiymat = 5;
Oshirish(ref qiymat);
Console.WriteLine(qiymat);  
// Natija: 6
```

### 2. `in`

`in` kalit so’zi ham parametrni metodga reference sifatida uzatadi lekin metodni shu parametrni qiymatini o’zgartirishni cheklaydi. U asosan katta strukturalar yoki read-only ma'lumotlarni nusxa ko'chirish xarajatlarisiz uzatib hotira sarfini optimallashtirish uchun ishlatiladi.

> 💡 `in` parametri metod ichida o’zgartilishi mumkin emas.

```csharp
public void ChopEtish(in string habar)
{
    Console.WriteLine(habar);
		// habar = "Salom Dunyo";   // --> ERROR
    // habar qiymatini o'zgartirish mumkin emas
}

// Ishlatilishi:
string tekst= "Wahid ustoz eng zo'ri, eeeeng zo'ri!";
ChopEtish(in tekst);  
// Output: Wahid ustoz eng zo'ri, eeeeng zo'ri!!
```
