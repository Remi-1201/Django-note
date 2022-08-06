# 1. Djangoをインストールする

```
pip install Django==4.0  
```

- **Version 確認**

```
python -m django --version
```

### To activate virtualen

`virtualenv newenv -p python3`

`source newenv/bin/activate`

### PostgreSQLを使用するための準備 (WSL)

`pip install psycopg2==2.8.6`

- **Version 確認**

`pip list`

# プロジェクトを作成

`django-admin startproject プロジェクト名`
>django-admin startproject dproject

`cd dproject`

# アプリケーションを作成

Djangoでは、プロジェクトの中にアプリケーションを配置し、開発を行っていきます。

つまり、一つのプロジェクトの中で複数のアプリケーションを管理することが可能です。

``` 
Project
 ├ サービス利用者用アプリケーション
 ├ 顧客分析用アプリケーション
 └ 業務管理用アプリケーション
 ```
 
 - 現在のディレクトリを確認 `pwd`

`python manage.py startapp アプリケーション名`
>python manage.py startapp blog

### サーバーを起動する

`python manage.py runserver`

`http://localhost:8000/`にアクセス

# シークレットキーの扱い

- `dproject/dproject/local_settings.py`に, `setting.py`に記述されているシークレットキーの部分をコピーして貼り付けてください。

- `setting.py`からシークレットキーの部分を削除する

- ルートディレクトリ直下に`.gitignore`ファイルを作成し、`local_settings.py`を記述します。

```[setting.py]
try:
    from .local_settings import *
except ImportError:
    pass
```

