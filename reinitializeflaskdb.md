**1. remove database file (optional). drop all tables in public schema and re-create the schema**
```sql
DROP SCHEMA public CASCADE;
CREATE SCHEMA public;
```
**2. initialize migrations**
```bash
flask db init
```
**3. create migration script**
```bash
flask db migrate -m "Initial migration"
```
**4. apply the migration**
```bash
flask db upgrade
```