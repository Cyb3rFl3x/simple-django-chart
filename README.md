# simple-django-chart
If you are currently working on a web application that is based on Django and will be run in Kubernetes, this is the easiest way. For easy maintenance and deployment of the application a Helm Chart is used.

# Steps
1. Build your application in a Python Docker container (Info 1)
2. Upload it to your container-repo like dockerhub, acr or other
3. Add the name of your repository into values.yaml (Info 2)
4.

## Info
1. The official way running a django application is to deploy the application in a python container and install django in it.
2. `repository: simple-django-chart:latest` -> `your repo`

## BUILD

```bash
docker build -t simple-django-chart .
docker run --name simple-django-chart -p 8000:8000 -d simple-django-chart
```

## PULL
```bash
docker run --name simple-django-chart -p 8000:8000 -d cyb3rfl3x/simple-django-chart:latest
```