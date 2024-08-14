# TNA Frontend Jinja

![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/tna-frontend-jinja/ci.yml?style=flat-square&event=push&branch=main)

TNA Frontend Jinja provides Jinja templates for the components in [TNA Frontend](tna-frontend.md).

- Source code: [tna-frontend-jinja on GitHub](https://github.com/nationalarchives/tna-frontend-jinja)
- Package: [tna-frontend-jinja on PyPI](https://pypi.org/project/tna-frontend-jinja/)

## How to use in your own Flask project

### Templates

1. Install the `tna-frontend-jinja` package from PyPI

2. Update your config to include templates from the package, making sure it comes after your application templates

```python
from flask import Flask
from jinja2 import ChoiceLoader, PackageLoader


def create_app():
    app = Flask(__name__)

    app.jinja_loader = ChoiceLoader(
        [
            PackageLoader("app"),
            PackageLoader("tna_frontend_jinja"),
        ]
    )
```

By having the application templates first, you can overwrite any TNA Frontend template by making a version in your application's template directory without having to change the package.

### Styles and JavaScript

The CSS and JavaScript are not included in the PyPI package. You must install them separately.

Install and use the `@nationalarchives/frontend` package from npm with `npm install @nationalarchives/frontend`.

Ensure you use the version of TNA Frontend that matches the version of TNA Frontend Jinja as described in the [TNA Frontend Jinja README](https://github.com/nationalarchives/tna-frontend-jinja#compatibility-with-tna-frontend).

### Using the templates

An example of using the templates in your service:

```
{% extends 'base.html' %}

{% from 'components/card/macro.html' import tnaCard %}

{% block content %}
  {{ tnaButton({
    'text': 'Visit us',
    'href': 'https://www.nationalarchives.gov.uk/about/visit-us/'
  }) }}
{% endblock %}
```

For a list of components and their macro options along with examples of use, check the [TNA Design System components](https://nationalarchives.github.io/design-system/components/).

The Jinja macros use the same options as the Nunjucks macros.
