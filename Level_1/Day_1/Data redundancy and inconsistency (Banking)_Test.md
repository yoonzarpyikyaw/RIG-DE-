# Banking Database: Data Redundancy & Inconsistency Solution
**Data redundancy and inconsistency (Banking)_Test.sql**သည် Banking System တစ်ခုတွင် Data များကို နေရာအနှံ့ခွဲသိမ်းခြင်း (File System Design) ကြောင့် ဖြစ်ပေါ်လာနိုင်သော Data Inconsistency ပြဿနာနှင့် ၎င်းကို DBMS ၏ Normalization နည်းပညာဖြင့် မည်သို့ဖြေရှင်းနိုင်ကြောင်း နှိုင်းယှဉ်ပြသထားသည့် Case Study ဖြစ်ပါသည်။

# ⚠️ The Problem: Bad Design (Separate Files)
ဤ Design တွင် Customer တစ်ယောက်၏ အချက်အလက် (အမည်၊ လိပ်စာ၊ ဖုန်း) ကို Table တိုင်းတွင် ထပ်ခါတလဲလဲ သိမ်းဆည်းထားသည်။

Tables involved:  
account_file: account_id(PK), customer_id, customer_name, address, phone, account_type, balance

loan_file: loan_id(PK), customer_id, customer_name, address, phone, loan_type, loan_amount, outstanding_amount

credit_card_file: card_id(PK), customer_id, customer_name, address, phone, card_number, card_type, credit_limit

Result: Customer က လိပ်စာပြောင်းလိုက်ပါက Table တစ်ခုတည်းတွင် update လုပ်မိလျှင် ကျန်ရှိသော Table များတွင် လိပ်စာအဟောင်းများ ကျန်နေခဲ့ကာ Data Inconsistency ဖြစ်ပေါ်စေသည်။

# ✅ The Solution: Good Design (Centralized/Normalized)
Data များကို Table တစ်ခုစီအလိုက် ခွဲခြားသိမ်းဆည်းပြီး Customer အချက်အလက်ကို တစ်နေရာတည်းတွင်သာ သိမ်းဆည်းသော Single Source of Truth ပုံစံဖြစ်သည်။

Tables involved:  
customers: customer_id(PK), customer_name, address, phone, email (Centralized Data)

accounts: account_id(PK), customer_id(FK), account_type, balance

loans: loan_id(PK), customer_id(FK), loan_type, loan_amount, outstanding_amount

credit_cards: card_id(PK), customer_id(FK), card_number, card_type, credit_limit

# 🛠️ SQL Features Demonstrated
Normalization: Data ထပ်နေမှုများကို ဖယ်ရှားရန် Table များ ခွဲထုတ်ခြင်း။

Foreign Key Constraints: ON UPDATE CASCADE ကိုအသုံးပြု၍ Customer ID ပြောင်းလဲပါက အခြား Table များတွင် အလိုအလျောက် ပြောင်းလဲစေခြင်း။

Union Queries: Bad design တွင် မကိုက်ညီသော Data များကို နှိုင်းယှဉ်ပြရန် အသုံးပြုခြင်း။

Relational Joins: Table အသီးသီးမှ Data များကို LEFT JOIN သုံး၍ ပြန်လည်ပေါင်းစည်းကြည့်ရှုခြင်း။

Database Views: ရှုပ်ထွေးသော Join များကို CREATE VIEW ဖြင့် လွယ်ကူစွာ ပြန်ကြည့်နိုင်ရန် ဖန်တီးခြင်း။

# ✨ Key Highlights
Inconsistency Demo: Script ထဲတွင် Customer တစ်ယောက်၏ လိပ်စာကို Table တစ်ခုတည်းမှာ ပြင်လိုက်သောအခါ အခြား Table များနှင့် Data ကွဲလွဲသွားပုံကို လက်တွေ့ပြသထားသည်။

Data Integrity: DBMS Solution တွင် လိပ်စာကို customers table တစ်ခုတည်း၌သာ ပြင်ရန်လိုအပ်ပြီး ကျန် Table များတွင် အလိုအလျောက် မှန်ကန်နေမည်ဖြစ်သည်။

Efficiency: စာရင်းဇယားများကို View အဖြစ် ဖန်တီးထားသဖြင့် Customer တစ်ယောက်၏ Banking Profile တစ်ခုလုံး (Account, Loan, Card) ကို တစ်ချက်တည်းဖြင့် ကြည့်ရှုနိုင်သည်။
Inventory Alert: လက်ကျန်ပစ္စည်း နည်းပါးလာပါက (ဥပမာ - ၂၀ အောက်) အလိုအလျောက် သိရှိနိုင်သည့် Query များ ပါဝင်သည်။

Transaction Security: အော်ဒါတင်စဉ် အမှားအယွင်း တစ်ခုခုရှိပါက Data မပျက်စီးစေရန် Transaction Control စနစ် ထည့်သွင်းထားသည်။

Access Control: Admin နှင့် Staff အကြား လုပ်ပိုင်ခွင့် ခွဲခြားသတ်မှတ်ပုံကို ပြသထားသည်။
