---
description: Sarvarbek Mumtozbekov
---

# Vector

C++03 da taqdim etilgan std::vector – bu o‘ziga ajratilgan xotirani o‘zi boshqara oladigan dinamik massiv. std::vector quyidagicha e‘lon qilinadi:
```cpp
#include <vector>
 
// uzunligini oldindan ko‘rsatish shart emas
std::vector<int> array; 
std::vector<int> array2 = { 10, 8, 6, 4, 2, 1 }; //initializer list orqali qiymat berish
std::vector<int> array3 { 10, 8, 6, 4, 2, 1 }; // uniform-initiaizatsiya orqali qiymat berish (C++11 dan boshlab)
```

 Etibor bering, initsializatsiya qilingan hollarda siz massivlar uzunligini aniq belgilashingiz shart emas. Buning sababi shundaki, std::vector dinamik ravishda o'z ichidagilar uchun talabga binoan xotira ajratadi.

## “Memory leak” yo‘q!
Vektor o‘zgaruvchisi qo‘llanilish doirasidan tashqariga chiqqanda, u o‘zi boshqargan (egallab olgan) xotirani avtomatik ravishda bo'shatadi. Bu nafaqat qulay (chunki buni qo‘lda qilishingiz shart emas), balki “Memory leak”ning oldini olishga ham yordam beradi. Quyidagi parchani ko‘rib chiqing:
```cpp
void doSomething(bool value)
{
    int *array = new int[7] { 12, 10, 8, 6, 4, 2, 1 };
 
    if (value)
        return;
 
   // nimadir qilamiz
 
    delete[] array; // agar value=true bo'lsa bu amal hech qachon bajarilmaydi
}
```

Agar value = true bo‘lsa array hech qachon xotiradan o‘chirilmaydi va “**Memory leak**” bo‘ladi.
Biroq, agar massiv vektor bo‘lsa, unda bu hech qachon sodir bo‘lmaydi, chunki vektor qo‘llanilish doirasidan tashqariga chiqqanda xotira avtomatik ravishda bo‘shatiladi (funktsiya avvalroq doiradan chiqib ketganmi yoki yo‘qligidan qat'iy nazar). Shu sababli std::vector dan foydalanish **new** operatori orqali dinamik xotira ajratishga qaraganda xavfsizroqdir.

## Vektorning uzunligi
Uzunligini bilmaydigan standart dinamik massivlardan farqli o‘laroq, std::vector o‘zining uzunligini eslab qoladi. Buni bilish uchun size() funksiyasidan foydalanishingiz kerak:
```cpp
#include <vector>
#include <iostream>
 
int main()
{
    std::vector<int> array { 12, 10, 8, 6, 4, 2, 1 };
    std::cout << "Uzunligi: " << array.size() << '\n';
 
    return 0;
}
```
Natija:
```
Uzunligi: 7
```

Standart dinamik ravishda ajratilgan massiv uzunligini o‘zgartirish juda muammoli va qiyin. std::vector uzunligini o‘zgartirish **resize()** funksiyasini chaqirish orqali oson:
```cpp
#include <vector>
#include <iostream>
 
int main()
{
    std::vector<int> array { 0, 1, 2 };
    array.resize(7); // array uzunligini 7 gа o'zgartirdik
 
    std::cout << "Uzunligi: " << array.size() << '\n';
 
    for (auto const &element: array)
        std::cout << element << ' ';
 
    return 0;
}
```
Natija:
```
Uzunligi: 7
0 1 2 0 0 0 0
```
Vektor uzunligini o‘zgartirish qimmat operatsiya hisoblanadi, shuning uchun siz bunday operatsiyalar sonini kamaytirishga harakat qilishingiz kerak.
