# Django 認証機能

### PostgreSQLをインストール

`sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'`

`wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -`

`sudo apt update`

`sudo apt -y install postgresql-13 libpq-dev`

`psql --version`  

>psql (PostgreSQL) 14.4 (Ubuntu 14.4-1.pgdg20.04+1)

`pip3 install psycopg2==2.8.6 --user`

`pip list`

>インストール済パッケージの一覧

- **PostgreSQLに接続**

`sudo /etc/init.d/postgresql start`

`psql postgres`

- **作成されているロールを確認**

`\du`

- **ロールを切り替えることなくOSのユーザ名でデータベースに接続**

`create role "OS User name" with login createdb createrole superuser;`

- **Other users**

`CREATE ROLE sample_user WITH LOGIN PASSWORD 'password';` 

`ALTER USER sample_user WITH createdb createrole superuser Replication;`

`ALTER USER OsUserName WITH login createdb createrole superuser Replication;`

- **Change password**

`find / -name 'pg_hba.conf' 2>/dev/nul`

`vim /etc/postgresql/14/main/pg_hba.conf`

> to `local   all             postgres                           trust`

> to `local   all             all                                md5`

`sudo service postgresql restart`

`psql -U postgres`

`ALTER USER postgres with password 'password';`

`ALTER USER remi with password 'password';`

`ALTER USER sample_user with password 'password';`

`\q`

`sudo vim /etc/postgresql/14/main/pg_hba.conf`

> to `local   all             postgres                           md5`

`sudo service postgresql restart`

`psql -U postgres`

- **Exit**

`\q`

- **Restart**

`/etc/init.d/postgresql restart`

---

### DB構築

`git clone git@github.com:diveintocode-corp/loginApp.git`

`cd loginApp`

`createdb login_app`

`python3 manage.py migrate`

- 管理者ユーザも作成

`python3 manage.py createsuperuser`

`python manage.py runserver`

[http://localhost:8000/blog/](http://localhost:8000/blog/)

---

[ステップ４以降の詳細手順はテキストを参照](https://diver.diveintocode.jp/curriculums/3096)

---

### Errors

>`Error loading psycopg2 module: No module named 'psycopg2'`

`pip3 install psycopg2==2.8.6 --user`

`pip3 install psycopg2-binary --user`

>`Couldn't import Django. Are you sure it's installed and available on your PYTHONPATH environment variable?`

`virtualenv newenv -p python3`

`source newenv/bin/activate`

- to install django

`pip install django`

`django-admin --version`

- 「setuptools」を最新版に更新

`pip3 install -U setuptools --user`

- pip自体もアップデート

`pip3 install -U pip --user`

> Could not install packages due to an EnvironmentError: [Errno 13]

`pip3 install package_name --user`
