# GCP cheatsheet

## Basics

### Setting default project
```
gcloud config set project [project-id]
```

### Setting default zone

```
gcloud config set compute/zone [zone]
```

Eg.
```
gcloud config set compute/zone europe-west1-b
```

### Logging into cloud shell from your terminal (not from Google Cloud Console web app)
```
gcloud alpha cloud-shell ssh
```

## Google Kubernetes Engine

### Fetching credentials for a running cluster - required to perform any deployment

```
gcloud container clusters get-credentials [cluster-name]
```