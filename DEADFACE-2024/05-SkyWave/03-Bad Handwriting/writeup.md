# SkyWave 7: Bad Handwriting

![img.png](task%2Fimg.png) 

```mysql
select employee_number
from Technicians
where technician_id =
      (select technician_id from Tower_Maintenance where maintenance_date = "2024-08-26" and tower_id = 133);
```

![img.png](img.png) \
flag{T263739990}