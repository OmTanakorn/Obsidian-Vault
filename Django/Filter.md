
```sql
results = MyModel.objects.filter(json_field__contains={'key': 'value'})
```