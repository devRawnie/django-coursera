# DJANGO

## MVT Framework

### Model

- Related to data
- Decides how information is stored and retrieved
- Defines entities and their relations

- `django.db.connection.queries` returns the latest SQL queries ran in the application

#### Migrations

- Evolves the database with new changes
- `python manage.py makemigrations` checks the models.py files for any change, and creates corresponding migration files
- `python manage.py migrate` applies all the migrations in the database
- 

### View

- Decides which data / template the user is requesting
- Sends the data to template to be rendered on screen
- Orchestrator of request response cycle

### Template

- Frontend part of Django
- Defines the layout of information displayed on the frontend

### Object Relational Mapping (ORM)

- Maps tables to Python objects
- Use object to store and retrieve data
- Portability across different dialects (Same syntax used across different versions of SQL like Postgres, MySQL etc)

## Views

- Django looks at incoming Request URL and uses `urls.py` and delegates it to a view from `views.py`
- A view handles the request and does any required processing to
  - fetch data from model
  - render a template to return to user

### URL Dispatcher

- Create a `URLConf` file in python which contains mappings between url endpoints and corresponding views
- Requests can be routed to 
- pre-defined django class
- a function in views.py
- a class in views.py with definition for `get()` and `post()`

### Request Response
- When django recieves an incoming request, it creates an object of type `HTTPRequest` and populates it with the metadata about the request
- This object is passed as the first argument to the **view function**
- Each view should return an object of type `HTTPResponse`

> django.utils.html.escape() escapes any html/js passed to it. This should be used whenever we accept user input
