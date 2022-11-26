---
description: Ro'zimurod Abdunazarov
---

# Dapper

Dapper - bu SQL so'rovlari natijalarini C# sinflari bilan taqqoslaydigan almashinuv vositasi. Ishlash tizimi EntityFreamwork ga ham o’xshaydi,ammo undan tezroq ishlaydi. Hammamiz biladigan https://stackoverflow.com/ saytining qidiruv tizimi ham Dapper yordamida tuzilgan. 

Shuningdek Dapper oldingi Ado.Net ning avlodi hisoblanadi.Shuning uchun ham tuzilma Ado.Net bilan juda o'xshash. 

Endi amaliyot bilan shug’ullansak, Man Dapper bilan ishlash ko’nikmasini shakllantirish uchun,kompyuterni uncha qiynamaydigan bir nechta dasturlarni o’rnatib olaman.VsCode, MsSqlLocalDb, Dotnet lar bo’lsa bo’ldi.

![](https://user-images.githubusercontent.com/91861166/204102947-97bf06ba-0e34-4ce0-991d-50420dbf0f8d.png)

```
dotnet new mvc –o DapperApp
```

![](https://user-images.githubusercontent.com/91861166/204103002-6872f186-1705-4db0-a2e9-58a153ae544a.png)

Loyihaga yangi kutubxonalarni qo’shamiz:
```
dotnet add package Microsoft.Data.SqlClient
dotnet add package Dapper
```

Yangi ma'lumotlar bazasi qurib olamiz:
```sql
CREATE DATABASE Users
```

Yangi jadval quramiz. (Bu kodlar faqat MsSql uchun)
```sql
CREATE TABLE People (
    Id INT PRIMARY KEY,
    FullName VARCHAR(MAX),
    Age INT NOT NULL,
    Email VARCHAR(MAX) NOT NULL
);
```

Jadvalni to’ldiramiz. (Bu kodlar faqat MsSql uchun)
```sql
INSERT INTO People VALUES 
   (1,'Ruzimurod Abdunazarov',19,'ruzimurodabdunazarov2003@mail.ru');
INSERT INTO People VALUES 
   (2,'Eldor Axmedov',18,'eldor04@mail.ru');
INSERT INTO People VALUES 
   (3,'Umid Abdusattorov',35,'umid.abdusattorov@mail.ru');
INSERT INTO People VALUES 
   (4,NULL,11,'testor06@mail.ru');
INSERT INTO People VALUES 
   (5,'Farzona Holmo''minova',16,'farzona2007@mail.ru');
INSERT INTO People VALUES 
   (6,'Doston Ibragimov',30,'dostonI23@mail.ru');
INSERT INTO People VALUES    
   (7,'Jasur Tursunov',25,'jasur13@mail.ru');
INSERT INTO People VALUES    
   (8,NULL,24,'testor2@mail.ru');
INSERT INTO People VALUES    
   (9,'Mohichexra Davronova',16,'mohichexra2007@mail.ru');
INSERT INTO People VALUES    
   (10,'Davron Sattorov',26,'davron165@mail.ru');
```

Keyin umumiy malumotlar ombori quyidagicha bo’ladi:

![](https://user-images.githubusercontent.com/91861166/204103131-24069c1b-3c5a-494b-aae3-8f30b1e7d183.png)

Bu malumotlar asosida yangi model tuzib olamiz.
```csharp
public class User
{
    public int Id { get; set; }
    [DisplayName("Ф.И.О")]
    public string? FullName { get; set; }
    [DisplayName("Возраст")]
    public int Age { get; set; }
    [DisplayName("Электронная почта")]
    [Required]
    public string? Email { get; set; }
}
```

Keyingi bosqichda malumotlar bazasidan malumot olib kelish uchun Dapper ORM(Object Relation Mapper) dan foydalanamiz.
```csharp
public interface IUserRepository
{
    int MaxId { get; }
    void Create(User user);
    void Delete(int id);
    User Get(int id);
    List<User> GetAll();
    void Update(User user);
    int Count { get; }
}
```

Birinchi _IUserRepository_ interfeysini qurib olamiz. 
Endi _UserRepository_ ni yozamiz. Kodlar asosan SQL ni o’zidagi Query da yoziladi, shuning uchun ham `Dapper EfCore` ga qaraganda tezroq ishlaydi.

1] Umumiy barcha User larni olib kelish uchun quyidagicha qilamiz.
```csharp
public List<User> GetAll()
{
    using (IDbConnection db = new SqlConnection(_connectionString))
    {
        return db.Query<User>("SELECT * FROM People").ToList();
    }
}
```

Shu yerda bir narsaga e’tibor bering: 
```SELECT * FROM People``` umumiy malumotlarni olib keldi. **Query()** buyrug'i buni object ga aylantirayapti.

2] Aynan qaysidir Userni olib kelish uchun (SQL da SELECT buyruqi yordamida)
```csharp
public User Get(int id)
{
    using (IDbConnection db = new SqlConnection(_connectionString))
    {
        return db.QuerySingleOrDefault<User>("SELECT * FROM People WHERE Id = @id", new { id }) ?? new User { };
    }
}
```
Bu yerda **QuerySingleOrDefault()** metodi bitta id parametrini Id ga tenglayapti.

3] Yangi User qo’shish uchun (SQL da INSERT buyruqi yordamida)
```csharp
public void Create(User user)
{
    using (IDbConnection db = new SqlConnection(_connectionString))
    {
        var sqlQuery = "INSERT INTO People VALUES(@Id, @FullName, @Age, @Email)";
        db.Execute(sqlQuery, user);
    }
}
```

