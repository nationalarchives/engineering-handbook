# Useful resources

## Status

| Resource                    | Status                                                                                                                                                              |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TNA Frontend                | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/tna-frontend/tests.yml?style=flat-square&event=push&branch=main)             |
| TNA Frontend Jinja          | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/tna-frontend-jinja/ci.yml?style=flat-square&event=push&branch=main)          |
| Docker images               | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/docker/build.yml?style=flat-square&event=push&branch=main)                   |
| Flask application template  | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/flask-application-template/cd.yml?style=flat-square&event=push&branch=main)  |
| Django application template | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/django-application-template/cd.yml?style=flat-square&event=push&branch=main) |

## Relationships

<img src="../assets/resource-relationships.drawio.svg">

## Process for new components and styles

```mermaid
graph TD;
    Figma --> Stakeholders;
    Stakeholders --> Decision{Signed off?};
    Decision --> |Yes| tna-frontend
    Decision --> |No| Figma
    tna-frontend --> Tests{Standards met?};
    Tests --> |Yes| npm["Publish TNA Frontend to npm"]
    Tests --> |No| tna-frontend
    npm --> prototype["Use in prototypes"];
    npm --> tna-frontend-jinja;
    tna-frontend-jinja --> Update["Update Jinja templates"];
    Update --> JinjaTests{Templates match?};
    JinjaTests --> |Yes| PyPI["Publish TNA Frontend Jinja to PyPI"]
    JinjaTests --> |No| Update
    npm --> |"Styles (CSS and JavaScript)"|Application["Use in application"];
    PyPI --> |"Jinja templates (HTML)"|Application["Use in application"];
```
