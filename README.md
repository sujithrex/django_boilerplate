# django_boilerplate

A production-ready Django boilerplate with environment-based configuration, MySQL support, and proper static/media file handling.

## Project Structure
```
project/
├── core/                   # Main project directory
│   ├── settings.py        # Project settings with env support
│   ├── urls.py            # Main URL configuration
│   └── wsgi.py            # WSGI configuration
├── web/                   # Main application
│   ├── urls.py           # Application URLs
│   └── views.py          # Application views
├── static/               # Static files (CSS, JS, Images)
├── media/                # User uploaded files
├── templates/            # Project templates
├── .env.dev             # Development environment variables
├── .env.pro             # Production environment variables
└── requirements.txt      # Project dependencies
```

## Features
- Environment-based configuration (.env.dev and .env.pro)
- MySQL database support with PyMySQL
- Static and media files configuration
- Production security settings
- Email configuration support
- Template directory structure

## Prerequisites
- Python 3.x
- MySQL Server
- Virtual Environment (recommended)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd <project-directory>
```

2. Create and activate virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: .\venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Set up environment:
For development:
```bash
cp .env.dev .env
```
For production:
```bash
cp .env.pro .env
```

5. Configure your database in .env:
```
DB_NAME=your_db_name
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
DB_PORT=3306
```

6. Run migrations:
```bash
python manage.py migrate
```

7. Create superuser (optional):
```bash
python manage.py createsuperuser
```

8. Run the development server:
```bash
python manage.py runserver
```

## Environment Variables

### Development (.env.dev)
```
DEBUG=True
SECRET_KEY=your-dev-secret-key
ALLOWED_HOSTS=localhost,127.0.0.1

DB_NAME=dev_db_name
DB_USER=dev_user
DB_PASSWORD=dev_password
DB_HOST=localhost
DB_PORT=3306

EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_HOST_USER=dev@example.com
EMAIL_HOST_PASSWORD=dev_email_password
EMAIL_USE_TLS=True
```

### Production (.env.pro)
```
DEBUG=False
SECRET_KEY=your-production-secret-key
ALLOWED_HOSTS=*

DB_NAME=prod_db_name
DB_USER=prod_user
DB_PASSWORD=prod_password
DB_HOST=localhost
DB_PORT=3306

EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_HOST_USER=prod@example.com
EMAIL_HOST_PASSWORD=prod_email_password
EMAIL_USE_TLS=True

SECURE_SSL_REDIRECT=True
SESSION_COOKIE_SECURE=True
CSRF_COOKIE_SECURE=True
SECURE_BROWSER_XSS_FILTER=True
SECURE_CONTENT_TYPE_NOSNIFF=True
```

## Dependencies
- Django==5.0.3
- PyMySQL==1.1.1
- python-dotenv==1.0.1
- Pillow==10.4.0
- Other dependencies in requirements.txt

## Directory Usage

### Static Files
Place your static files in the `static/` directory:
```
static/
├── css/
├── js/
└── images/
```

### Media Files
User-uploaded files will be stored in the `media/` directory.

### Templates
Place your HTML templates in the `templates/` directory:
```
templates/
├── base.html
└── web/
    └── your_templates.html
```

## Security Notes
1. Never commit .env files containing sensitive data
2. Change the SECRET_KEY in production
3. Set DEBUG=False in production
4. Update ALLOWED_HOSTS with your domain in production
5. Use strong database passwords

## Development Workflow
1. Create new apps using: `python manage.py startapp app_name`
2. Add new apps to INSTALLED_APPS in settings.py
3. Create models in your apps
4. Make migrations: `python manage.py makemigrations`
5. Apply migrations: `python manage.py migrate`

## Production Deployment
1. Use production .env file
2. Collect static files: `python manage.py collectstatic`
3. Configure your web server (Nginx/Apache)
4. Set up SSL certificate
5. Configure database backup
