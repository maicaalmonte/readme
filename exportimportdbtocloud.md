1. migrate data from local to render
<br> *export data from local db:
```bash
pg_dump -U your_local_username -h localhost -F c -b -v -f backup_file.dump your_database_name
```
<br> *import data to render db:

```bash
pg_restore -U render_username -h render_host -d render_database_name -v backup_file.dump
```
2. update python app:
```python
from sqlalchemy import create_engine

DATABASE_URL = "postgresql://username:password@host:port/database"
engine = create_engine(DATABASE_URL)
```
