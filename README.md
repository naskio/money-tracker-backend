# money-tracker-backend
Training Camp by ETIC at ESI (Algiers), backend, Django, 2020
# step-by-step guide
- install python 3.6+
- install virtualenv
- create a folder for the project
- create a virtual env
    ```
    virtualenv -p python3 .env
  ```
  or
    ```
    virtualenv .env
    ```
  then
    ```
  source .env/bin/activate
  ```
- install django
    ```
    pip install django
    ```
- freeze requirements
    ```
    pip freeze > requirements.txt
    ```
- install requirements
    ```
    pip install -r requirements.txt
    ```
- create django project
  ```
  django-admin startproject PROJECT_NAME
  ```
- create a django app
  ```
  django-admin startapp APP_NAME
  ```
- prepare the .env:
    - at the end of the file (.env/bin/activate) add:
    ```
    export DEBUG="True"
    ```
    - at the end of the deactivate function add:
    ```
    unset DEBUG
    ```

- config.py
    - add apps
    - debug=false on prod
    - allowed host
    - dj-database-url (for database)
    ```
    pip install dj-database-url
    ```
    
- adding models, fields, enums

- make migrations
```
python manage.py makemigrations
```
- migrate
```
python manage.py migrate
```

- adding auth
```
pip install djangorestframework-simplejwt
```
    
- adding filtering
```
pip install django-filter
```

- deploy to heroku
    - create app in heroku
    - add Procfile to the project
    - add those packages in requirements.txt
        gunicorn
        psycopg2-binary
    - run
    ```
    heroku git:remote -a tc-money-tracker
    ```
    - disable collectstatic
    ```
    heroku config:set DEBUG_COLLECTSTATIC=1
    ```
    or add staticfiles and static folders to git
    - run
    ```
    git push heroku master
    ```
    - run the migration
    ```
    heroku run python manage.py migrate
    ```
    - create the admin
    ```
    heroku run python manage.py createsuperuser
    ```

