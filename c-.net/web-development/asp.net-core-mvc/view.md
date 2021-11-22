---
description: Temur G'aniyev
---

# View

**View** - MVC patternida malumotlarni foydalanuvchiga namoyish etuvchi va undan malumotlarni qabul qiluvchi qism hisoblanadi. View  HTML kod va Razor Markup dan tashkil topgan bo\'ladi. Razor Markup HTML kodlarni qayta ishlovchi kodlar bo\'lib C# dasturlash tilida yoziladi. ASP.NET Core MVC da View lar **.cshtml** kengaytmaga ega bo\'lgan fayllardan iborat bo\'ladi va Controller nomi bilan bir hil papkaga guruh qilib joylashtiriladi. O\'z navbatida bu guruhlangan papkalar esa **Views** papkasida bo\'ladi.

Namunaviy Viewning ko\'rinishi quydagicha:

```cshap
@model IEnumerable<BasicTutorials.Models.Student>

@{
    ViewBag.Title = "Index";
    Layout = "~/Views/Shared/_Layout.cshtml";
}

<h2>Index</h2>

<p>
    @Html.ActionLink("Create New", "Create")
</p>
<table class="table">
    <tr>
        <th>
            @Html.DisplayNameFor(model => model.StudentName)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.Age)
        </th>
        <th></th>
    </tr>

@foreach (var item in Model) {
    <tr>
        <td>
            @Html.DisplayFor(modelItem => item.StudentName)
        </td>
        <td>
            @Html.DisplayFor(modelItem => item.Age)
        </td>
        <td>
            @Html.ActionLink("Edit", "Edit", new { id=item.StudentId }) |
            @Html.ActionLink("Details", "Details", new { id=item.StudentId  }) |
            @Html.ActionLink("Delete", "Delete", new { id = item.StudentId })
        </td>
    </tr>
}

</table>

```
