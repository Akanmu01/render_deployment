# Django on Render
This is a simple project developed using Django framework and it contains the settings required for successfull deployment of Django projects on Render.
## Setup

Below are the steps to follow to setup this project locally on your machine;

* Clone the project locally on your machine using **git clone**
* Create and activate a new virtual enviroment.
* To install dependencies run
```
pip install -r requirements.txt
```
* Go to the projects setting.py file and remove the comments in the database section.

* In your terminal execute the following commands to makemigrations and migrate to database

```
python manage.py makemigrations
python manage.py migrate
```

## Using PostgreSQL Database

Comment the database section out completely and paste the follwing lines of code beneath it.

```
DATABASES = {  
    'default': {  
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'database_name',  
        'USER': 'database_user',  
        'PASSWORD': 'Database_password',  
        'HOST': 'database_host.oregon-postgres.render.com',  
        'PORT': '5432',
    }  
}
```
# Build command

```
./build.sh
```

# Start command

```
gunicorn project_name.wsgi:application
```

## Using Default Database

Comment the database section out completely and paste the follwing lines of code beneath it.
```

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```


## Using No Database

Comment the database section out completely and paste the follwing lines of code beneath it.
```

DATABASES = {}
```

# To setup database on render click new then select postgrel db

```
Fill in your name and the name of the database

Don't forget to import dj-database-url at the beginning of the file
import dj_database_url
# Database
# https://docs.djangoproject.com/en/3.0/ref/settings/#database

DATABASES = {
    'default': dj_database_url.config(
        default=database external connection string that start with postgre',
        conn_max_age=600
    )
}
```


# Access your database data here

```
# https://pgweb-demo.fly.dev
click on scheme and paste your external connection string there then login
```



# After connecting to render database
```
Run the following command locally
python manage.py makemigration
python manage.py migrate
python manage.py createsuperuser


# Note: You have to do this locally, you don't have access to render terminal since you're using free account there

```
