# DataBase

We use SQL alchemy which is a very popular ORM that people use for different DataBase.

You can use different database without changing the python code.

We use SQLite for development and then when we're ready to deploy this application we'll switch over to a Postgres database for production

## Install SQL alchemy

```
pip install flask-sqlalchemy
```

## Get SQLite
Do this in the project root folder path, type ```python``` in terminal to enter the python shell, then execute the following command:
```python
from app import db
db.create_all()
```

## Add User and Post in Terminal
```python
from app import db
from app import User, Post
user_1 = User(username='kk', email='kk@kk.com', password='password')
db.session.add(user_1)
user_2 = User(username='zz', email='zz@zz.com', password='password')
db.session.add(user_2)
db.session.commit()
```

## Query User in Python Shell
```python
from app import User, Post
User.query.all()
# [User('kk', 'kk@kk.com', 'default.jpg'), User('zz', 'zz@zz.com', 'default.jpg')]
User.query.first()
# User('kk', 'kk@kk.com', 'default.jpg')
User.query.filter_by(username='kk').all()
# User('kk', 'kk@kk.com', 'default.jpg')
# User('kk', 'kk@kk.com', 'default.jpg')
User.query.filter_by(username='kk').first()
user = User.query.filter_by(username='kk').first()
user.id
# 1

# query by id
user = User.query.get(1)
```

## Create Post
```python
post_1 = Post(title='Blog 1', content='First Post Content', user_id=1)
post_1
# Post('Blog 1', 'None')
post_2 = Post(title='Blog 2', content='Second Post Content', user_id=1)
db.session.add(post_1)
db.session.add(post_2)
db.session.commit()
user.posts
# [Post('Blog 1', '2021-06-23 11:50:32.612430'), Post('Blog 2', '2021-06-23 11:50:32.616048')]


# query
post = Post.query.first()
post.author
# User('kk', 'kk@kk.com', 'default.jpg')
post.id
# 1

```

## Delete the database
```python
db.drop_all()
```