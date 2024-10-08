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
- [MKDocs](https://www.mkdocs.org/)

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

## Using an application template

### Setup

1. Create a new repository from one of the application templates
1. Update the port in the `docker-compose.yml`
1. Create an action variable in GitHub for `DOCKER_IMAGE_NAME` - this will be the name of the built Docker container

### Developing locally

The application templates contain two Docker containers; an `app` and a `dev`.

#### The `app` container

This is the container for the application.

You can override the base image (`IMAGE`) and version (`IMAGE_TAG`) in the `docker-compose.yml` but by default they use the same non-rooted image as in production. The default values are defined in the `Dockerfile`.

#### The `dev` container

See [Included scripts in `tna-python-dev`](./docker-images.md#included-scripts-in-tna-python-dev).

### Possible issues

Using these Docker images in Windows environments could encounter issues with permissions inside the container.

If this occurs, change the `IMAGE` build argument in your `docker-compose.yml` to the rooted version of the image.

**Do not change the image in the `Dockerfile` to the rooted version.**

| Image               | Rooted image             |
| ------------------- | ------------------------ |
| `tna-python`        | `tna-python-root`        |
| `tna-python-django` | `tna-python-django-root` |
