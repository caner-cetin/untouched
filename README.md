# Untouched

https://pypi.org/project/untouched/

https://github.com/DAMACANER/untouched


Carbon copy of https://github.com/lann/builder for making a Python NoSQL query builder.

Installing:

```python
poetry add untouched
```

Example:

```python
from  untouched.builder import Builder, get_struct, T
from untouched.registry import Registry
from typing import Optional

NameDBField: str = "name"
AgeDBField: str = "age"
class UserQueryBuilder(Builder):
        """
        The UserBuilder class inherits from Builder and provides specific methods to set the 'name' and 'age' attributes.
        """

        def __init__(self):
            super().__init__()

        def name(self, val: str) -> 'UserQueryBuilder':
            """
            Creates a new UserBuilder with the 'name' attribute set to the provided value.
            """
            return self.set_value(NameDBField, val)

        def age(self, val: int) -> 'UserQueryBuilder':
            """
            Creates a new UserBuilder with the 'age' attribute set to the provided value.
            """
            return self.set_value(AgeDBField, val)


class User:
        """
        The User class represents the structure that the UserBuilder will build.
        """

        def __init__(self, name: Optional[str] = None, age: Optional[int] = None):
            self.name = name
            self.age = age

registry = Registry()
registry.register(UserQueryBuilder(), User())
user_builder = UserQueryBuilder().name("caner").age(25)
print(user_builder.get_builder_map())


# Output:
# 
# {'age': 25, 'name': 'caner'}
```

Thanks a lot to Lann for the original builder package, this is wonderful.

Not a perfect copy of the library, yet it works! Which is, what python is right? It is fast enough, and it works.