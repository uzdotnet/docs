---
description: Niyozbek Mirzayev
---
# Struct

Dasturlashga endi kirib kelganlar orasida turli xil yangi atamalarga duch kelish oddiy holat. Shu atamalardan biri bu **Struktura** yoki ingliz tilda **Struct** dir.

C# dasturlash tilida(**boshqa dasturlash tillarida ham**) turli tiplar mavjud va shu orada tiplar asosan ikkiga bo'linadi: **value type** va **reference type**. **Value type**ga *int*, *float* yoki *char* va shu kabilarni misol keltirishimiz mumkin, bu tiplar faqat bitta ma'lumotni qabul oladi. Lekin **reference type**  birdan oshiq ma'lumotlarni o'z ichiga sig'dira oladi.

Struktura ham **reference type**ga kiradi va u o'ziga har xil **value type**dagi ma'lumotlarni qabul qiladi. Xo'sh, bu bizga nega kerak? Tasavvur qiling, siz o'z dasturingiz foydalanuvchilarining ma'lumotlarni saqlab qo'ymoqchisiz va har bir foydalanuvchining ma'lumotlari quyidagi ko'rinishda bo'ladi:

```csharp
string ism = "Dave";
string familiya = "Thompson";
int yosh = 17;

string ism2 = "Jef";
string familiya2 = "Harrison";
int yosh2 = 23;
```

Lekin bir muammo bor, foydalanuvchilar soni ko'paygani sari har bir foydalanuvchining ma'lumotlarini boshqalari bilan chalkashishini ko'rishimiz mumkin. Sababi ma'lumot ko'p va har bir foydalanuvchining ma'lumoti bir-biriga mantiqiy tomondan bog'lanmagan.

Shu payt Struktura bizga yordamga keladi. U har bir foydalanuvchining ma'lumotlarini xotirada alohida saqlaydi va mantiq bog'lab beradi. Bu o'z o'rnida dasturchiga qulaylik yaratadi. 

Misol uchun yuqoridagi kod Struktura yordamida quyidagi ko'rinishga keladi:

```csharp
foydalanuvchi1
{
   string ism = "Dave";
   string familiya = "Thompson";
   int yosh = 17;
};

foydalanuvchi2
{
   string ism = "Jeff";
   string familiya = "Harrison";
   int yosh = 23;
};
```

**Keling, C# dasturlash tilida Struktura qanday ishlatilishini ko'rib chiqamiz.**

Birinchi o'rinda Struktura yaratish **struct** kalit so'zini yozish bilan boshlanadi, shundan so'ng, uning nomi va uning xususiyatlarni e'lon qilishimiz lozim. Misol uchun, **Talaba** nomli Struktura quyidagicha ko'rinishga ega bo'ladi:

```csharp
struct Talaba
{
    public string ism;
    public string familiya;
    public int yosh;
}
```

Talaba Strukturasini huddi qolip kabi tasavvur qiling. Lekin sezganingizdek biz faqat qolip yasadik. Undan hali birorta ham o'zgaruvchi yaratganimiz yo'q. Shu qolip asosida o'zgaruvchi yaratish uchun:

```csharp
Talaba talaba1 = new Talaba();
```
operatorini asosan dasturning Main qismida e'lon qilamiz. Uni ma'lumotlar bilan to'ldirish uchun yaratilgan o'zgaruvchini chaqirish, shundan so'ng uni ma'lum xususiyatlar bilan to'ldirish lozim.
Buni quyidagicha ko'rsangiz bo'ladi:
```csharp
talaba1.ism = "Dave";
talaba1.familiya = "Thompson";
talaba1.yosh = 17;
```

Kiritilgan xususiyatlarni Consoleda chiqarish uchun quyidagi funksiyadan foydalanish kifoya.

```csharp
Console.WriteLine(talaba1.ism)
Console.WriteLine(talaba1.familiya)
Console.WriteLine(talaba1.yosh)
```

Bu Consoleda quyidagi ko'rinishda bo'ladi:

```
Dave
Thompson
17

```

Strukturada ochiq xususiyatlaridan tashqari yashirin xususiyatlarga ham ega bo'lishi mumkin. Buning uchun xususiyatlarni konstruktorda e'lon qilish davomida **public(ommaviy)** o'rnida **private(shaxsiy)** operatoridan foydalanamiz.
Bu hodisani quyidagi kodda, **yosh** public xususiyatini private xususiyatga o'zgartishi orqali ko'rishimiz mumkin:
```csharp
struct Talaba
{
    public string ism;
    public string familiya;
    private int yosh;
}
```

Hozirdan boshlab talabaning yoshini dasturda ishlata olmaymiz. Lekin, ma'lumotni ishlata olmasak nima keragi bor, to'g'rimi?

Shu sababdan shu kabi yashirin xususiyatlarni namoyon qilish yoki ularga qiymat berish uchun maxsus funksiyalar - **Event**lar e'lon qilishimiz mumkun. Misol uchun talabaning faqatgina yoshini ko'rsata oladigan Event quyidagicha bo'ladi: 

```csharp
struct Talaba
{
	public string ism;
	public string familiya;
	private int yosh;

	public void GetAge()
	{
		return yosh;
	}
}

```

Quyida foydalanuvchi yoshini e'lon qiluvchi va uni Consoleda chiqaruvchi Eventlar va Strukuraning to'liq ko'rinishi:

```csharp
using System;

namespace Struktura
{
	internal class Program
	{
		static void Main(string[] args)
		{
			//talaba strukturasidan o'zgaruvchi yasash
			Talaba talaba1 = new Talaba();

			//ochiq xususiyatlarga qiymat berish
			talaba1.ism = "Dave";
			talaba1.familiya = "Thompson";

			//foydalanuvchining taxminiy yoshini kiritish
			int yosh = 17;

			//olingan qiymatni Eventga yuborish
			talaba1.PutAge(yosh);

			//private xususiyani Event orqali Consolega chiqarish
			talaba1.GetAge();

		}
	}

	//Struktura
	struct Talaba
	{
		//ochiq xususiyatlar-public properties
		public string ism;
		public string familiya;

		//yashirin xususiyatlar-private properties
		private int yosh;

		//yashirin xususiyatni(yosh) ko'rsatuvchi Event
		public void GetAge()
		{
			Console.WriteLine(yosh);
		}

		//Yashirin xususiyatga(yosh) qiymat beruvchi Event
		public void PutAge(int age)
		{
			yosh = age;
		}
	}
}
```

Consoleda natija quyidagicha bo'ladi:

```
17
```
