First, we will use Google Cloud Build to create a npm docker image with the JFrog CLI. This will enable us to use JFrog CLI to build npm packages.

> **Note** [Google Cloud Build](https://cloud.google.com/cloud-build) uses Docker to execute builds. For each build step, Cloud Build executes a Docker container as an instance of docker run.

1. Return to your Cloud Shell terminal and change directory to _gcp-gke-workshop/jfrog-cli-docker_.

2. We will use Google Cloud Build to create JFrog CLI docker image. This build command uses cloudbuild.yaml. If you look inside this file, you will find it performs following steps
- `docker build` to create the docker image
- `docker tag` to tag newly created image
- `docker login` to log into your Free Tier
- `docker push` to push the newly created image to Artifactory's Docker repository.


```
gcloud builds submit --substitutions=_JFROG_SERVER_NAME="${JFROG_SERVER_NAME}",_JFROG_USER="${JFROG_USER}",_JFROG_API_KEY="${JFROG_API_KEY}" --gcs-log-dir=gs://${PROJECT_ID}_cloudbuild/clouddays --config=cloudbuild.yaml .
```

**What's going on here?**
![Google Cloud Build JFrog CLI](../../docs/images/cloud-build-jfrog-cli.png)

This command should result in a successful build of docker image and it should be pushed to Artifactory.
![JFrog CLI build success](../../docs/images/gcp/build_success1.png)

![JFrog CLI build success](../../docs/images/gcp/build_success2.png)
