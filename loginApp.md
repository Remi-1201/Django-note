# Django 認証機能

## PostgreSQLをインストール

`sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'`

`wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -`

`sudo apt update`

`sudo apt -y install postgresql-13 libpq-dev`

`psql --version`  
>psql (PostgreSQL) 14.4 (Ubuntu 14.4-1.pgdg20.04+1)

#### PostgreSQLに接続

`sudo /etc/init.d/postgresql start`

`psql postgres`

#### 作成されているロールを確認

`\du`

#### ロールを切り替えることなくOSのユーザ名でデータベースに接続

`create role "OS User name" with login createdb createrole superuser;`

##### For other users 

`CREATE ROLE sample_user WITH LOGIN PASSWORD 'pass';`

`ALTER USER sample_user WITH createdb createrole superuser Replication;`

`ALTER USER OsUserName WITH login createdb createrole superuser Replication;`

##### Change password

`find / -name 'pg_hba.conf' 2>/dev/nul`

`vim /etc/postgresql/14/main/pg_hba.conf`

> to `local   all             postgres                           trust`
> 
> to `local   all             all                                md5`


`sudo service postgresql restart`

`psql -U postgres`

`ALTER USER postgres with password 'pass';`

`ALTER USER my_user with password 'pass';`

`\q`

`sudo vim /etc/postgresql/14/main/pg_hba.conf`

> to `local   all             postgres                           md5`

`sudo service postgresql restart`

`psql -U postgres`

- Exit

`\q`

- Restart

`/etc/init.d/postgresql restart`

---

### DB構築

`git clone git@github.com:diveintocode-corp/loginApp.git`

`cd loginApp`

`createdb login_app`

`python3 manage.py migrate`

---

## Errors

> Error loading psycopg2 module: No module named 'psycopg2' 

`sudo apt install python3-psycopg2`

`pip install psycopg2-binary`

> Couldn't import Django. Are you sure it's installed and available on your PYTHONPATH environment variable?

`virtualenv newenv`

`source newenv/bin/activate`

`pip install django`

`django-admin --version`
