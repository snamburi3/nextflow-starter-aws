## Instructions to submit to Container registry

1. Configure Docker with the following command:
```
gcloud auth configure-docker
```

2. Submit to Private Container Registry in the project. You need to be the directory that has the Dockerfile
```
gcloud builds submit --tag us.gcr.io/[PROJECT_ID]/samtools:v1.10 --timeout=2000s
```
