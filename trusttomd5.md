**1. authentication method from trust to md5**


``` plaintext
# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     md5

# IPv4 local connections:
host    all             all             127.0.0.1/32            md5

# IPv6 local connections:
host    all             all             ::1/128                 md5

# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     md5
host    replication     all             127.0.0.1/32            md5
host    replication     all             ::1/
```
**2. save and reload postgresql:**

```cmd
pg_ctl reload -D "C:\Program Files\PostgreSQL\17\data"
```
**3. ensure password is set for postgresql if ur using md5. to set a password:**
```sql
ALTER USER your_user_name WITH PASSWORD 'your_password';
```
**if successful....**
<br>**4. test postgresql connection**
```cdm
psql -U your_user_name -h 127.0.0.1 -d your_database_name
```
#
<br>or to scram-sha-256
```plaintext
# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     scram-sha-256

# IPv4 local connections:
host    all             all             127.0.0.1/32            scram-sha-256

# IPv6 local connections:
host    all             all             ::1/128                 scram-sha-256

# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     scram-sha-256
host    replication     all             127.0.0.1/32            scram-sha-256
host    replication     all             ::1/128                 scram-sha-256

# Allow connections from remote hosts in the subnet 192.168.1.0/24
host    all             all             192.168.1.0/24          scram-sha-256
```
<br> to trust if u don't want to add password

```plaintext
# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     trust

# IPv4 local connections:
host    all             all             127.0.0.1/32            trust

# IPv6 local connections:
host    all             all             ::1/128                 trust

# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     trust
host    replication     all             127.0.0.1/32            trust
host    replication     all             ::1/128                 trust

# Allow connections from remote hosts in the subnet 192.168.1.0/24
host    all             all             192.168.1.0/24          trust
```
