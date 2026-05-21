# 🚀 Leveling Up My Database Skills: Diving into MSSQL Stored Procedures (CRUD to Session-Based Temps)

Database Management မှာ စွမ်းဆောင်ရည် အကောင်းဆုံးနဲ့ အလုပ်လုပ်နိုင်ဖို့အတွက် SQL Queries တွေကို စနစ်တကျ စုစည်းသိမ်းဆည်းပေးနိုင်တဲ့ **MSSQL Stored Procedures** အကြောင်းကို လက်တွေ့ Lab တစ်ခု လုပ်ရင်း ထဲထဲဝင်ဝင် ပြန်လည်လေ့လာဖြစ်ခဲ့တဲ့ မှတ်တမ်းဖြစ်ပါတယ်။

ပုံမှန်ရေးနေကျ CRUD Operations တွေကို Application code ထဲမှာပဲ တိုက်ရိုက်ရေးမယ့်အစား တွက်ချက်မှုဆိုင်ရာ Logic တွေကို Stored Procedure တွေအဖြစ် ခွဲထုတ်လိုက်ခြင်းက Database ရဲ့ Performance ကို သိသိသာသာ မြန်ဆန်စေတဲ့အပြင် Security ပိုင်းမှာပါ ပိုမိုခိုင်မာစေပါတယ်။

---

## 💡 ဒီ Lab ကနေ ပြန်လည်ဆန်းသစ်ခွင့်ရခဲ့တဲ့ Core Concepts များ

### 1. Structured CRUD Logic
* `@Parameters` တွေကို အသုံးပြုပြီး Data တွေကို စနစ်တကျ စစ်ထုတ်ထည့်သွင်းပေးခြင်း။
* `InsertEmployee`, `DeleteEmployee` နဲ့ `UpdateEmployeeAddress` စတဲ့ လုပ်ငန်းစဉ်များကို စနစ်တကျ တည်ဆောက်ခြင်း။

### 2. Dynamic OUTPUT Parameters
* Database ထဲက အချက်အလက်တွေကို ရိုးရိုး `SELECT` ပြရုံတင်မကဘဲ Variable တွေထဲ တန်ဖိုးပြန်ထုတ်ပေးနိုင်တဲ့ `@p_total_employees INT OUTPUT` ရဲ့ စွမ်းဆောင်ရည်ကို အသုံးချခြင်း။

### 3. Internal Logic Processing
* ဝန်ထမ်းတစ်ယောက်ရဲ့ လစာကို Dynamic တိုးပေးပြီး တိုးသွားတဲ့လစာအသစ်ကိုပါ Variable ထဲ ပြန်သိမ်းပေးတဲ့ `IncreaseSalary` logic မျိုးကို ရေးသားစမ်းသပ်ခြင်း။

### 4. Maintenance & Inspection
* လက်ရှိတည်ဆောက်ထားတဲ့ Procedure တွေကို `ALTER PROCEDURE` နဲ့ ပြင်ဆင်ပုံ။
* `sys.procedures` စနစ်ဇယား (System Catalog View) ကနေ ရှာဖွေပုံ။
* `sp_helptext` ကို သုံးပြီး ရေးထားတဲ့ ဖွဲ့စည်းပုံကို ပြန်လည်စစ်ဆေးပုံ။

### 5. Session Isolation (Temporary SPs)
* **Local Temporary Procedure (`#TempEmployeeReport`):** Active ဖြစ်နေတဲ့ လက်ရှိ Connection Session တစ်ခုတည်းအတွက်သာ အလုပ်လုပ်ခြင်း။
* **Global Temporary Procedure (`##GlobalEmployeeReport`):** Session အားလုံးက လှမ်းသုံးလို့ရမယ့် ပုံစံမျိုး။
* *အထက်ပါ နှစ်ခုကြားက သီးခြားခွဲထုတ်ထားတဲ့ (Isolation) ခြားနားချက်များကို လက်တွေ့လေ့လာခြင်း။*

---

> 🎯 **Takeaway:** ဒီလို လက်တွေ့လေ့လာမှုတွေကတစ်ဆင့် ပိုမိုကောင်းမွန်ပြီး စွမ်းဆောင်ရည်မြင့်မားတဲ့ **Database Architecture** တွေကို တည်ဆောက်နိုင်ဖို့ အများကြီး အထောက်အကူပြုစေပါတယ်။
> # screenshot တွေကြည့်ချင်ရင်တော့ 
