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
