---
title: Advanced Programming with Python. Session 6
author: Pepe García
email: jgarciah@faculty.ie.edu
date: 2020-04-20
lang: en
---

Advanced Programming with Python. Session 6
===========================================


Plan for today
==============

-   SQL in Python
-   Using SQL in web applications

SQL refresher
=============

We use SQL to interact with databases.  The **SELECT** statement is used
to get data from the database.

    SELECT *
    FROM users u
    INNER JOIN invoices i
    WHERE i.user_id = u.id

SQL refresher
=============

The **INSERT** statement is used to add data to the database

    INSERT INTO users
    VALUES("pepe@pepegar.com", "pepegar")

SQL refresher
=============

The **UPDATE** statement is used to modify data that\'s already in the
DB

    UPDATE users u
    SET active=false
    WHERE u.id = 55;

SQL refresher
=============

We use the **DELETE ** statement when deleting data from the DB

    DELETE FROM users
    WHERE id = 55;

Using plain SQL in Python
=========================

It\'s possible to use SQL directly in Python by using the SQLAlchemy
library:

```python
from sqlalchemy import create_engine

engine = create_engine("sqlite:///example-using-sql/twitter.db")

conn = engine.connect()

results = conn.execute("SELECT * FROM users")
```

Practice
========

See example

**session-6/example-using-sql**

install
=======

flask-sqlalchemy
================

Let\'s install flask-sqlalchemy

Object Relational Mapping
=========================

ORM is a technique we\'ll use to relate database records to Python
objects.

    CREATE TABLE users (
      id INTEGER PRIMARY KEY,
      username TEXT NOT NULL,
      email TEXT NOT NULL
    );

    class User:
        def __init__(self, id, username, email):
            self.id = id
            self.username = username
            self.email = email

Declaring models
================

Models are classes that we\'ll use to interact with the DB.  We\'ll
declare them by extending **db.Model**

    class User(db.Model):
        pass

Adding fields to models
=======================

We\'ll need to make model fields have the same type as the DB columns:

    class User(db.Model):
        id = db.Column(db.Integer, primary_key=True)
        username = db.Column(db.String, nullable=False)
        email = db.Column(db.String, nullable=False)

Object Relational Mapping
=========================

Using SQLAlchemy ORM, we can use methods in the class instead of raw
SQL:

    SELECT * FROM users;

    SELECT * FROM users WHERE email = 'pepe@ie.edu';

    SELECT * FROM users WHERE email = 'pepe@ie.edu'
                        AND username = 'pepegar;'

    User.query.all()

    User.query.filter(User.email == "pepe@ie.edu")

    User.query.filter(User.email == "pepe@ie.edu") \
              .filter(User.username == "pepegar")

Practice
========

See example

**session-6/example-using-orm**

Homework
========

Modify your last homework so that it stores the data inside a database
instead of storing it in memory
