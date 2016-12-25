## Random notes on Flask

_When you are enlightened, write it down._

- UserMixin doesn't have a query function; this is because the `load_user()` function was not returning a user, rather an instance of the user class with only the `id` populated.

### Why use UserMixin?

[UserMixin](https://flask-login.readthedocs.io/en/latest/#flask_login.UserMixin) provides default implementations for the methods that Flask-Login expects user objects to have.

### [What is Declarative Base?](http://stackoverflow.com/a/15176114/1166929)

`declarative_base()` is a factory function that constructs a base class for declarative class definitions (which is assigned to Base variable in your example). The one you created in user.py is associated with User model.

[From the docs:](http://docs.sqlalchemy.org/en/latest/orm/extensions/declarative/api.html?highlight=base#sqlalchemy.ext.declarative.declarative_base)

> Construct a base class for declarative class definitions.

> The new base class will be given a metaclass that produces appropriate Table objects and makes the appropriate mapper() calls based on the information provided declaratively in the class and any subclasses of the class.

### Do I need to run Base.metadata.create_all() each time?

A lot of [examples](http://flask-sqlalchemy.pocoo.org/2.1/quickstart/) for starting Flask have you use an interactive db session to start the database. But shouldn't this be something that is done programmatically?
