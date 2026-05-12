# 🏢 HR System: Database Transaction Management (ACID)

ဤ Project သည် HR Management System ၏ အခြေခံလုပ်ငန်းစဉ်များကို အသုံးပြု၍ Database တစ်ခု၏ အရေးကြီးဆုံး ဂုဏ်သတ္တိများဖြစ်သော  
**ACID Properties** (Atomicity, Consistency, Isolation, Durability) ကို လက်တွေ့စမ်းသပ်ရန် ရေးသားထားသော SQL Implementation ဖြစ်သည်။

## 📋 Database Structure

ဤ Script တွင် အဓိကအားဖြင့် ဝန်ထမ်းအချက်အလက်များကို သိမ်းဆည်းရန် Table (၁) ခုကို အသုံးပြုထားသည်။

### 🗄️ Database Name: `hr_demo`

### 📊 Table: `employees`

| Column Name | Data Type | Constraints | Description |
| --- | --- | --- | --- |
| `employee_id` | INT | PK, AUTO_INCREMENT | ဝန်ထမ်း၏ ID နံပါတ် |
| `employee_name` | VARCHAR(100) | NOT NULL | ဝန်ထမ်းအမည် |
| `department` | VARCHAR(100) | - | တာဝန်ကျဌာန |
| `salary` | DECIMAL(10,2) | NOT NULL | လစာပမာဏ |
| `leave_balance` | INT | NOT NULL, DEFAULT 0 | ခွင့်ရက်လက်ကျန် |

---

## 🛠️ ACID Test Cases (Implementation Details)

### 1️⃣ A - Atomicity (အလုံးစုံဖြစ်ခြင်း)

Transaction တစ်ခုအတွင်းရှိ SQL command များအားလုံး အောင်မြင်ရမည်။ တစ်ခုခုချို့ယွင်းပါက မူလအတိုင်းပြန်ဖြစ်ရမည်။

* **Scenario:** ဝန်ထမ်းအား လစာတိုးပေးခြင်းနှင့် ခွင့်ရက်နှုတ်ခြင်းကို တစ်ပြိုင်တည်းလုပ်ဆောင်သည်။
* **Failed Case:** အကယ်၍ ဒုတိယအဆင့်တွင် အမှားအယွင်းရှိပါက `ROLLBACK` လုပ်ခြင်းဖြင့် ပထမအဆင့်ကလုပ်ခဲ့သော လစာတိုးခြင်းကိုပါ ပယ်ဖျက်ပေးသည်။

### 2️⃣ C - Consistency (ကိုက်ညီမှုရှိခြင်း)

Database သည် သတ်မှတ်ထားသော စည်းမျဉ်း (Business Rules) များနှင့် အမြဲကိုက်ညီနေရမည်။

* **Scenario:** ခွင့်ရက်လက်ကျန် (Leave Balance) သည် သုညအောက် (Negative) မရောက်စေရန် Logic ဖြင့် ထိန်းချုပ်ထားသည်။
* **Consistency Rule:** `leave_balance >= requested_days` ဖြစ်မှသာ Transaction ကို အတည်ပြုသည်။

### 3️⃣ I - Isolation (သီးခြားဖြစ်ခြင်း)

Transaction တစ်ခု အလုပ်လုပ်နေစဉ် အခြား Transaction တစ်ခုက ဝင်ရောက်နှောင့်ယှက်ခြင်း သို့မဟုတ် မတည်မြဲသေးသော ဒေတာများကို ဖတ်ရှုခြင်း (Dirty Read) မရှိစေရ။

* **Test Method:** Session နှစ်ခု (MySQL Windows နှစ်ခု) ခွဲ၍ စမ်းသပ်သည်။ Session 1 က `COMMIT` မလုပ်သေးသရွေ့ Session 2 က ဒေတာအဟောင်းကိုသာ မြင်တွေ့ရမည် ဖြစ်သည်။

### 4️⃣ D - Durability (ခိုင်မြဲမှုရှိခြင်း)

Transaction တစ်ခု `COMMIT` ဖြစ်သွားပြီးပါက စနစ်ချို့ယွင်းမှု (System Crash) ဖြစ်စေကာမူ ထိုဒေတာသည် Database ထဲတွင် အမြဲတမ်း တည်ရှိနေရမည်။

* **Validation:** လစာပြင်ဆင်ပြီး `COMMIT` လုပ်ပြီးနောက် Connection ပိတ်၍ ပြန်ဖွင့်ကြည့်ခြင်းဖြင့် ဒေတာတည်မြဲမှုကို စစ်ဆေးသည်။

---

## 🚀 Key Business Features

Project တွင် အောက်ပါ Feature များကို ACID concept ဖြင့် ပေါင်းစပ်ထားသည်-

* **Employee Promotion:** ဝန်ထမ်းရာထူးတိုးရာတွင် လစာတိုးခြင်း၊ ဌာနပြောင်းခြင်းနှင့် ခွင့်ရက်တိုးပေးခြင်းတို့ကို Atomic ဖြစ်စွာ ဆောင်ရွက်ခြင်း။
* **Data Integrity:** မရှိသော ဝန်ထမ်း ID ကို Update လုပ်မိပါက စနစ်က လက်မခံဘဲ Rollback လုပ်ခြင်း။
* **Transaction Controls:** `START TRANSACTION`, `COMMIT`, `ROLLBACK` command များကို ထိရောက်စွာ အသုံးပြုထားခြင်း။

---

## 🛠️ How to Use

1. MySQL Workbench သို့မဟုတ် SQL Client တစ်ခုတွင် `hr_acid_examples.sql` ကို ဖွင့်ပါ။
2. အပိုင်းတစ်ခုချင်းစီအလိုက် (Section by Section) Execute လုပ်၍ Result များကို လေ့လာပါ။
3. **Isolation Test** အတွက် Session နှစ်ခုခွဲ၍ စမ်းသပ်ရန် မမေ့ပါနှင့်။

---

### 📊 Summary

* **Total Databases:** 1 (`hr_demo`)
* **Total Tables:** 1 (`employees`)
* **Key Operations:** Transactions, Data Consistency Checks, Rollback Scenarios.

---

ဒီ README format က ဖတ်ရတာ ရှင်းလင်းပြီး ဝန်ထမ်းအချက်အလက်တွေနဲ့ ACID properties တွေ ဘယ်လိုအလုပ်လုပ်တယ်ဆိုတာကို တစ်ချက်ကြည့်ရုံနဲ့ နားလည်စေမှာပါခင်ဗျာ။
