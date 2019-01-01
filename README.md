<h1>Django SQLite to MySQL Migrations</h1>
In this guide we will discuss how to migrate data from sqlite to mysql in the most easy and simple way.The following are the steps to migrate data from sqlite to mysql.
<h1>Steps</h2>

  1. Connect your sqlite3 database
  2. Once thats done then just type this command 
  ```javascript
python manage.py dumpdata --exclude=contenttypes --exclude=auth.Permission --format=xml > output.xml
```
  3. Now once the data has been dumped then connect to your MySql database and apply these commands
  ```javascript
  python manage.py makemigrations
  ```
  &nbsp; &nbsp; &nbsp;then
   ```javascript
  python manage.py migrate --run-syncdb
  ```
  4. Now finally just run this command
  ```javascript
  python manage.py loaddata output.xml
  ```
  <h2>MySql Connection Code</h2>
  
   ```javascript
  DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'database name',
        'USER': 'your username',
        'PASSWORD': 'your password',
        'HOST': 'localhost',
        'PORT': '3306',
    },    
}
```
  
  <h2>Errors</h2>
  If any error about the formate of the xml file comes then just change the utf-8 to utf-16 then apply step number 4 again.
  Example
  
  From
  
  ```javascript
  <?xml version="1.0" encoding="utf-8"?>
  ```
  To
   ```javascript
  <?xml version="1.0" encoding="utf-16"?>
  ```
  
