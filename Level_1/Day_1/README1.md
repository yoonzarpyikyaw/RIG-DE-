# E-Commerce Database Management System
**DDL_DML_DQL_DCL_DTL.sql** သည် E-commerce database တစ်ခုကို စနစ်တကျ တည်ဆောက်ပုံ၊ Data များ စီမံခန့်ခွဲပုံနှင့် Transaction များ ပြုလုပ်ပုံကို လေ့လာနိုင်ရန် ရည်ရွယ်ပါသည်။

# Database Structure (Day 1)
1. products  product_id (PK), product_name, sku, selling_price (Column)
2. inventory_stock - stock_id (PK), product_id (FK), quantity (Column)
3. sales_orders - sales_order_id (PK), order_number, customer_id, warehouse_id, order_date, status, total_amount, remarks, created_at, updated_at (Column)
# SQL Features Demonstrated
ဤ Project တွင် SQL ၏ အဓိက Language Group (၅) မျိုးလုံးကို လက်တွေ့ အသုံးချထားပါသည် -

DDL (Data Definition Language): CREATE DATABASE နှင့် CREATE TABLE များ အသုံးပြု၍ Database Structure ကို တည်ဆောက်ခြင်း။

DML (Data Manipulation Language): INSERT, UPDATE, DELETE တို့ဖြင့် Data များကို ပြုပြင်ပြောင်းလဲခြင်း။

DQL (Data Query Language): SELECT နှင့် JOIN များ အသုံးပြု၍ လက်ကျန်စာရင်းနှင့် အရောင်းစာရင်းများကို ရှာဖွေခြင်း။

DCL (Data Control Language): User အသစ်များ တည်ဆောက်ပြီး Access Permission (GRANT/REVOKE) များ သတ်မှတ်ခြင်း။

TCL (Transaction Control Language): ငွေပေးချေမှုနှင့် စတော့နှုတ်ခြင်း လုပ်ငန်းစဉ်များတွင် Data မမှားယွင်းစေရန် COMMIT နှင့် ROLLBACK တို့ဖြင့် ထိန်းချုပ်ခြင်း။

# ✨Key Highlights
Relational Integrity: Foreign Key များ အသုံးပြု၍ Table များအကြား ချိတ်ဆက်မှုကို ခိုင်မာအောင် တည်ဆောက်ထားသည်။
