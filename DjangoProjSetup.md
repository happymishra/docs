# Python Djnago Workshop - Project setup

1. Install Python

```shell
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt-get update
sudo apt-get install python3.6
```

2. Create a folder djnago-handson

```shell
mkdir djnago-handson
```

3. Install Pipenv
```python
pip install pipenv
```

4. Move to the directory where you have create django-workshop folder
```shell
cd /home/rupesh/djnago-handson
```

5.   Create pipenv virtual environment and initialise pipenv
```python
# Creates virtual environment using python 3.6
pipenv install --python 3.6
```

6. Activate pipenv virtual environment
```python
pipenv shell
```

7. List all the python packages installed in the virtual environment
```python
pip list
```

8. Install django in the virtual environment
```python
pipenv install django==2.2
```  

9. Check if django installed correctly
```python
pip list
```

 ----------------------------------------------------------------------------

1. Create a new Django project
```python
django-admin startproject worldcup
```

2. Check the project folder
```shell
ls -larth
```

3.  Start Django server
```python
python manage.py runserver OR python manage.py runserver 8080
```

4.  Create App in Django
```python
python manage.py startapp simpleapp
```

5.  Create another app 'players'
```python
python manage.py startapp players
```

6.  Make migrations
```python
python manage.py makemigrations
```

7.  Check migrations in SQL
```python
python manage.py sqlmigrate players 0001
```

8.  Migrate to database
```python
python manage.py migrate
```

------------------------------------------------------------------------

SQLLite browser
```shell
sudo apt-get update
sudo apt-get install sqlitebrowser
```

SQLLite installation
```shell
sudo apt-get install sqlite3 libsqlite3-dev
```

------------------------------------------------------------------------


Create Superuser for Admin
```shell
python manage.py createsuperuser
```

-----------------------------------------------------------------------

Extra commands;

Get pipenv python environment
```python
pipenv run which python
pipenv --venv
```

Uninstall package
```python
pipenv uninstall packageName
```;

Clean environment and removed the uninstalled packages from the environment
```
pipenv clean
```

Remove virtual environment created by pipenv
```python
pipenv -rm
```

Lock pipfile
```
pipenv Lock
```

Project Home folder
```python
pipenv --where
```

Deactivate Virtual Environment
```python
exit
```

Start Django Shell
```python
python manage.py shell
```

SQL query for migrations
```python
python manage.py sqlmigrate <appname> <migration number eg. 0001 or 0004>
```


Add migrations manually
```python
python manage.py makemigrations --name migration_name app_ame --empty
```