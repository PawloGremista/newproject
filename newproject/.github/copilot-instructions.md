# Project Instructions

## Project overview

This is a reusable Django project template using PostgreSQL.

The template provides a working foundation for new Django applications:
database connection, migrations, authentication, Django Admin, static and
media files, and basic project configuration.

Keep the project simple. Do not introduce additional technologies or
dependencies unless they are actually required.

## Technology

- Python
- Django 6.1
- PostgreSQL
- Django ORM
- Django built-in authentication
- python-dotenv for environment variables

## Project structure

The main Django project is located in `newproject/`.

Django applications are separate from the main project configuration.

### `core/`

`core` is the initial example application included in the template.

It serves two purposes:

1. It is a starting point for the first application of a new project.
2. It demonstrates the connection between Django, the Django ORM and
   PostgreSQL.

The `Item` model is an example model used to demonstrate database operations,
Django migrations and Django Admin.

`core` is not intended to be a generic container for unrelated application
logic. When a project grows, functionality should be placed in an appropriate
Django application.

### `users/`

`users` contains authentication-related functionality such as registration,
login and logout.

The project currently uses Django's built-in User model.

Do not introduce a custom User model unless the project requirements justify
it.

### `templates/`

The root `templates/` directory contains templates shared by the whole
project, such as the base layout and homepage.

Application-specific templates should be stored inside their application, for
example:

    users/templates/users/login.html

### `static/`

Contains project static files such as CSS and JavaScript.

### `media/`

Contains user-uploaded files.

### `newproject/`

Contains the main Django project configuration, including settings and the
root URL configuration.

## Database

PostgreSQL is the project's database.

Use Django ORM for database operations by default.

Prefer Django ORM methods such as:

    Model.objects.all()
    Model.objects.get(...)
    Model.objects.filter(...)
    Model.objects.create(...)

over raw SQL.

Use raw SQL only when there is a specific reason that the ORM is not a
reasonable solution.

Database schema changes must be handled using Django migrations.

After changing models, create and apply migrations when appropriate:

    py manage.py makemigrations
    py manage.py migrate

Do not modify migration files that have already been applied unless there is
a specific reason to do so.

## Authentication

Use Django's built-in authentication system unless project requirements
specifically require another solution.

Authentication-related functionality belongs in the `users` application.

Use Django's existing authentication forms and utilities where appropriate.

## Security

Never hardcode:

- passwords
- database credentials
- API keys
- Django secret keys
- other sensitive configuration

Sensitive configuration must be stored in environment variables.

The `.env` file must never be committed to Git.

Do not suggest committing credentials or other secrets to the repository.

When handling user-provided redirect destinations such as `next`, use
Django's mechanisms for validating safe redirects.

## Views

Keep views simple and focused on handling HTTP requests.

Use Django's existing forms, authentication utilities and ORM instead of
reimplementing functionality that Django already provides.

Avoid putting large amounts of business logic directly into views.

## Templates

Use Django templates for server-rendered HTML.

Reuse the shared `layout.html` template where appropriate.

Keep application-specific templates inside their respective applications.

Do not put significant business logic into templates.

## Dependencies

Do not add a Python package when Django or the Python standard library
already provides a suitable solution.

Add dependencies only when they provide functionality that is actually
required.

Keep `requirements.txt` synchronized with intentional dependency changes.

## Tests

New functionality should have appropriate tests when practical.

Use Django's built-in testing framework unless the project explicitly adopts
another solution.

The example `Item` model may be used as a simple starting point for testing
database operations.

## Code style

Follow normal Django and Python conventions.

Prefer simple, readable and maintainable code.

Use descriptive names.

Avoid unnecessary abstraction and premature optimization.

Preserve the existing project structure and style when modifying code unless
there is a good reason to change it.

## Architecture

Do not introduce Docker, Django REST Framework, JWT, Redis, Celery or other
additional infrastructure unless the project actually requires it.

Do not create new abstractions or applications merely for the sake of
following a particular architectural pattern.

When a change could significantly affect the project architecture, explain
the relevant options before implementing it.