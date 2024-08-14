# Application templates

| Resource                     | Status                                                                                                                                                               |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Flask application template   | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/flask-application-template/cd.yml?style=flat-square&event=push&branch=main)   |
| Django application template  | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/django-application-template/cd.yml?style=flat-square&event=push&branch=main)  |
| FastAPI application template | ![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/fastapi-application-template/cd.yml?style=flat-square&event=push&branch=main) |


All application templates come with:

- [TNA Base Docker images](./docker-images.md) with non-root users
- Docker compose for local development
- Docker build scripts for GitHub Actions ready to run
- Environment configuration
- [Poetry](../technology/backend/python.md#poetry) for dependency management
- Tests
- Development containers for formatting and testing code
- Formatting configuration
- Healthcheck endpoints

## Flask

GitHub repo: [flask-application-template](https://github.com/nationalarchives/flask-application-template)

### Features

- Flask
- CSP ([Flask Talisman](https://github.com/GoogleCloudPlatform/flask-talisman))
- Pytest
- [TNA Frontend](./tna-frontend.md)/[TNA Frontend Jinja](./tna-frontend-jinja.md)
- A small API client library

## Django

GitHub repo: [django-application-template](https://github.com/nationalarchives/django-application-template)

### Features

- Django
- Database for Docker compose
- CSP ([Django CSP](https://github.com/mozilla/django-csp))
- [TNA Frontend](./tna-frontend.md)/[TNA Frontend Jinja](./tna-frontend-jinja.md)
- A small API client library
- [WhiteNoise](https://github.com/evansd/whitenoise) for serving static files in production

## FastAPI

GitHub repo: [fastapi-application-template](https://github.com/nationalarchives/fastapi-application-template)

### Features

- FastAPI
