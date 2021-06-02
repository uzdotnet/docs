---
description: Xolbek Xoliyorov
---

# Funksiya

C\# dasturlash tilida funksiyalar nimaligini o’rganishdan oldin funksiyaning o’zi nima u bizga nega kerak degan savollarga javob topamiz.  
  
**Funksiya nega kerak ?**  
Biz biroz yirikroq dastur yozish mobaynida juda ko’p bir xil bo’lgan vazifani qayta va qayta yozayotgandek bo’lamiz. Bu xuddi kuni bilan paxta terayotgan kishining ishiga o’xshaydi qaniydi bitta robot bo’lsayu unga bir marta paxta terishni o’rgatib qo’ysak keyin har safar aytganingda paxtani terib qo’ysa deb orzu qiladi paxta teruvchi , albatta terimchining bu orzusini amalga oshirish qiyin . Lekin sizning ishingizni \(ya’ni kodlashda bir vazifani qayta yozishni\) yengillashtirishning yo’li bor , bu yerda bizga Funksiyalar yordamga keladi  
  
**Funksiya nima?**  
Bir marta kod yozib uni dasturning istalgan joyida istalgancha ishlatish imkonini beruvchi operatorlar guruhi Funksiya deyiladi. Bu huddi yuqoridagi misolimizga o’xshash bir marta qanday qilishni o’rgat va xoxlagan vaqting xoxlagan joyingda ishlat. Funksiya dasturchining kodini sezilarni darajada qisqartiradi va bu orqali dastur kodini o’qish osonlashadi va qotira hajmidan ham yutiladi.  
  
**C\# da funksiyadan foydalanish**  
Dasturlashda funksiyalar ikki toifaga bo’linadi  
• Qiymat qaytaruvchi   
• Qiymat qaytarmaydigan

Dastlab biz **qiymat qaytaruvchi funksiyalar** ni ko’rib chiqamiz. Qiymat qaytaruvchi funksiyalar malum bir qiymatni \(int ,float ,string va boshq\) qaytaradi Qiymat qaytaruvchi funksiya larning tuzilishini ko’ramiz

 

![](../../../.gitbook/assets/image%20%2857%29.png)

Bularning barchasiga alohida to’xtalib o’tamiz   
1.  - bu funksiya qaytaradigan qiymat bo’lib turli xil ma’lumot turlaridan foydalanishimiz mumkin masalan int, float string kabilar.  
2.  - funksiyaning nomi yani uni chaqiradigan ism deyishimiz ham mumkin unga ism tanlayotganda lotin alifbosidagi katta va kichik harflar , raqamlar va tagchiziq \(‘\_’\) foydalangan holda , raqamdan boshlamasdan va c\# tilidagi kalit so’zlardan foydalanmagan holda xoxlagan ismni berishimiz mumkin.   
3. \(&lt;parametrlar&gt;\) – bu funksiya yakuniy qiymatni yaratish uchun foydalanadigan yordamchilar deyishimiz mumkin ushbu yordamchilar sifatida esa turli xil malumot tipidagi o’zgaruvchilar keladi . yordamchilar sifatida 0 tadan xoxlagancha o’zgaruvchilar bo’lishi mumkin ular quyidagicha yoziladi \(int a, float b, int c\) . 4. // funksiya tanasi - ushbu qism funksiyaning asosiy qismi hisoblaning qaytariladigan yakuniy qiymatgacha bo’lgan barcha ishlar shu yerda qilinadi va figurali qavs \(‘{‘\) bilan boshlanadi ushbu qismda parametr sifatida kiritilgan o’zgaruvchilar ham ishlatiladi.   
5. // return  - ushbu amal biz funksiyaning qaytaradigan qiymatini aniqlaydi.  ning turi funksiyada elon qilingan dastlabki qiymat bilan bir xil bo’lishi shart.yani funksiya int turida bo’lsa biz return dan keyin ham int turidagi o’zgaruvchi bo’ladi.   
Ming marta eshitgandan ko’ra bir marta ko’rgan yaxshi deganlaridek biz C\# tilida Funksiya ga oddiygana ikki sonda kattasini topuvchi funksiya orqali misol keltiramiz

