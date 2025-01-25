**other navigations:**
<br>.locate pg_hba.conf
```cmd
notepad "C:\Program Files\PostgreSQL\<version>\data\pg_hba.conf"
```
.locate config file postgresql**
```bash
 notepad "C:\Program Files\PostgreSQL\17\data\postgresql.conf"
```
.check current path in powershell
```bash
    echo $env:PATH
````
.check if postgresql is running:
```cmd
netstat -ano | findstr :5433
```
.connect directly usinf psql command-line tool:
```bash
psql -h localhost -p 5433 -U your_username -d your_database
```
.check postgresql status:
```bash
net start | findstr postgres
```
.test postgresql connection:
```bash
psql -h localhost -p 5433 -U your_username -d your_database
```