---
description: Yusupov Adhamjon
---

# Funksiyalarda massivdan foydalanish

Massivlarni argument sifatida funksiya parametriga berish mumkin. Massivlar ma'lumotli(reference) tur bo'lgani uchun, funksiya unung qiymatlarini o'zgartira oladi.

Butun sonlardan iborat massiv qimatlarini <i>n</i> marta ko'paytirish uchun quyidagicha ifodalash mumkin:
```csharp
static void Main()
{
  int[] numArr = { 3, 5, 8, 12, 21};
  Multiply(numArr, 2);
}

static void Multiply(int[] numArr, int mul)
{
  for (int i = 0; i < numArr.Length; i++)
  {
    numArr[i] *= mul;
  };
}
```

Yangi massivni funksiya tanasining o'zada xosil qilib argument sifatida berish mumkin:
```csharp
Multiply(new int[] {3, 5, 8, 12, 21}, 2);
```

Massivni qaytaruvchi qiymat sifatida ifodalaymiz:
```csharp
static int[] GetRandomNums(int n)
{
  int[] arr = new int[n];
  Random random = new Random();

  for (int i = 0; i < n; i++)
  {
    int num;
    do
    {
      num = random.Next(1, n + 1);
    } while (Contains(arr, num));
    arr[i] = num;
  }
  return arr;
}

// n soni arr massivda mavjudliligini tekshiramiz
static bool Contains(int[] arr, int n)
{
  foreach (var item in arr)
  {
    if (item == n) return true;
  }
  return false;
}
```
Ushbu funksiyadan foydalanamiz:
```csharp
int[] randomNumsArr = GetRandomNums(10);
Console.WriteLine(string.Join(" ", randomNumsArr));
```

# Dastur matni

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main()
        {
            int[] numArr = { 3, 5, 8, 12, 21};
            Multiply(numArr, 2);

            int[] randomNumsArr = GetRandomNums(10);
            Console.WriteLine(string.Join(" ", randomNumsArr));
        }

        static void Multiply(int[] numArr, int mul)
        {
            for (int i = 0; i < numArr.Length; i++)
            {
                numArr[i] *= mul;
            };
        }


        static int[] GetRandomNums(int n)
        {
            int[] arr = new int[n];
            Random random = new Random();

            for (int i = 0; i < n; i++)
            {
                int num;
                do
                {
                    num = random.Next(1, n + 1);
                } while (Contains(arr, num));
                arr[i] = num;
            }
            return arr;
        }

        // n sonini arr massivda mavjudliligini tekshiramiz
        static bool Contains(int[] arr, int n)
        {
            foreach (var item in arr)
            {
                if (item == n) return true;
            }
            return false;
        }
    }
}
```
