# Application templates

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

## FastAPI

GitHub repo: [fastapi-application-template](https://github.com/nationalarchives/fastapi-application-template)

### Features

- FastAPI