4] Malum bir Userni o’zgartirish uchun (SQL da UPDATE buyruqi yordamida)
```csharp
public void Update(User user)
{
    using (IDbConnection db = new SqlConnection(_connectionString))
    {
        var sqlQuery = "UPDATE People SET FullName = @FullName, Age = @Age, Email = @Email WHERE Id = @Id";
        db.Execute(sqlQuery, user);
    }
}
```

5] Malum bir Userni o’chirish uchun (SQL da DELETE buyruqi yordamida)
```csharp
public void Delete(int id)
{
    using (IDbConnection db = new SqlConnection(_connectionString))
    {
        var sqlQuery = "DELETE FROM People WHERE Id = @id";
        db.Execute(sqlQuery, new { id });
    }
}
```

6] Ma’lum bir prodsedureni chaqirish uchun (SQL da EXEC buyruqi yordamida)
Eng avvalo string DateTime ni Full qilib beradigan bitta prodsedura yaratib olaman:
```sql
CREATE PROCEDURE ToFullDateTime @dateTime nvarchar(30)
AS
    DECLARE @date DATETIME;
    SET @date = CONVERT(DATETIME, @dateTime, 121)
    SELECT DATENAME(YEAR, @date) AS 'Year',        
    DATENAME(QUARTER, @date)     AS 'Quarter',     
    DATENAME(MONTH, @date)       AS 'MonthName',       
    DATENAME(DAYOFYEAR, @date)   AS 'DayOfYear',   
    DATENAME(DAY, @date)         AS 'Day',         
    DATENAME(WEEK, @date)        AS 'Week',        
    DATENAME(WEEKDAY, @date)     AS 'DayOfTheWeek',     
    DATENAME(HOUR, @date)        AS 'Hour',        
    DATENAME(MINUTE, @date)      AS 'Minute',      
    DATENAME(SECOND, @date)      AS 'Second',      
    DATENAME(MILLISECOND, @date) AS 'MilliSecond', 
    DATENAME(MICROSECOND, @date) AS 'MicroSecond', 
    DATENAME(NANOSECOND, @date)  AS 'NanoSecond',  
    DATENAME(ISO_WEEK, @date)    AS 'ISO_WEEK'
```
a] CommandType.Text bilan
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
    var sqlQuery = "EXEC ToFullDateTime @dateTime";
    FullTime result = db.QuerySingleOrDefault<FullTime>(sqlQuery, new { dateTime = DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss") });
    return $"Год - {result.Year}, Четверть - {result.Quarter}, Месяц название - {result.MonthName}, День года - {result.DayOfYear}, День - {result.Day}, День недели - {result.DayOfTheWeek}, Час - {result.Hour}, Минута - {result.Minute}, Секунд - {result.Second}"; 
}
```

b] CommandType.StoredProcedure bilan
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
    var prodsedure = "[ToFullDateTime]";
    var values = new { dateTime = DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss") };
    FullTime result = db.QuerySingleOrDefault<FullTime>(prodsedure, values,commandType: CommandType.StoredProcedure);
    return $"Год - {result.Year}, Четверть - {result.Quarter}, Месяц название - {result.MonthName}, День года - {result.DayOfYear}, День - {result.Day}, День недели - {result.DayOfTheWeek}, Час - {result.Hour}, Минута - {result.Minute}, Секунд - {result.Second}"; 
}
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------
Demak yana bitta takrorlash qilib olamiz, boshi esingizdan chiqib ketgan bo’lsa:

a) Sql bilan bog’lanish hosil qilish
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
	//qanaqadir kod
}
```

b) Sql kodlarini shunchaki yozish
```sql
SELECT * FROM People
```

c) Yangi model tuzish (biz qaytarayotgan malumot obyekt ko’rinishida chiroyli bo’lishi uchun)
```csharp
public class Class_Nomi
{
    //Proporties
}
```

d) Dapper bilan ko’nikma: Agar nimanidir bazada yangilamoqchi bo’lsangiz **Execute()**
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
    var sqlQuery = "INSERT INTO People VALUES(@Id, @FullName, @Age, @Email)";
    db.Execute(sqlQuery, user);
}
```

e) Dapper bilan ko’nikma: Agar nimanidir bazadan olmoqchi bo’lsangiz Query()
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
    return db.Query<User>("SELECT * FROM People").ToList();
}
```

f) Dapper bilan ko’nikma: Agar bazadan kelayotgan malumot bir qator bo’lsa **QuerySingleOrDefault()**
```csharp
using (IDbConnection db = new SqlConnection(_connectionString))
{
    return db.QuerySingleOrDefault<User>("SELECT * FROM People WHERE Id = @id", new { id }) ?? new User { };
}
```

g) Dapper bilan ko’nikma: Agar bazadan bitta prodsedureni ishlamoqchi bo’lsangiz  
**CommandType.StoredProcedure** yoki **CommandType.Text** bilan qilamiz.



Proyektning github dagi kodlarini [https://github.com/Ruzimurod2003/dapper-mvc](https://github.com/Ruzimurod2003/dapper-mvc) ga joylab qo’ydim.
Agar nimanidir o’rgangan bo’lsangiz bundan juda ham xursandman.

