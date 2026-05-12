ယခု SQL script သည် HR Management System တစ်ခုကို အခြေခံပြီး Database တစ်ခုရဲ့ အသက်ဝိညာဉ်ဖြစ်တဲ့ ACID Properties အကြောင်းကို လက်တွေ့စမ်းသပ်နိုင်ဖို့ ရေးသားထားတာ ဖြစ်ပါတယ်။  

HR Database System: ACID Properties Demonstration
ဤ Project သည် MySQL ကို အသုံးပြု၍ HR Management System တစ်ခုတွင် ACID (Atomicity, Consistency, Isolation, Durability) properties များ မည်သို့ အလုပ်လုပ်သည်ကို လက်တွေ့ပြသရန် ရေးသားထားသော Script ဖြစ်သည်။

📊 Database Schema Overview
Project တွင် အဓိက Table (၄) ခု ပါဝင်သည်-

Departments: ဌာနဆိုင်ရာ အချက်အလက်များ။

Employees: ဝန်ထမ်းအချက်အလက်၊ လစာနှင့် ခွင့်ရက်လက်ကျန်များ။

Payroll Transactions: လစာပေးချေမှုမှတ်တမ်းများ။

Leave Requests: ခွင့်တိုင်ကြားမှုနှင့် ခွင့်ပြုချက်မှတ်တမ်းများ။

🛠 ACID Implementation Details
1. Atomicity (အကုန်လုံးဖြစ်ရမည် သို့မဟုတ် လုံးဝမဖြစ်ရ)
Script ထဲတွင် ခွင့်တိုင်ကြားခြင်း (Leave Request) လုပ်ငန်းစဉ်ဖြင့် ပြသထားသည်။

အောင်မြင်မှု (Success scenario): leave_requests ထဲသို့ ဒေတာဝင်ခြင်းနှင့် employees ထဲမှ ခွင့်ရက်နှုတ်ခြင်းကို START TRANSACTION နှင့် COMMIT ကြားတွင် ထားရှိသည်။

ကျရှုံးမှု (Failure scenario): အကယ်၍ ဝန်ထမ်း ID မှားယွင်းနေပါက (FK Constraint Error)၊ ခွင့်ရက်နှုတ်ထားသော အပိုင်းကိုပါ ROLLBACK လုပ်ပြီး မူလအခြေအနေသို့ ပြန်သွားစေသည်။

2. Consistency (ဒေတာများ မှန်ကန်မှုရှိနေခြင်း)
Database Constraints များကို အသုံးပြု၍ စည်းမျဉ်းများကို ထိန်းသိမ်းထားသည်-

Check Constraints: လစာ (Salary) နှင့် ခွင့်ရက်လက်ကျန် (Leave Balance) များသည် Negative (သုညအောက်) မဖြစ်စေရန် တားဆီးထားသည်။

Foreign Keys: မရှိသော ဌာန (Department) သို့မဟုတ် ဝန်ထမ်း (Employee) ကို ထည့်သွင်းခြင်းမှ ကာကွယ်ပေးသည်။

3. Isolation (သီးခြားစီ ဖြစ်နေခြင်း)
တစ်ချိန်တည်းတွင် Transaction နှစ်ခု အလုပ်လုပ်ပါက တစ်ခုနှင့်တစ်ခု အနှောင့်အယှက်မဖြစ်စေရန် စမ်းသပ်ထားသည်။

Read Committed: Session 1 မှ လစာတိုးလိုက်သော်လည်း COMMIT မလုပ်သေးသရွေ့ Session 2 မှ ဝန်ထမ်း၏ လစာအဟောင်းကိုသာ မြင်တွေ့ရမည် ဖြစ်သည်။ ၎င်းသည် Uncommitted data (Dirty Read) များကို တားဆီးပေးသည်။

4. Durability (ခိုင်မြဲမှုရှိခြင်း)
လစာပေးချေမှု (Payroll Processing) ကို COMMIT လုပ်ပြီးသည်နှင့် Database တစ်ခုလုံး Restart ကျသွားစေကာမူ သို့မဟုတ် Connection ပြတ်တောက်သွားစေကာမူ ထိုဒေတာသည် ပျောက်ပျက်မသွားဘဲ အမြဲတမ်း သိမ်းဆည်းပြီးသား ဖြစ်နေခြင်းကို ဆိုလိုသည်။

🚀 How to Run the Test
MySQL Workbench သို့မဟုတ် မိမိနှစ်သက်ရာ SQL Client တွင် Script ကို Run ပါ။

Atomicity & Consistency စမ်းသပ်ရန် Script ပါ ROLLBACK နေရာများကို တစ်ဆင့်ချင်း Execute လုပ်ကြည့်ပါ။

Isolation ကို စမ်းသပ်ရန်အတွက် Windows နှစ်ခု (Sessions နှစ်ခု) ဖွင့်၍ Script ပါ ညွှန်ကြားချက်အတိုင်း စမ်းသပ်ပါ။

💡 Key Business Logic Tested
Employee Promotion: ဌာနပြောင်းခြင်း၊ ရာထူးတိုးခြင်းနှင့် လစာတိုးခြင်းတို့ကို Transaction တစ်ခုတည်းဖြင့် ချိတ်ဆက်လုပ်ဆောင်ခြင်း။

Leave Approval: ခွင့်ရက်အတည်ပြုခြင်းနှင့် လက်ကျန်ခွင့်ရက် တွက်ချက်ခြင်း။

Constraint Safeguards: မမှန်ကန်သော ဒေတာများ (ဥပမာ- လစာ အနှုတ်ပြခြင်း) ကို လက်မခံစေရန် စစ်ဆေးခြင်း။
