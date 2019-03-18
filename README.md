### butterdb
---
https://github.com/terrible-ideas/butterdb

```py
import butterdb
import json

with open('SomeGoogleProject-xxxxxxx.json') as credentials_file:
  json_key = json.load(credentials_file)
  
client_email = json.key['client_email']
private_key = str(json_key['private_key']).encode('utf-8')

database = butterdb.Database(name="MyDatabaseSheet", client_email=client_email, private_key=private_key)

@butterdb.register(database)
class User(butterdb.Model):
  def __init__(self, name, password):
    self.name = self.field(name)
    self.password = self.field(password)
    
users = User.get_instances()

marianne = users[1]

print(marianne.password)

marianne.password = "hunter2"
marianne.commit()


bob = User("bob", "BestPassword!")
bob.commit()
```

```py
import butterdb

database = butterdb.Database("MyDatabaseSheet", "foo@google.com", "password")

@butterdb.register(database)
class User(butterdb.Model):
  def __init__(self, name, password):
    self.name = self.field(name)
    self.password = self.field(password)
    
barray = User("Barry", "hunter2")
barray.name = "Steve"
barray.commit()

users = User.get_instances()
```

```
```


