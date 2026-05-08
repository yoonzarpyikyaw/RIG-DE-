# Query Descriptions

### 1. Show All Tables
```sql
SELECT table_name
FROM information_schema.tables
WHERE table_schema = 'schoolmsdb';

Purpose:


Display all tables inside the schoolmsdb database.



# 2. Show Foreign Key Relationships
SELECT    kcu.CONSTRAINT_NAME AS foreign_key_name,    kcu.TABLE_NAME AS child_table,    kcu.COLUMN_NAME AS child_column,    kcu.REFERENCED_TABLE_NAME AS parent_table,    kcu.REFERENCED_COLUMN_NAME AS parent_columnFROM information_schema.KEY_COLUMN_USAGE kcuWHERE kcu.REFERENCED_TABLE_NAME IS NOT NULL  AND kcu.TABLE_SCHEMA = 'schoolmsdb'ORDER BY child_table, foreign_key_name;
Purpose:


Display all foreign key relationships in the schoolmsdb database.


Show:


Foreign key name


Child table & column


Parent table & column





