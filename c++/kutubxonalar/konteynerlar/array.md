---
description: Sarvarbek Mumtozbekov
---

# std::array
C++ 11 da kiritilgan std::array – bu funksiyaga o‘tkazilganda ko‘rsatgichga aylanmaydigan o‘zgarmas massiv.  std:array o‘zgaruvchisi quyidagicha elon qilinadi:
```cpp
#include <array>
std::array<int, 4> myarray; // int turida uzunligi 4 bo'lgan massiv elon qildik 
```

Oddiy massivlar singari, std::array uzunligi kompilyatsiya vaqtida o‘rnatilishi kerak. std::array ishga initializer ro‘yxati yoki uniform-initiaizatsiya  yordamida yaratish mumkin:
```cpp
std::array<int, 4> myarray = { 8, 6, 4, 1 }; // initializer ro‘yxati
std::array<int, 4> myarray2 { 8, 6, 4, 1 }; // uniform-initiaizatsiya
```

Massiv qiymatlariga odatdagidek indeks operatori orqali murojaat qilish mumkin:
```cpp
std::cout << myarray[1];
myarray[2] = 7;
```
Xuddi standart massivlardagi kabi, indeks operatori diapazonga tekshirmaydi. Agar noto‘g‘ri indeks ko‘rsatilgan bo‘lsa, yomon narsalar sodir bo‘lishi mumkin :).


std::array da elementga murojaat qilishning yana bir yo‘li bor, bunda **at()** funksiyasi yordam beradi. **at()**  funksiyasining oddiy indeks operatoridan farqi shundaki, bu funksiya diapazonga tekshiradi. Xato indeks kiritilganda std::out_of_range exception tashlaydi.


**size()** funksiyasi yordamida massiv o‘lchamini bilib olish mumkin.
```cpp
std::array<double, 4> myarray{ 8.0, 6.4, 4.3, 1.9 };
std::cout << "length: " << myarray.size();
```
natija: 4


### Xulosa
std::array standart massivlar uchun ajoyib o'rinbosar. std::array bilan yaratilgan massivlar samaraliroq, chunki ular kamroq xotiradan foydalanadi. std::array ning standart massivlardan yagona kamchiliklari biroz noqulay sintaksis va siz massiv uzunligini aniq ko'rsatishingiz kerakligidir (kompilyator uni biz uchun hisoblab chiqmaydi). Ammo bu nisbatan kichik noqulaylik. Har qanday noaniq vazifalarda standart massivlar o'rniga std::array dan foydalanish tavsiya etiladi.
