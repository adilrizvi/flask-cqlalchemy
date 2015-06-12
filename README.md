# Flask-CQLAlchemy

Flask-CQLAlchemy handles connections to Cassandra clusters
and gives a unified easier way to declare models and their
columns

## Installation
```
pip install flask-cqlalchemy
```

## Example
```
#example_app.py
import uuid
from flask import Flask
from flask.ext.cqlalchemy import CQLAlchemy

app = Flask(__name__)
app.config['CASSANDRA_DB'] = ['127.0.0.1']
app.config['CASSANDRA_KEYSPACE'] = "cqlengine"
db = CQLAlchemy(app)


class User(db.Model):
    uid = db.columns.UUID(primary_key=True, default=uuid.uuid4)
    username = db.columns.Text(required=False)
```

## Usage
Start a python shell

```
>>from example_app import db
>>from example_app import User
>>user1 = User(username='John Doe')
>>user1.save()
```
For a complete list of available method refer to the cqlengine [Model documentation](http://datastax.github.io/python-driver/api/cassandra/cqlengine/models.html)
