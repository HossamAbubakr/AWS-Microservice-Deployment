# Udagram Image Sharing Platform, AWS Microservice Deployment

## Table of Contents

- [Summary](#Summary)

- [Technologies](#Technologies)

- [Docker Images](#Docker-Images)

- [Testing](#Testing)

- [Structure](#Structure)

- [Continuous Integration](#Continuous-Integration)

- [Configuration](#Configuration)

- [Deployment](#Deployment)

## Summary

This Instagram clone was configured and deployed to AWS as part of my **AWS Cloud Developer Nanodegree from Udacity**.

**It demonstrates my understanding and ability to configure the following :**

#### AWS services

AWS S3  
AWS IAM  
AWS RDS - PostgreSQL

#### Containerization

Build Docker image.  
Kubernetes service scaling.  
Debugging Docker containers.  
Pushing Docker images to a registry.  
Create and deploy a Kubernetes cluster.  
Setting up a reverse proxy server using Nginx.  
Using Docker Compose to run multiple containers.  
Running a Docker container with environment variables.

#### Microservice Configuration

Divide a monolithic application into smaller services.

#### Deployment

CI using Travis.  
Automated testing with Travis.  
CI/CD (Continuous Integration/Continuous Delivery) Principles.

## Technologies

Node.JS was used for the backend.  
Docker was used for containerization.  
Ionic/Angular was used for the frontend.  
Travis was used for continuous integration.  
Docker Hub was used as the image registry.  
Typescript was used as the language of choice.  
Kubernetes was used for container orchestration.  
Kubectl was used as the Kubernetes command-line tool of choice.

## Docker-Images

1. [Frontend.](https://hub.docker.com/repository/docker/hossamabubakr/udacity-frontend)
2. [ReverseProxy.](https://hub.docker.com/repository/docker/hossamabubakr/reverseproxy)
3. [RestAPI Feed Backend.](https://hub.docker.com/repository/docker/hossamabubakr/udacity-restapi-feed)
4. [RestAPI User Backend.](https://hub.docker.com/repository/docker/hossamabubakr/udacity-restapi-user)

## Testing

Each microservice includes a Postman Collection Json file that can be imported for testing

## Structure

```
|   .travis.yml
|   README.md
|
+---Deployment Pictures
|       App1.PNG
|       App2.PNG
|       App3.PNG
|       Compose.PNG
|       Pods.PNG
|
+---deployment
|   +---docker
|   |       .dockerignore
|   |       docker-compose-build.yaml
|   |       docker-compose.yaml
|   |       Dockerfile
|   |       nginx.conf
|   |
|   \---k8s
|           aws-secret.yaml.EXAMPLE
|           backend-feed-deployment.yaml
|           backend-feed-service.yaml
|           backend-user-deployment.yaml
|           backend-user-service.yaml
|           env-configmap.yaml.EXAMPLE
|           env-secret.yaml.EXAMPLE
|           external-service.yaml
|           frontend-deployment.yaml
|           frontend-service.yaml
|           reverseproxy-deployment.yaml
|           reverseproxy-service.yaml
|
+---frontend
|   |   angular.json
|   |   Dockerfile
|   |   ionic.config.json
|   |   package-lock.json
|   |   package.json
|   |   tsconfig.json
|   |   tslint.json
|   |
|   +---e2e
|   |   |   protractor.conf.js
|   |   |   tsconfig.e2e.json
|   |   |
|   |   \---src
|   |           app.e2e-spec.ts
|   |           app.po.ts
|   |
|   +---src
|   |   |   global.scss
|   |   |   index.html
|   |   |   karma.conf.js
|   |   |   main.ts
|   |   |   polyfills.ts
|   |   |   test.ts
|   |   |   tsconfig.app.json
|   |   |   tsconfig.spec.json
|   |   |
|   |   +---app
|   |   |   |   app-routing.module.ts
|   |   |   |   app.component.html
|   |   |   |   app.component.spec.ts
|   |   |   |   app.component.ts
|   |   |   |   app.module.ts
|   |   |   |
|   |   |   +---api
|   |   |   |       api.module.ts
|   |   |   |       api.service.ts
|   |   |   |
|   |   |   +---auth
|   |   |   |   |   auth.module.ts
|   |   |   |   |
|   |   |   |   +---auth-login
|   |   |   |   |       auth-login.component.html
|   |   |   |   |       auth-login.component.scss
|   |   |   |   |       auth-login.component.spec.ts
|   |   |   |   |       auth-login.component.ts
|   |   |   |   |
|   |   |   |   +---auth-menu-button
|   |   |   |   |   |   auth-menu-button.component.html
|   |   |   |   |   |   auth-menu-button.component.scss
|   |   |   |   |   |   auth-menu-button.component.spec.ts
|   |   |   |   |   |   auth-menu-button.component.ts
|   |   |   |   |   |
|   |   |   |   |   \---auth-menu-user
|   |   |   |   |           auth-menu-user.component.html
|   |   |   |   |           auth-menu-user.component.scss
|   |   |   |   |           auth-menu-user.component.spec.ts
|   |   |   |   |           auth-menu-user.component.ts
|   |   |   |   |
|   |   |   |   +---auth-register
|   |   |   |   |       auth-register.component.html
|   |   |   |   |       auth-register.component.scss
|   |   |   |   |       auth-register.component.spec.ts
|   |   |   |   |       auth-register.component.ts
|   |   |   |   |
|   |   |   |   +---models
|   |   |   |   |       user.model.ts
|   |   |   |   |
|   |   |   |   \---services
|   |   |   |           auth.guard.service.spec.ts
|   |   |   |           auth.guard.service.ts
|   |   |   |           auth.service.spec.ts
|   |   |   |           auth.service.ts
|   |   |   |
|   |   |   +---feed
|   |   |   |   |   feed.module.ts
|   |   |   |   |
|   |   |   |   +---feed-item
|   |   |   |   |       feed-item.component.html
|   |   |   |   |       feed-item.component.scss
|   |   |   |   |       feed-item.component.spec.ts
|   |   |   |   |       feed-item.component.ts
|   |   |   |   |
|   |   |   |   +---feed-list
|   |   |   |   |       feed-list.component.html
|   |   |   |   |       feed-list.component.scss
|   |   |   |   |       feed-list.component.spec.ts
|   |   |   |   |       feed-list.component.ts
|   |   |   |   |
|   |   |   |   +---feed-upload
|   |   |   |   |   |   feed-upload.component.html
|   |   |   |   |   |   feed-upload.component.scss
|   |   |   |   |   |   feed-upload.component.spec.ts
|   |   |   |   |   |   feed-upload.component.ts
|   |   |   |   |   |
|   |   |   |   |   \---feed-upload-button
|   |   |   |   |           feed-upload-button.component.html
|   |   |   |   |           feed-upload-button.component.scss
|   |   |   |   |           feed-upload-button.component.spec.ts
|   |   |   |   |           feed-upload-button.component.ts
|   |   |   |   |
|   |   |   |   +---models
|   |   |   |   |       feed-item.model.ts
|   |   |   |   |
|   |   |   |   \---services
|   |   |   |           feed.provider.service.spec.ts
|   |   |   |           feed.provider.service.ts
|   |   |   |
|   |   |   +---home
|   |   |   |       home.module.ts
|   |   |   |       home.page.html
|   |   |   |       home.page.scss
|   |   |   |       home.page.spec.ts
|   |   |   |       home.page.ts
|   |   |   |
|   |   |   \---menubar
|   |   |           menubar.component.html
|   |   |           menubar.component.scss
|   |   |           menubar.component.spec.ts
|   |   |           menubar.component.ts
|   |   |
|   |   +---assets
|   |   |   |   shapes.svg
|   |   |   |
|   |   |   \---icon
|   |   |           favicon.png
|   |   |
|   |   +---environments
|   |   |       environment.prod.ts
|   |   |       environment.ts
|   |   |
|   |   \---theme
|   |           variables.scss
|   |
|   \---udacity_tests
|           git_test.sh
|
+---restapi-feed
|   |   Dockerfile
|   |   package-lock.json
|   |   package.json
|   |   tsconfig.json
|   |   udacity-c2-restapi.postman_collection.json
|   |
|   +---mock
|   |       xander0.jpg
|   |       xander1.jpg
|   |       xander2.jpg
|   |
|   \---src
|       |   aws.ts
|       |   sequelize.ts
|       |   server.ts
|       |
|       +---config
|       |       config.ts
|       |
|       +---controllers
|       |   \---v0
|       |       |   index.router.ts
|       |       |   model.index.ts
|       |       |
|       |       \---feed
|       |           +---models
|       |           |       FeedItem.ts
|       |           |
|       |           \---routes
|       |                   feed.router.ts
|       |
|       \---migrations
|               20190325-create-feed-item.js
|               20190328-create-user.js
|
\---restapi-user
    |   Dockerfile
    |   package-lock.json
    |   package.json
    |   tsconfig.json
    |   udacity-c2-restapi.postman_collection.json
    |
    +---mock
    |       xander0.jpg
    |       xander1.jpg
    |       xander2.jpg
    |
    \---src
        |   aws.ts
        |   sequelize.ts
        |   server.ts
        |
        +---config
        |       config.ts
        |
        +---controllers
        |   \---v0
        |       |   index.router.ts
        |       |   model.index.ts
        |       |
        |       \---users
        |           +---models
        |           |       User.ts
        |           |
        |           \---routes
        |                   auth.router.ts
        |                   user.router.ts
        |
        \---migrations
                20190325-create-feed-item.js
                20190328-create-user.js
```

## Continuous Integration

A Travis yaml configuration file has already been created, configured and included with the project

## Configuration

You will have to configure/use the following services

1. AWS S3
2. AWS IAM
3. AWS Redis - PostgreSQL

Making the following changes to the files located at /deployment/k8s :  
Rename  
aws-secret.yaml.EXAMPLE to aws-secret.yaml  
and replace

```
___INSERT_AWS_CREDENTIALS_FILE__BASE64____
```

With your AWS config file content encoded with Base64

Rename  
env-configmap.yaml.EXAMPLE to env-configmap.yaml  
and replace

```
  AWS_BUCKET: ___INSERT_AWS_BUCKET___
  AWS_PROFILE: ___INSERT_AWS_PROFILE___
  AWS_REGION: ___INSERT_AWS_REGION___
  JWT_SECRET: ___INSERT_JWT_SECRET___
  POSTGRESS_DB: ___INSERT_POSTGRESS_DB___
  POSTGRESS_HOST: ___INSERT_POSTGRESS_HOST___
```

With the AWS services information

Rename
env-secret.yaml.EXAMPLE to env-secret.yaml
And replace the following in them

```
  POSTGRESS_USERNAME: ___INSERT_POSTGRESS_USERNAME__BASE64___
  POSTGRESS_PASSWORD: ___INSERT_POSTGRESS_PASSWORD__BASE64___
```

With the AWS Redis information encoded with Base64

## Deployment

### 1. Docker Compose

Navigate to folder

```shell
cd deployment/docker/
```

Build the images for each of our defined services

```shell
docker-compose -f docker-compose-build.yaml build --parallel
```

Run Container

```shell
docker-compose up
```

### 2. Kubernetes

[Install Kubectl](https://kubernetes.io/docs/tasks/tools/)

Navigate to folder

```shell
cd deployment/k8s/
```

Create deployments and services

```shell
kubectl apply -f reverseproxy-deployment.yaml,reverseproxy-service.yaml,frontend-deployment.yaml,frontend-service.yaml,backend-feed-deployment.yaml,backend-feed-service.yaml,backend-user-deployment.yaml,backend-user-service.yaml
```

View running pods

```shell
kubectl get pod
```

You can also build the project using the included configuration settings

```shell
npm run build
```
