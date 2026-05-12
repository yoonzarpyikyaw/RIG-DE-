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

# 🛒 Retail Store: Difficulty in Accessing Data Solution
ဤ Project သည် လုပ်ငန်းတစ်ခု၏ Data များသည် သီးခြားစီဖြစ်နေသော File System ပုံစံမျိုးတွင် Reporting ထုတ်ရန် မည်မျှခက်ခဲကြောင်းနှင့် DBMS (Relational Database) ကို အသုံးပြု၍ Ad-hoc Reporting များကို စက္ကန့်ပိုင်းအတွင်း မည်သို့ထုတ်ယူနိုင်ကြောင်း ပြသထားပါသည်။

# ⚠️ The Problem: File-Based Style (Data Isolation)
အချက်အလက်များကို သီးခြား Table များ (သို့မဟုတ် ဖိုင်များ) အဖြစ် သိမ်းဆည်းထားပြီး ၎င်းတို့အကြား ချိတ်ဆက်မှု (Relationship) မရှိပါ။

Tables involved:  
stores_file: store_id (PK), store_name, region, city

products_file: product_id (PK), product_name, category, unit_price

sales_file: sale_id (PK), sale_date, store_id, product_id, quantity, total_amount

Scenario: Manager က "ပြီးခဲ့တဲ့ ၆ လအတွင်း Region အလိုက် အရောင်းဘယ်လောက်ရှိလဲ" ဟု မေးမြန်းပါက Sales ဖိုင်တွင် Region မပါဝင်သဖြင့် အခြားဖိုင်များနှင့် လက်ဖြင့် (သို့မဟုတ် ပရိုဂရမ်ဖြင့်) အပင်ပန်းခံ ချိတ်ဆက်ရယူရပါသည်။

# ✅ The Solution: Integrated DBMS Design
Table များအကြား Foreign Key များဖြင့် ချိတ်ဆက်ထားပြီး SQL Join များကို အသုံးပြုကာ လိုချင်သော Report ကို ချက်ချင်း ထုတ်ယူနိုင်ပါသည်။

Tables involved:  
stores: store_id (PK), store_name, region, city

products: product_id (PK), product_name, category, unit_price

sales: sale_id (PK), sale_date, store_id (FK), product_id (FK), quantity, total_amount

# 🛠️ SQL Features Demonstrated
Relational Joins: Table ၃ ခု (sales, stores, products) ကို ပေါင်းစည်းပြီး အချက်အလက် ရှာဖွေခြင်း။

Aggregation Functions: SUM() နှင့် COUNT() တို့ကို သုံး၍ စုစုပေါင်း အရောင်းပမာဏနှင့် အရောင်းအကြိမ်ရေကို တွက်ချက်ခြင်း။

Group By & Date Formatting: အရောင်းဒေတာများကို လအလိုက် (Monthly) နှင့် နယ်မြေအလိုက် (Regionally) စုစည်းပြသခြင်း။

Database Views: ခဏခဏ ထုတ်ကြည့်ရမည့် Report များအတွက် CREATE VIEW ကို အသုံးပြု၍ ပိုမိုမြန်ဆန်အောင် ပြုလုပ်ခြင်း။

# ✨ Key Highlights
Ad-hoc Reporting: မန်နေဂျာက မေးလာသမျှ မေးခွန်းများကို Custom code ရေးစရာမလိုဘဲ SQL query တစ်ကြောင်းတည်းဖြင့် ဖြေကြားနိုင်ခြင်း။

Monthly Trend Analysis: အချိန်ကာလအလိုက် အရောင်းအခြေအနေများကို DATE_FORMAT အသုံးပြု၍ Trend တစ်ခုအဖြစ် ကြည့်ရှုနိုင်ခြင်း။

Performance: Data များ များပြားလာသော်လည်း Indexing နှင့် Proper Joining များကြောင့် Report ထုတ်ရာတွင် မြန်ဆန်ခြင်း။

# 🚀 How to Use
MySQL သို့မဟုတ် MariaDB ကဲ့သို့သော SQL Editor တစ်ခုကို ဖွင့်ပါ။

ပေးထားသော .sql file ထဲမှ script များကို copy ကူး၍ run ပါ။

အောက်ပါ Query ဖြင့် Stock လက်ကျန်နှင့် ပစ္စည်းအမည်ကို တွဲဖက်ကြည့်ရှုနိုင်ပါသည်။

```sql
SELECT p.product_name, i.quantity
FROM products p
JOIN inventory_stock i ON p.product_id = i.product_id;
```
