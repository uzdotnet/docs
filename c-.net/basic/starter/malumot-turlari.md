---
description: Abduxoshimov Xondamir
---

# Ma'lumot turlari

Ma’lumotlar toifasi – bu o’zgaruvchilarning turi va xotiradan qancha joy egallashini belgilab beruvchi kerakli omil. Foydalanilgan o’zgaruvchiga to’g’ri tipni belgilash muhim vazifalardan biridir. Sababi bu orqali biz, yaratayotgan dasturimizda yuzaga keladigan ba’zi bir muammolarni oldini olishimiz, eng asosiysi vaqt tejalishi va dasturning xotiradan kamroq joy egallanishiga erishishimiz mumkin. C# dasturlash tili keng ko’lamdagi ma’lumotlar toifasini o’zida mujassamlashtirgan.\
Quyida bir nechta ma’lumotlar toifasiga birikkan holatda o’zgaruvchilarni hosil qilishni ko’rishimiz mumkin:

```csharp
string stringVar = "Salom Dunyo!!";
int intVar = 100;
float floatVar = 10.2f;
char charVar = 'A';
bool boolVar = true;
```

C# da ma’lumotlar toifasi asosan 2 turli bo’ladi: qiymatli(value) va ma’lumotli(reference). Value turdagi toifalarga – odatiy tiplar(sonli(int , float, double…), mantiqiy(bool), belgili(char) va matnli(string)) , enum turlari va strukturalar kabilar kiradi . Reference turdagi toifalar o’z ichiga – classlar, interfeys, delegatlar hamda massiv turlarini oladi.

![Klassifikatsiya](<../../../.gitbook/assets/image (93).png>)

C# da oldindan tashkil qilingan bir qancha tiplar mavjud. Quyidagi jadvalda ulardan ba’zilarini ko’rishimiz mumkin.

![](<../../../.gitbook/assets/image (34).png>)

![](<../../../.gitbook/assets/image (33).png>)

```csharp
// compile time error: Cannot implicitly convert type 'long' to 'int'.
int i = 21474836470
```

### Sonli tiplar

Sonli tiplar o’z o’rnida ikki turga bo’linadi: butun(integer) va haqiqiy(floating point). Butun tiplar – barcha butun, musbat va manfiy (52, -52, 0) sonlarni o’zi ichiga oladi. Bularga misol tariqasida – byte, short , int , long , int32, int64 larni olishimiz mumkin. Haqiqiy tiplar – o’zlarida kasr(1.2, -2.3, 10.5) sonlarni aks ettiradi. Misol uchun : float, double, long double kabi tiplar. C# dasturlash tilida sonli tiplar ko’p bo’lishiga qaramay, int(butun) va double(haqiqiy) tiplari ko’proq foydalaniladi. Quyidagi ko’rinishda sonli tiplarga doir toifalarni ko’rishimiz mumkin.

![](<../../../.gitbook/assets/image (62).png>)

### Butun tiplar

Butun tiplar – barcha musbat va mandiy butun sonlarni o’z ichiga oladi. C# da butun tiplar oilasida 4 ta tip mavjud: _byte,_ _short_, _int_ , _long_. Byte byte tipi 0 dan 255 gacha bo’lgan sonlarni qabul qiladi, xotiradan 8 bitni egallaydi hamda Byte strukturasiga tegishlidur\
sbyte tipi ham byte tipi bilan bir xil , lekin u -128 dan 127 gacha manfiy sonlarni ham o’zida saqlaydi. sbyte – _Sbyte_ strukturasidan o’rin olgan .

```csharp
byte b1 = 255;
byte b2 = -128;// compile-time error: Constant value '-128' cannot be converted to a 'byte'
sbyte sb1 = -128; 
sbyte sb2 = 127; 

Console.WriteLine(Byte.MaxValue);//255
Console.WriteLine(Byte.MinValue);//0
Console.WriteLine(SByte.MaxValue);//127
Console.WriteLine(SByte.MinValue);//-128

```

_**Short**_ \
short tipi -32,768 dan 32,767 gacha bo’lgan sonlarni o’zida jamlaydi, xotiradan egallanadigan joy 16 bit. Int16 stukturasini ichida joylashgan. short tipiga o’xshash ushort tipi ham mavjud. Bu tip 0 dan 65,535 gacha sonlarni qabul qiladi. UInt16 strukturasida joylashgan.

