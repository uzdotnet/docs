---
description: Temur G'aniyev
---

# Controller

**Controller** - Asp.Net Coredagi **Microsoft.AspNetCore.Mvc.Controller** sinfdan voris olgan yangi sinf hisoblanadi. Shuningdek foydalanuvchidan kelgan **request** (so'rov) ni qayta ishlaydi. Kerak bo'lsa **model** ni shaklantiradi va **view** (ko'rinish) ni chaqiradi.

**Controller** lar **Controllers** papkasida joylashadi.Agar siz yangi controller qo'shmoqchi bo'lsangi aynan shu papkaga qo'shishingiz kerak bo'ladi

Agar siz ushbu **https://localhost:5001/Home/Privacy** urlga tashrif buyursangiz: **Controllers** papkasida joylashgan **HomeController** nomli sinfning **Privacy** metodi ishga tushadi va bu metod sizga ota sinfdan voris olgan View() methodi orqali view(ko'rinishni) qaytaradi.

Namunaviy Controllerning ko'rinishi quydagicha:

```
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Logging;
using dotnetuz.Models;

namespace dotnetuz.Controllers
{
    public class HomeController : Controller
    {
        private readonly ILogger<HomeController> _logger;

        public HomeController(ILogger<HomeController> logger)
        {
            _logger = logger;
        }

        public IActionResult Index()
        {
            return View();
        }

        public IActionResult Privacy()
        {
            return View();
        }
    }
}
```
