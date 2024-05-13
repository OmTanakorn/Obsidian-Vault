### design_database

### data type
* กรองข้อมูลโดยค้นหาค่าใน JSONField 
``` sql
SELECT * FROM your_table WHERE your_json_field->>'key' = 'value';
```
 * กรองข้อมูลโดยใช้ JSONB containment operator (@>) 
```sql
SELECT * FROM your_table WHERE your_json_field @> '{"key": "value"}';
```

### normalization
