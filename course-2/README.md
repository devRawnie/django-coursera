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
-  
