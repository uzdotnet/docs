---
description: Niyozbek Mirzayev
---
# Sealed

C# dasturlash tilida **Sealed class** tushunchasi mavjud. 
{% hint style="info" %}
**Sealed class** deb o'zidan voris (inheritance) qoldirmaydigan classlarga aytiladi. Sealed class yaratish uchun C# dasturlash tilida class yozuvidan oldin **sealed** kalit so'zini yozish lozim. Sealed kalit so'zi kompilyator uchun bu classdan voris olib bo'lmasligini bildiradi.
{% endhint %}


Sealed classga misol: 
```csharp
	sealed class class_nomi
	{
	    // xususiylatlar
	    // methodlar
	
	}
```


Quyidagi kodda sealed classdan voris olishga harakat qilingan:
```csharp
namespace Sealed_Class
{
	internal class Program
	{
		static void Main(string[] args)
		{
			//....
		}

		// sealed classni yaratish
		public sealed class Class_nomi1
		{
			//....
		}

		//seled klassdan voris olishga harakat qilish
		public class Class_nomi2 : Class_nomi1
    		{
			//...
		}
	}
}
```

 Agar kod ishga tushirilsa natija quyidagicha bo'ladi:

```
💡 error CS0509: 'Class_nomi2': cannot derive from sealed type 'Class_nomi1'
```
{% hint style="info" %}
Methodlar ham sealed bo'lishi mumkin, lekin sealed qilingan methodning classi, biror-bir classning vorisi bo'lishi lozim. Methodni sealed qilinishidan asosiy maqsad: voris classdagi methodni override qilishdan himoya qilish.
{% endhint %}
(Override yoki shu kabi tamoyillar haqida bilmasangiz, oldingi maqolalarni ko'rishingiz mumkin.)

Tushunishga qiyin bo'lishi mumkin, ammo quyidagi kodda tushunish osonroq:

```csharp
namespace Sealed_Class
{
	internal class Program
	{

		static void Main(string[] args)
		{
			//....
		}

		public class Asosiy
		{
			// voris bo'ladigan method
			 public virtual int Add(int a, int b)
			 {
				  return a + b;
			 }
		}

		//asosiy classdan voris olish
		public class Voris1 : Asosiy
    		{
			//voris bo'lgan methodni sealed qilish
			public sealed override int Add(int a, int b)
			{
				return a + b;
			}
		}
	}
}
```

Yuqoridagi kodda voris bo'lgan method polymorphism yordamida sealed qilindi, yani Voris1 classidagi Add methodini boshqa classda voris olib bo'lmasligi ta'minlandi. 

Quyidagi kodda, esa yuqoridagi kodning sealed qilingan methodidan voris olishga harakat qilingan:

```csharp
namespace Sealed_Class
{
	internal class Program
	{	
		static void Main(string[] args)
		{
			//....
		}

		public class Asosiy
		{
			// voris bo'ladigan method
			 public virtual int Add(int a, int b)
			 {
				  return a + b;
			 }
		}

		//asosiy classdan voris olish
		public class Voris1 : Asosiy
		{
			//voris bo'lgan methodni sealed qilish
			public sealed override int Add(int a, int b)
			{
				return a + b;
			}
		}
		
		public class Voris2 : Voris1
		{
			//sealed bo'lgan methoddan voris olishga urinish
			public override int Add(int a, int b)
			{
				return a + b;
			}
		}
	}
}
```

Natija quydagicha bo'ladi:
```
💡 error CS0239: 'Program.Voris2.Add(int, int)': cannot override inherited member 'Program.Voris1.Add(int, int)' because it is sealed.
```
