## Python Flask PostgreSQL Web App

Below are the steps to set up this project

1. Install Python 3.7.3
2. ```pip3 install pipenv``` this will install pipenv 
3. ```pipenv shell``` to create virtual env with python 3.7.3
4. ```pipenv install -r ./requirements.txt``` to install all packages from requirements.txt
5. Execute command to start project : ```flask run```

> Steps to create a postgres database and deply a Python app to Heroku

### Install guinicorn locally
```pipenv install gunicorn```

### Login via CLI
```heroku login```

### Create app
```heroku create python-postgres-lexus```

### Create database
```heroku addons:create heroku-postgresql:hobby-dev --app python-postgres-lexus```

### Get URI
```heroku config --app python-postgres-lexus```

### Create Procfile
```
touch Procfile

# Add this
web: gunicorn app:app
```

### Create requirements.txt
```pip freeze > requirements.txt```

### Create runtime.txt
```
touch runtime.txt

# Add this
python-3.7.2
```

### Deploy with Git
```
git init
git add . && git commit -m 'Deploy'
heroku git:remote -a appname
git push heroku master
```

### Add table to remote database
```
heroku run python
>>> from app import db
>>> db.create_all()
>>>exit()
```
### Visit app
```heroku open```

### Run PostgreSQL in console
```heroku pg:psql --app python-postgres-lexus```