```csharp
int max( int a , int b)
{
	int max;
	if(a>b) max = a;
	else max = b;
	return max;
}
```

**C\# Console dasturida funksiyadan foydalanish**

```csharp
using System;
namespace function_test
{
    class Program
    {
       
        static void Main(string[] args)
        {
            int a = 5, b = 8;
            Console.WriteLine(max(a, b));
            Console.ReadKey();
        }
        static  int max(int a, int b)
        {
            int max;
            if (a > b)
                max = a;
            else
                max = b;
            return max;
        }        
    }
}
```

output: 8

Yuqorida console dasturida max yani ikki sondan kattasini topuvchi funksiya yaratildi va undan dasturning Main qismida foydalanildi. Albatta bu yerda funksiyaning foydasi yaqqol sezilmagandir ammo siz dastur ichida funksiyani bir necha marotaba foydalansangiz naqadar foydali ekanligini tushunasiz.

**Qiymat qaytarmaydigan funksiyalar**  
Agar biz funksiyalarni xizmatchi inson deb bilsak qiymat qaytaradigan va qaytarmaydigan funksiyalarni shunday tariflashimiz mumkin . Deylik xizmatchiga qanchadir pul\(ya’ni parametr\) berib do’konga jo’natamiz va bizga aytgan narsamizni \(qaytaradigan qiymat\) ni olib keladi bu qiymat qaytaradigan funksiyaga misol bo’ladi . boshqa xizmatchiga esa pul\(ya’ni parametr\) berib unga hovlidagi qandaydir ishlarni aytamiz va u aytgan ishlaringizni qildi lekin sizga hech narsa qaytarib kelmadi bu qiymat qaytarmaydigan funksiyaga misol bo’la oladi. Qisqa qilib aytganda qiymat qaytarmaydigan funksiyaning qaytaruvchi qiymati bo’lmaydi va u qandaydir vazifani bajargan bo’ladi.

Endi esa qiymat qaytarmaydigan funksiyalarning tuzilishini ko’rib chiqamiz

![](../../../.gitbook/assets/image%20%283%29.png)

Qiymat qaytarmaydigan funksiyaning qiymat qaytaradigan funksiyadan asosiy farqi bu funksiyalar qaytariladigan qiymat turi o’rniga ‘void’ kalit so’zi bilan boshlanadi va qaytariladigan qiymat return yozilmaydi. Endi esa qiymat qaytarmaydigan funksiyaga misol yozamiz

```csharp
void print(string s,int n)
{
    for(int i=0;i<n;i++)
		    Console.WriteLine(s);
}
```

Bu shunchaki s matnni n marta takma tak chiqaruvchi funksiya Bundan foydalanishni yana console dasturda ham ko’ramiz.

```csharp
using System;
namespace function1
{
    class Program
    {
       
        static void Main(string[] args)
        {
            string text = "dot-net.uz";
	          int n = 3;
            print(text, n);
        }

        static void print(string s, int n)
        {
            for(int i = 0; i < n; i++)
          	Console.Write(s + " ");
        }
       
    }
}
```

Output: dot-net.uz dot-net.uz dot-net.uz

Xulosa qilib aytadigan bo’lsak funksilar bizning og’irimizni yengil uzog’imizni yaqin qiluvchi yordamchi zamonaviy dasturlash tillarini funksiyalarsiz tasavvur qilib bo’lmaydi . Katta loyiha qila turib funksiyalardan foydalanmaslikni yangi uyni faqat qo’l mehnati bilan qurmoqchi bo’lgan inson harakati bilan o’xshatish mumkin. Bu boshlanishi edi keyingi darslarda funksiyalarga yanada kengroq to’xtalamiz.

