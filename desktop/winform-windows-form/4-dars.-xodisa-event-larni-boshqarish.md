---
description: Jasurbek Xasanboyev
---

# 4-dars. Xodisa\(Event\)larni boshqarish

Formaga komponentlarni tashlab  oldik endi ularga event berishimiz kerak. Ya’ni buttonni bosgan paytingizda u qandaydir amalni bajarish orqali qaysidir vazifani bajaradi. Misol keltiradigan bo\`lsak kalkulyatorga sonni kiritib ‘+’ tugmasini bo\`lsak dastur tushunadiki demak kiritiladigan ikkinchi son birinchi songa qo\`shiladi va ‘=’ tugmasini bosgan paytimizda ikki sonni yig\`indisini bizga chop etib beradi. Menimcha sizda **Event**  haqida tushuncha paydo bo\`ldi deb o\`ylayman.

Komponentga hodisa qo\`shish uchun qo\`ydagi ketma-krtlik bajariladi:

1. Hodisa qo\`shilishi kerak bo\`lgan komponent tanlanadi avvalgi darsda yaratgan dasturimiz bo\`yicha qaraydigan bo\`lsak bizda hodisa Buttonda edi.
2. **Properties** menyusidan hodisa belgisiga bosiladi va bizga hodisalar ro\`yhati ko\`rinadi.
3. Ro\`yhatdan _Click_ hodisasini topib unga sichqonchaning chap tugmasini ikki marta bosamiz \(double-click\).

Bizga quyidagicha kod forma ochiladi:

```csharp
private void btnAdd_Click(object sender, EventArgs e)
{
}
```

Bizni dasturimizda joylashgan txtName nomli textbox bor. Dastur vazifasi esa textbox ga kiritilgan ismni lstNames nomdagi listboxga qo'shish kerak bo'ladi. Bunda quyidagicha shartlar bor: ism bo'sh bo'lmasligi kerak va kirtilayotgan ism avval kiritilmagan bo\`lishi kerak.

```csharp
private void btnAdd_Click(object sender, EventArgs e)
{
    if (!string.IsNullOrWhiteSpace(txtName.Text) && !lstNames.Items.Contains(txtName.Text))
        lstNames.Items.Add(txtName.Text);
}
```

