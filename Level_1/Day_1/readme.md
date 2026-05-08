# E-Commerce Database Management System (SQL)
ဤ Project သည် E-commerce လုပ်ငန်းတစ်ခု၏ Product Management, Inventory Tracking, နှင့် Sales Ordering လုပ်ငန်းစဉ်များကို SQL Query များအသုံးပြု၍ စနစ်တကျ စီမံခန့်ခွဲပုံကို ပြသထားသော Use Case တစ်ခု ဖြစ်ပါသည်။

📊 Database Schema Summary
Database ထဲတွင် Table စုစုပေါင်း (၃) ခုပါဝင်ပြီး တစ်ခုနှင့်တစ်ခု Relation ချိတ်ဆက်ထားပါသည်။

1. Products Table
ကုန်ပစ္စည်းအချက်အလက်များကို သိမ်းဆည်းပါသည်။

product_id: Primary Key

product_name: ကုန်ပစ္စည်းအမည်

sku: Unique Stock Keeping Unit

selling_price: ရောင်းဈေး

2. Inventory Stock Table
လက်ကျန်ပစ္စည်းအရေအတွက်ကို ထိန်းချုပ်ပါသည်။

stock_id: Primary Key

product_id: Foreign Key (Link to Products)

quantity: လက်ကျန်အရေအတွက်

3. Sales Orders Table
အော်ဒါစာရင်းများကို မှတ်တမ်းတင်ပါသည်။

sales_order_id: Primary Key

order_number: Unique Order ID

status: Order အခြေအနေ (Pending, Shipped, etc.)

total_amount: စုစုပေါင်းကျသင့်ငွေ

🛠️ SQL Features Demonstrated
ဤ Project တွင် SQL ၏ အဓိက Language Group (၅) မျိုးလုံးကို အသုံးပြုထားပါသည်။

DDL (Data Definition Language): Table များ တည်ဆောက်ခြင်း (CREATE).

DML (Data Manipulation Language): အချက်အလက်များ ထည့်ခြင်း၊ ပြင်ခြင်း၊ ဖျက်ခြင်း (INSERT, UPDATE, DELETE).

DQL (Data Query Language): Data ပြန်ထုတ်ကြည့်ခြင်း နှင့် Table များ ချိတ်ဆက်ကြည့်ခြင်း (SELECT, JOIN).

DCL (Data Control Language): User Access များကို ထိန်းချုပ်ခြင်း (GRANT, REVOKE).

TCL (Transaction Control Language): လုပ်ငန်းစဉ်တစ်ခုလုံး အောင်မြင်မှသာ အတည်ပြုခြင်း (COMMIT, ROLLBACK).

🚀 How to Use
MySQL သို့မဟုတ် MariaDB ကဲ့သို့သော SQL Editor တစ်ခုကို ဖွင့်ပါ။

ပေးထားသော .sql file ထဲမှ script များကို copy ကူး၍ run ပါ။

အောက်ပါ Query ဖြင့် Stock လက်ကျန်နှင့် ပစ္စည်းအမည်ကို တွဲဖက်ကြည့်ရှုနိုင်ပါသည်။

SQL
SELECT p.product_name, i.quantity
FROM products p
JOIN inventory_stock i ON p.product_id = i.product_id;
📝 Key Highlights
Low Stock Alert: လက်ကျန် ၂၀ အောက်နည်းသော ပစ္စည်းများကို အလိုအလျောက် ရှာဖွေနိုင်ခြင်း။

Data Integrity: Foreign Key များအသုံးပြု၍ Data များ မှားယွင်းမှုမရှိအောင် ချိတ်ဆက်ထားခြင်း။

Security: Staff User များအတွက် သီးသန့် Permission များ သတ်မှတ်ထားခြင်း။

Author: [Your Name]
Date: May 2026
