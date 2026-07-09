# DE_Level_1_Oracle_index_Test

ဤ Project သည် Oracle Database တွင် Indexing အမျိုးမျိုးကို အသုံးပြု၍ Database Performance မြှင့်တင်ခြင်းနှင့် Query Optimization ပြုလုပ်ခြင်းတို့ကို လက်တွေ့ စမ်းသပ်ထားသော Lab ဖြစ်သည်။ Telecom Subscriber နှင့် Call Detail Records Scenario ကို အခြေခံထားသည်။

## Project Structure
- **Tables**: `subscribers` (Customer data) နှင့် `call_records` (CDR logs)
- **Index Implementation**: Unique, B-tree, Composite, Function-based Index များ
- **Monitoring**: Index usage tracking နှင့် Maintenance (Rebuild)
- **Analysis**: Execution Plan analyzing via DBMS_XPLAN

## Critical Concepts Explored

### 1. Advanced Indexing Strategies
- **Composite Index**: City နှင့် Status ကဲ့သို့သော Column အများအပြားပါဝင်သည့် Filter များအတွက် အသုံးပြုသည်။
- **Function-based Index**: `UPPER(customer_name)` ကဲ့သို့သော Function များသုံးသည့်အခါ Index Scan ဖြစ်စေရန် အသုံးပြုသည်။
- **Foreign Key Indexing**: Table များ JOIN လုပ်သည့်အခါ Performance ကောင်းမွန်စေရန် Foreign Key column များတွင် Index ထည့်သွင်းသည်။

### 2. Performance Analysis Tools
- `EXPLAIN PLAN FOR` ကို အသုံးပြု၍ Query များ၏ Cost နှင့် Scan Type (Index Scan vs Full Table Scan) ကို ခွဲခြားစိတ်ဖြာခြင်း။
- `DBMS_XPLAN.DISPLAY` ဖြင့် အသေးစိတ် Execution path ကို လေ့လာခြင်း။

### 3. Maintenance & Optimization
- `MONITORING USAGE` ဖြင့် အသုံးမလိုသော Index များကို ရှာဖွေခြင်း။
- Index fragmentation ကို လျှော့ချရန် `REBUILD` command အသုံးပြုပုံ။

## SQL Configurations များအား အသုံးပြုနည်း
1. `CREATE TABLE` script များဖြင့် Schema တည်ဆောက်ပါ။
2. Sample data များ ထည့်သွင်းပါ။
3. `CREATE INDEX` scripts များဖြင့် Index များ တည်ဆောက်ပါ။
4. `EXPLAIN PLAN` ကို အသုံးပြု၍ Performance ကို စစ်ဆေးပါ။

## Design Conclusions
Index များသည် Database Read Performance ကို သိသိသာသာ ကောင်းမွန်စေသော်လည်း ၎င်းတို့သည် Storage space ယူခြင်းနှင့် DML operations များတွင် Overhead ဖြစ်စေခြင်းတို့ ရှိသောကြောင့် လိုအပ်သည့်နေရာတွင်သာ စနစ်တကျ အသုံးချသင့်သည်။
