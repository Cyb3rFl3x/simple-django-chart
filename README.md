# simple-django-chart
If you are currently working on a web application that is based on Django and will be run in Kubernetes, this is the easiest way. For easy maintenance and deployment of the application a Helm Chart is used.

# Steps
1. Build your application in a Python Docker container (Info 1)
2. Upload it to your container-repo like dockerhub, acr or other (Info 2)
3. Add the name of your repository into values.yaml (Info 3)
4. Run your container in Kubernetes (Info 4)

## Info
1. The official way running a django application is to deploy the application in a python container and install django
2. Build and upload Container:
```bash
docker build -t simple-django-chart .
docker run --name simple-django-chart -p 8000:8000 -d simple-django-chart
# If works, push to DockerHub or other Container Registries
```
3. `repository: simple-django-chart:latest` -> `repository: your repo`
4. Run your container:
```bash
helm template .
helm install . --generate-name
```

Define $POD_NAME by pasting the printed commands from your CLI.

```bash
kubectl --namespace default port-forward $POD_NAME 8000:8088
```

goto: localhost:8088

## PULL 
```bash
docker run --name simple-django-chart -p 8000:8000 -d cyb3rfl3x/simple-django-chart:latest
```