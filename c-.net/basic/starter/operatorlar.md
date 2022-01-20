---
description: Suxrob Xayitmurodov
---

# Operatorlar

Bu maqolamda men operatorlar haqida qisman ma'lumot berib o'taman.

Operatorlar odatda harakat yoki jarayonni (harakat va jarayonni ham bo’lishi mumkin) ifodalovchi belgidir. Ular matematika va logikani yaxshi biladigan har qanday inson uchun muammo tug’dirmaydi. Ya’ni ularning asosini aynan shular tashkil qiladi. Operatorlar ma’lum bir qiymat yoki operandlarni boshqarishga qodir bo’ladi. Operatorlar har qanday dasturlash tilining asosini tashkil qiladi. Ular oddiy hisoblashlardan tortib, hattoki xavsizlikni shifrlash kabi murakkab algoritmik vazifalarni ham bajara oladi!

### C# dasturlash tilida operatorlar nechta?

Asosan 5 xil turi mavjud:

* Arifmetik operatorlar
* Mantiqiy operatorlar
* Shart operatorlar
* Tanlash operatorlar
* Takrorlash operatorlar

### Ular haqida qisman ma'lumot beraman degan edingiz!?

1. Arifmetik operatorlar bizga arifmetik amallar qilish imkonini beradi. Ya’ni biz bunda 5 arifmetik amallarni bajara olamiz.

```csharp
int result; 
int x = 10, y = 5; 
              
    // Addition 
    result = (x + y); 
    Console.WriteLine("Addition Operator: " + result); 
              
    // Subtraction 
    result = (x - y); 
    Console.WriteLine("Subtraction Operator: " + result); 
```

2\. Mantiqiy operatorlarda biz mantiqiy amallar ustida ishlaymiz. Agar qiymat to’g’ri bo’lsa true aks holda false qiymatini qaytaradi.

```csharp
int x = 5, y = 10, result; 
              
  // To find which value is greater 
  // Using Conditional Operator 
  result = x > y ? x : y;  
              
  // To display the result  
  Console.WriteLine("Result: " + result); 
           
  // To find which value is smaller 
  // Using Conditional Operator 
  result = x < y ? x : y;  
              
  // To display the result 
  Console.WriteLine("Result: " + result); 
```

3\. Qachonki e’lon qilingan bir qancha qiymatlar bo’lsa, ushbu operator o’ziga mos qiymatni tanlashda va uni amalga oshirishda ishlatiladi

```csharp
int day = 2;
switch(day) 
{
    case 1:
	Console.WriteLine(“Monday”);
	break;
    case 2:
	Console.WriteLine(“Tuesday”);
	break;
    default:
	Console.WriteLine(“Wrong day!”);
	break;
}
```

{% hint style="info" %}
Agarda ushbu ma'lumotlar sizga tushunarli bo'lgan bo'lsa bundan men xursandman. Agarda ularni eslab qolgan bo'lsangiz men juda ham xursandman. \
Agarda tushunmagan bo'lsangiz kuyinmang, ushbu operatorlar bilan hali maqolalarimizda batafsil tanishib olasiz
{% endhint %}
