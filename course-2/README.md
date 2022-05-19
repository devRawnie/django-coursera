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

## Templates
- Made up of static HTML + Tags from Templating language (Django Templating language in case of Django)
- naming convention for a template: `<app_name>/templates/<app_name>/template-name.html`

### Django Template Language

- Anything put inside the `{{ }}` is automatically escaped
- To prevent escaping, pass `filter` tag like this: `{{ variable|filter }}`

### Template Inheritance

### Reversing URLs

- Given a URL, to find its view we can name each url in the `urls.py`
- Refer to those urls inside the `url` tag in DTL

```py
{% url 'app-name:url-name' %} # in urls.py

django.urls.reverse('url-name') # in python
```
- Specify **app_name** parameter in urls.py and use it to refer to the urls in other applications with the same syntax as mentioned above
- Can also use `namespace` argument in path() to refer to a url with that name instead of the app name


## Object lifecycle
- \_\_init__ : Constructor
- \_\_del__  : Destructor

> Convention over configuration

## Django Generic Views
- Hides all the boilerplate code for 
  - fetching all objects of the model
  - rendering the objects in a template

`django.views.generic.ListView`

## CSRF Attack

- Cross Site Request Forgery
- Lets say the user is logged in on a real website via Session Cookie
- The attacker will create a fake form, to post something else, and in the background the actual form is submitted to the legitimate website
- The legitimate website accepts the form because of the cookie value

### Defense

- Choose a large random number and put it in session (CSRF Token)
- The token is included in the form whenever the form is generated.
- The site rejects the request if incoming CSRF Token does not match the session's CSRF Token
- 

> Page refresh re-runs the entire transaction again. The post request will be sent again on refresh. This is bad UX

## POST-Redirect-GET

- Never send HTML in the response of a POST Request
- In response of a POST request, redirect the user to another page

> Flash message pattern

