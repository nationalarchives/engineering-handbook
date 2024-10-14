# TNA Frontend Django

> ⚠️ **TNA Frontend Django has been deprecated**

TNA Frontend Django provides Django templates for the components in [TNA Frontend](tna-frontend.md).

- [tna-frontend-django source code on GitHub](https://github.com/nationalarchives/tna-frontend-django)
- [nationalarchives-frontend-django package on PyPI](https://pypi.org/project/nationalarchives-frontend-django/)

## How to use in your own Django project

### Templates

1. Install the `nationalarchives-frontend-django` package from PyPI

2. Update your config to include templates from the package, making sure it comes after your application templates

```python
from distutils.sysconfig import get_python_lib

TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [
            os.path.join(BASE_DIR, "templates"),
            os.path.join(
              get_python_lib(), "nationalarchives-frontend-django/templates"
            )
        ],
        "APP_DIRS": True,
    }
]
```

### Styles

The CSS and JavaScript are not included in the PyPI package. You must install them separately.

Install the `@nationalarchives/frontend` package from npm with `npm install @nationalarchives/frontend`.

Add the config to enable you to use the static files:

```py
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "node_modules", "@nationalarchives", "frontend")
]
```

Import the stylesheet with:

```html
{% load static %}
<html>
  <head>
    <link rel="stylesheet" href="{% static 'nationalarchives/all.css' %}">
  </head>
  <body>
    <!-- PAGE CONTENT -->
    <script src="{% static 'nationalarchives/all.js' %}"></script>
  </body>
</html>
```

The `@nationalarchives/frontend` package also includes the SCSS if you wish to compile the CSS yourself.