```csharp
short s1 = -32768;
short s2 = 32767;
short s3 = 35000;//Compile-time error: Constant value '35000' cannot be converted to a 'short'

ushort us1 = 65535;
ushort us2 = -32000; //Compile-time error: Constant value '-32000' cannot be converted to a 'ushort'

Console.WriteLine(Int16.MaxValue);//32767
Console.WriteLine(Int16.MinValue);//-32768
Console.WriteLine(UInt16.MaxValue);//65535
Console.WriteLine(UInt16.MinValue);//0
```

_**Int**_ \
int tipi 32 bitlik butun toifadur. Butun sonlarni qabul qilish chegarasi -2,147,483,648 dan 2,147,483,647 gacha. Int32 strukturasida joylashgan. Bu tipga yaqin tip uint tipi. UInt32 strukturasiga tegishli bo’lib 0 dan 4,294,967,295 gacha sonlarni o’z ichiga oladi.

```csharp
int i = -2147483648;
int j = 2147483647;
int k = 4294967295; //Compile-time error: Cannot implicitly convert type 'uint' to 'int'.

uint ui1 = 4294967295;
uint ui2 =-1; //Compile-time error: Constant value '-1' cannot be converted to a 'uint'

Console.WriteLine(Int32.MaxValue);//2147483647
Console.WriteLine(Int32.MinValue);//-2147483648
Console.WriteLine(UInt32.MaxValue);//4294967295
Console.WriteLine(UInt32.MinValue);//0
```

int toifasi o’n oltilik va ikkilik sanoq sistemalariga nisbatan ham foydalaniladi. O’n oltilik sanoq sistemalari 0x yoki 0X qo’shimchalari bilan, ikkilikdagi sonlar esa, 0b yoki 0B bilan boshlanadi.

```csharp
int hex = 0x2F;
int binary = 0b_0010_1111;

Console.WriteLine(hex);
Console.WriteLine(binary);
```

_**Long**_\
long tipi o’zida -9,223,372,036,854,775,808 dan 9,223,372,036,854,775,807 gacha sonlarni saqlaydi. Xotiradan egallaydigan joyi 64 bitni tashkil etadi. Int64 strukturasida joylashgan. ulong tipi ham long tipi bilan o’xshash. U o’zida 0 dan 18,446,744,073,709,551,615 gacha sonlarni qabul qiladi. Int64 strukturasida joylashgan.

```csharp
long l1 = -9223372036854775808;
long l2 = 9223372036854775807;

ulong ul1 = 18223372036854775808ul;
ulong ul2 = 18223372036854775808UL;

Console.WriteLine(Int64.MaxValue);//9223372036854775807
Console.WriteLine(Int64.MinValue);//-9223372036854775808
Console.WriteLine(UInt64.MaxValue);//18446744073709551615
Console.WriteLine(UInt64.MinValue);//0
```

### Haqiqiy tiplar

Haqiqiy toifalar o’zida musbat va manfiy o’nli kasrlarni aks ettiradi. C# da haqiqiy toifalar asosan 3 turli: float, double va decimal \
\
_**Float**_ \
float tipi xotiradan 4 baytni egallaydi. Single strukturasiga tegishli. float toifadagi tipni hosil qilish uchun f yoki F suffiksidan foydalaniladi.

```csharp
float f1 = 123456.5F;
float f2 = 1.123456f;

Console.WriteLine(f1);//123456.5
Console.WriteLine(f2);//1.123456
```

_**Double**_ \
double tipi float tipiga qaraganda imkoniyati kattaroq, lekin xotiradan 8 bayt egallaydi. Double strukturasida joylashgan. double toifadagi tipni hosil qilish uchun d yoki D suffiksidan foydalaniladi.

```csharp
double d1 = 12345678912345.5d;
double d2 = 1.123456789123456D;

Console.WriteLine(d1);//12345678912345.5
Console.WriteLine(d2);//1.123456789123456
```

_**Decimal**_ \
decimal tipi xotiradan boshqa tiplarga qaraganda balandroq joy egallaydi. Egallanadigan joy 16 bayt. Bu tip asosan moliya sohalaridagi dasturlarda ko’proq foydalaniladi. decimal toifadagi tipni hosil qilish uchun m yoki M suffiksidan foydalaniladi.

```csharp
decimal d1 = 123456789123456789123456789.5m;
decimal d2 = 1.1234567891345679123456789123m;

Console.WriteLine(d1);
Console.WriteLine(d2);
```
