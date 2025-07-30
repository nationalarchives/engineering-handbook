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

When using Flask, use the [flask-talisman](https://github.com/wntrblm/flask-talisman) extension to handle your CSP.

When using Django, use the [django-csp](https://github.com/mozilla/django-csp) extension to handle your CSP.

CSP is included in the [TNA application templates](../../resources/application-templates.md) that provide a frontend.

### CSP for TNA Frontend

When using TNA Frontend with the [application templates](../../resources/application-templates.md), the following CSP must be set as a minimum:

- `CSP_STYLE_SRC='self',https://fonts.googleapis.com,https://p.typekit.net,https://use.typekit.net`
- `CSP_FONT_SRC='self',https://fonts.gstatic.com,https://use.typekit.net`

## Environment variables

[TODO]
