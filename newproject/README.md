# Django Project Template

A basic Django project template with PostgreSQL, authentication,
environment variables, static/media files and Django Admin.

The project is intended to be used as a starting point for new Django applications.

## Requirements

- Python 3.12+
- PostgreSQL 15+
- pip

## Included

- Django 6.1
- PostgreSQL support
- Django ORM and migrations
- Django built-in authentication
- Login / Register / Logout
- Django Admin
- Static files
- Media files
- Environment variables using `.env`
- Basic example model
- Git configuration
- Requirements file

## Project structure

    newproject/
    ├── core/
    │   ├── migrations/
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py
    │   ├── tests.py
    │   ├── urls.py
    │   └── views.py
    │
    ├── users/
    │   ├── migrations/
    │   ├── templates/
    │   │   └── users/
    │   │       ├── login.html
    │   │       └── register.html
    │   ├── admin.py
    │   ├── apps.py
    │   ├── models.py
    │   ├── tests.py
    │   ├── urls.py
    │   └── views.py
    │
    ├── newproject/
    │   ├── settings.py
    │   ├── urls.py
    │   ├── views.py
    │   ├── asgi.py
    │   └── wsgi.py
    │
    ├── static/
    │   ├── css/
    │   └── js/
    │
    ├── templates/
    │   ├── homepage.html
    │   └── layout.html
    │
    ├── media/
    ├── .env.example
    ├── .gitignore
    ├── manage.py
    ├── README.md
    └── requirements.txt

## Installation

### 1. Clone the repository

    git clone <repository-url>
    cd <project-directory>

### 2. Create a virtual environment

    py -m venv .venv

Activate it:

Windows:

    .venv\Scripts\activate

### 3. Install dependencies

    py -m pip install -r requirements.txt

### 4. Configure environment variables

Create a `.env` file based on `.env.example`:

    SECRET_KEY=your-secret-key
    DEBUG=True

    DB_NAME=your_database
    DB_USER=postgres
    DB_PASSWORD=your_password
    DB_HOST=localhost
    DB_PORT=5432

Do not commit `.env` to the repository.

### 5. Prepare the database

Create a PostgreSQL database matching the values in `.env`.

Then run:

    py manage.py migrate

### 6. Create an administrator

    py manage.py createsuperuser

### 7. Start the development server

    py manage.py runserver

The application will be available at:

    http://127.0.0.1:8000/

The Django administration panel is available at:

    http://127.0.0.1:8000/admin/

## Authentication

The template uses Django's built-in authentication system.

Available views:

- `/login/`
- `/register/`
- `/logout/`

Users are stored in PostgreSQL using Django's authentication system.

The template does not use a custom User model. Project-specific user data
can be added later if required.

## Database

The project uses PostgreSQL as its database.

Django communicates with PostgreSQL through the Django ORM.

Example:

    Item.objects.all()

    Item.objects.create(
        name="Example",
        description="Example item"
    )

Database structure is managed using Django migrations.

Create migrations:

    py manage.py makemigrations

Apply migrations:

    py manage.py migrate

## Django Admin

Models can be registered in `admin.py` and managed through Django Admin.

Example:

    from django.contrib import admin
    from .models import Item

    admin.site.register(Item)

## Environment variables

Sensitive configuration is stored in `.env`.

The following values should not be committed to Git:

- database passwords
- Django `SECRET_KEY`
- API keys
- other credentials

`.env.example` is provided as a template for required environment variables.

## Static and media files

Static files are stored in:

    static/

Uploaded media files are stored in:

    media/

Do not commit user-uploaded media files unless the project specifically requires it.

## Development

Run the development server with:

    py manage.py runserver

Run tests with:

    py manage.py test

Check the project configuration with:

    py manage.py check

## Project development principles

- Use Django ORM for database operations.
- Keep secrets outside the source code.
- Use migrations to modify database structure.
- Use Django's built-in authentication unless project requirements justify a custom solution.
- Keep views and business logic reasonably separated as the project grows.