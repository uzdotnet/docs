---
description: Sarvarbek Mumtozbekov
---
# Konteynerlar

## STL konteynerlari
Shubhasiz STL kutubxonasining eng ko'p qo'llaniladigan funksiyanali konteyner sinflari (yoki ularni "konteynerlar" deb ham atashadi). STL turli vaziyatlarda ishlatilishi mumkin bo'lgan turli xil konteyner sinflarini o'z ichiga oladi. Umuman olganda, STL konteynerlari uchta asosiy toifaga va adapterlarga bo'linadi:

1.	Ketma-ket;
2.	Assotsiativ;
3.	Tartibsiz assotsiativ.

## Ketma-ket konteynerlar
Ketma-ket konteynerlar (yoki "ketma-ketlik konteynerlari") elementlari ketma-ket joylashgan konteyner sinflari. Ularning o'ziga xos xususiyati shundaki, siz elementingizni konteynerning istalgan joyiga qo'shishingiz mumkin. Ketma-ket konteynerning eng keng tarqalgan misoli massivdir: massivga 4 ta element qo'shsangiz, bu elementlar (massivda) aynan siz qo'shgan tartibda bo'ladi.

C++ 11 dan boshlab, STL 5 ta ketma-ketlik konteynerlarini o'z ichiga oladi:
1.	std::vector;
2.	std::deque;
3.	std::massiv;
4.	std::list;
5.	std::forward_list;

## Assotsiativ konteynerlar
Assotsiativ konteynerlar - konteyner sinflari bo'lib, ularning barcha elementlarini (shu jumladan siz qo'shganlarni ham) avtomatik ravishda tartiblaydi. Assotsiativ konteynerlar taqqoslash operatori < yordamida elementlarni tartiblaydi.

1.	std::set;
2.	std::map;
3.	std::multiset;
4.	std:multimap;
	
## Tartibsiz assotsiativ konteynerlar
Tartibsiz assotsiativ konteynerlar tartibsiz (xeshlangan) ma'lumotlar tuzilmalari, tezkor qidirish imkoniyatlariga ega (o'rtacha murakkablik O(1), eng yomon holat O(n)) amalga oshiradi.
1.	std::unordered_set;
2.	std:: unordered_map;
3.	std:: unordered_multiset;
4.	std: unordered_multimap;

## Adapterlar
Adapterlar - bu muayyan vazifalarni bajarish uchun mo'ljallangan, oldindan belgilangan maxsus konteyner sinflari.
1.	std::stack;
2.	std::queue;
3.	std::priority_queue;
4.	std::span (C++20)
