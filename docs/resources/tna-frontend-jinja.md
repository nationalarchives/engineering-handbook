# TNA Frontend Jinja

TNA Frontend Jinja provides Jinja templates for the components in [TNA Frontend](../tna-frontend).

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

### Styles

The CSS and JavaScript are not included in the PyPI package. You must install them separately.

Install and use the `@nationalarchives/frontend` package from npm with `npm install @nationalarchives/frontend`.

Ensure you use the version of TNA Frontend that matches the version of TNA Frontend Jinja as described in the [TNA Frontend Jinja README](https://github.com/nationalarchives/tna-frontend-jinja#compatibility-with-tna-frontend). This ensures your CSS from TNA Frontend matches the HTML from TNA Frontend Jinja.
