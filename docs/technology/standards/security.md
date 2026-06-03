# Security

## CSP

A content security policy ([CSP](https://content-security-policy.com/)) is a header returned from a server request (or less often through a `<meta>` element in the `<head>` of the HTML) which states which resources can load on your page.

This helps reduce the risk of XSS attacks.

The CSP is a whitelist of domains, hashes and nonces for elements such as:

- scripts
- images
- stylesheets
- fonts
- forms
- iframes

When using Flask, use the [Flask Talisman module](https://nationalarchives.github.io/python-utilities/flask/#talisman) of [TNA Python Utilities](../../resources/python-utilities.md) to handle your CSP.

[Django 6 supports CSP](https://docs.djangoproject.com/en/6.0/ref/csp/). When using older versions of Django, use the [django-csp](https://github.com/mozilla/django-csp) extension to handle your CSP.

CSP is included in the [TNA application templates](../../resources/application-templates.md) that provide a frontend.

### CSP for TNA Frontend

When using TNA Frontend with the [application templates](../../resources/application-templates.md), the following CSP must be set as a minimum:

- `CSP_STYLE_SRC='self',https://fonts.googleapis.com,https://p.typekit.net,https://use.typekit.net`
- `CSP_FONT_SRC='self',https://fonts.gstatic.com,https://use.typekit.net`

When using the Flask Talisman module in TNA Python Utilities, you can add these in with preset CSP policies using `allow_google_content_security_policy=True` and `allow_typekit_content_security_policy=True`.

```python
from flask import Flask
from tna_utilities.flask import Talisman

app = Flask(__name__)
Talisman(
    app,
    allow_google_content_security_policy=True,
    allow_typekit_content_security_policy=True,
)
```

## Data types

Certain data types are considered either private or public.

See a [list of example data types and how secure/private they should be kept](https://docs.google.com/spreadsheets/d/1mg3CHSLma7ZR7YI78wl9EwTdZ0WNTXWHqLJiXunQlI8/edit?usp=sharing).
