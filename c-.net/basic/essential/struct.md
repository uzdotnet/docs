---
description: Niyozbek Mirzayev
---
# Struct

Dasturlashga endi kirib kelganlar orasida turli xil yangi atamalarga duch kelish oddiy holat. Shu atamalardan biri bu **Struktura** yoki ingliz tilda **Struct**dir.

C# dasturlash tilida (boshqa dasturlash tillarida ham) ma'lumotlar ikki xil bo'ladi: **value type** va **reference type**. 

**Value type**  tipidagi ma'lumotlar xotirada o'zi ma'lum joy egallab, qiymati yozilgan holda saqlanadi. Bu tipga misol qilib oddiy tiplar: *int, double, char, string, boolean* kabilarni, bundan tashqari **struct**ni ham keltirishimiz mumkin. **Struktura** o'zi ham value type hisoblanadi va value type dagi ma'lumotlarni jamlangan holatda saqlash uchun ishlatiladi. value type turidagi ma'lumotlar **stack** xotirada saqlanadi.

**Reference type**dagi ma'lumotlar esa xotirada saqlanganda o'zi bilan birga qiymatini olib yurmaydi, ular shunchaki xotirada  boshqa ma'lumot yozilgan manzilga ko'rsatkich (havola)ni  o'zida saqlaydi. Reference typega *classlar, interfacelar, delegatlar, massivlar* misol bo'la oladi.  Reference type turidagi ma'lumotlar **heap** xotirada saqlanadi.

Struktura bir nechta o'zaro bog'liq ma'lumotlarni ular orasidagi mantiqiy bog'liqlikni ta'minlagan holda saqlash imkoniyatini beradi. Strukturani tushunishdan avval, undan foydalanmagan holda talabalar haqidagi ma'lumotlarni saqlashga urinib ko'raylik. Bu holatda talabalarga tegishli har bitta ma'lumotni yangi o'zgaruvchiga yuklashimizga to'g'ri keladi:

```csharp
string ism = "Dave";
string familiya = "Thompson";
int yosh = 17;

string ism2 = "Jef";
string familiya2 = "Harrison";
int yosh2 = 23;
```

Lekin bir muammo bor, foydalanuvchilar soni ko'paygani sari har bir foydalanuvchining ma'lumotlarini boshqalari bilan chalkashishini ko'rishimiz mumkin. Sababi ma'lumot ko'p va har bir foydalanuvchining ma'lumoti bir-biriga mantiqiy tomondan bog'lanmagan.

Shu payt Struktura bizga yordamga keladi. U har bir foydalanuvchining ma'lumotlarini xotirada alohida saqlaydi va mantiqan bog'lab beradi. Bu o'z o'rnida dasturchiga qulaylik yaratadi. 

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
ko'rinishida dasturning Main qismida e'lon qilamiz. Uni ma'lumotlar bilan to'ldirish uchun yaratilgan o'zgaruvchini chaqirish, shundan so'ng uni ma'lum xususiyatlar bilan to'ldirish lozim. Buni quyidagicha ko'rsangiz bo'ladi:
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

Natija quyidagi ko'rinishda bo'ladi:
```
Dave
Thompson
17

```

Strukturada ochiq xususiyatlaridan tashqari yashirin xususiyatlarga ham ega bo'lishi mumkin. Buning uchun xususiyatlarni konstruktorda e'lon qilish davomida **public (ommaviy)** o'rnida **private (shaxsiy)** operatoridan foydalanamiz.
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

Shu sababdan shu kabi yashirin xususiyatlarni namoyon qilish yoki ularga qiymat berish uchun maxsus funksiyalar - **event**lar e'lon qilishimiz mumkin. Shunday qilsak, dasturning Main qismida talabaning bu xususiyatiga faqatgina shu **event** orqali murojaat qilish mumkin bo'ladi. Bunday usulda ulanish ma'lumotlar bexosdan o'zgarib ketishini oldini oladi. Misol uchun talabaning faqatgina yoshini ko'rsata oladigan Event quyidagicha bo'ladi: 

```csharp
struct Talaba
{
	public string ism;
	public string familiya;
	private int yosh;

	public int GetAge()
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

Bundan tashqari, **event**lar yordamida o'zgaruvchiga qiymat berishda ma'lum shartlar qo'yish, qo'shimcha amallar bajarish mumkin. Masalan, odatda talabaning yoshi eng kamida 17 yosh bo'ladi deb hisoblasak, yosh o'zgaruvchisiga bundan kichik qiymat berish mumkin bo'lmasin:
```csharp
using System;

namespace Struktura
{
	internal class Program
	{
		static void Main(string[] args)
		{
			
			Talaba talaba1 = new Talaba();			
			talaba1.ism = "Dave";
			talaba1.familiya = "Thompson";		
			talaba1.PutAge(3);  
			//talabaning yoshi 3 ga teng bo'lolmagani uchun, bu talabaning yoshi 17 deb belgilanadi
			
			talaba1.GetAge();
			
			Talaba talaba2 = new Talaba();			
			talaba2.ism = "Jeff";
			talaba2.familiya = "Harrison";		
			talaba2.PutAge(23);			
			talaba2.GetAge();

		}
	}

	//Struktura
	struct Talaba
	{		
		public string ism;
		public string familiya;		
		private int yosh;		
		public void GetAge()
		{
			Console.WriteLine(yosh);
		}
		public void PutAge(int age)
		{
			if (age>16) yosh = age;
			else yosh=17;
		}
	}
}
```
Natija:
```
17
23
```
Ko'rib turganingizdek, **event**lar ma'lumotlar ustidan nazorat qilib turishimizni osonlashtiradi.
