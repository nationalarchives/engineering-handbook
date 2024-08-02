# Security

## CSP

A [CSP](https://content-security-policy.com/) is a header returned from a server request (or less often through a `<meta>` element in the `<head>` of the HTML) which states which resources can load on your page.

This helps reduce the risk of XSS attacks.

The CSP is a whitelist of domains, hashes and nonces for elements such as:

- scripts
- images
- stylesheets
- fonts
- forms
- iframes

When using Flask, use the [flask-talisman](https://github.com/GoogleCloudPlatform/flask-talisman) extension to handle your CSP.

When using Django, use the [django-csp](https://github.com/mozilla/django-csp) extension to handle your CSP.

## Environment variables

[TODO]
