### Build Docker
```
docker build -t ubuntu-aws .
```

### Run AWS nextflow
```
nextflow run test-aws.nf -profile awsbatch -c aws.config -w s3://AWS-Bucket/nextflow-test
```


### GCP

1. Enable the following APIs
```
Container Registry API
Cloud Life Sciences API 
Cloud Build API
```

2. Authenticate
```
gcloud auth login
gcloud auth application-default login
```

3. Add Project Name to the config file ~/.config/gcloud/application_default_credentials.json
```
project_id": "PROJECT-ID",
```

4. Set project
```
gcloud config set project [PROJECT_ID]
```

5. Export environment variables
```
export NXF_VER="20.10.0"
export NXF_MODE=google
export NXF_DEBUG=3
export PROJECT="PROJECT_ID"
export GOOGLE_APPLICATION_CREDENTIALS=~/.config/gcloud/application_default_credentials.json
```

6. Run GCP nextflow

* a. Make sure the below staging bucket exists

* b. Make sure the service account (Compute Engine default service account) used by nextflow can write to the bucket

* c. Replace PROJECT_ID in gcp/gcp.config with your GCP Project ID
```
nextflow run gcp/test-gcp.nf -profile gls -c gcp/gcp.config -w gs://PROJECT_ID/test-sn
```

### Troubleshooting

1. Make sure the network and subnet is 'default' with 'auto' mode
2. Enable 'Private Google access' for the network/subnet
3. Specify disk size in the process. The default disk space is 500GB in nextflow!

## References
1. Nextflow on GCP: https://www.nextflow.io/docs/latest/google.html
