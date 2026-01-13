# Application templates

## Python applications

Flask, Django and FastAPI application templates come with:

- [TNA Base Docker images](./docker-images.md) with non-root users
- Docker compose for local development
- Docker build scripts for GitHub Actions ready to run
- Environment configuration
- [Poetry](../technology/backend/python.md#poetry) for dependency management
- Tests
- Development containers for formatting and testing code
- Formatting configuration
- Healthcheck endpoints
- [MKDocs](https://www.mkdocs.org/)

### Flask

GitHub repo: [flask-application-template](https://github.com/nationalarchives/flask-application-template)

- Flask
- CSP ([Flask Talisman](https://github.com/GoogleCloudPlatform/flask-talisman))
- Pytest
- [TNA Frontend](./tna-frontend.md)/[TNA Frontend Jinja](./tna-frontend-jinja.md)
- A small API client library

### Django

GitHub repo: [django-application-template](https://github.com/nationalarchives/django-application-template)

- Django
- Database for Docker compose
- CSP ([Django CSP](https://github.com/mozilla/django-csp))
- [TNA Frontend](./tna-frontend.md)/[TNA Frontend Jinja](./tna-frontend-jinja.md)
- A small API client library
- [WhiteNoise](https://github.com/evansd/whitenoise) for serving static files in production

### FastAPI

GitHub repo: [fastapi-application-template](https://github.com/nationalarchives/fastapi-application-template)

- FastAPI

### Using the Python application templates

#### Setup

1. Create a new repository from one of the application templates (click the "Use this template" button in the top right of the GitHub repo page)
1. Update the port in the `docker-compose.yml` so you can run multiple applcations at the same time without conflict
1. Create an action variable in GitHub for `DOCKER_IMAGE_NAME` - this will be the name of the built Docker container
1. Ideally, update the project name in `pyproject.toml`

#### Developing locally

The `app` container is the container for the application.

By default, the production image specified in the `Dockerfile` is [`tna-python`](./docker-images.md#tna-python).

When developing, the base image getes overwritten in the `docker-compose.yml` to [`tna-python-dev`](./docker-images.md#tna-python-dev) which runs as root and comes with some scripts to help you format and test your code.

> ⚠️ **Do not change the image in the `Dockerfile` to the `dev` version.**

Pushing to the `main` branch will automatically build a Docker image and upload it to GitHub alongside the source code.

## Static sites

GitHub repo: [static-site-template](https://github.com/nationalarchives/static-site-template)

The static site template is for small, self-contained sites with no requirement to handle backend logic. It is designed to be built and deployed to simple, static hosting solutions.

- 11ty
- [TNA Frontend](./tna-frontend.md)
- Markdown rendering
- SCSS compilation
- JS transpilation
