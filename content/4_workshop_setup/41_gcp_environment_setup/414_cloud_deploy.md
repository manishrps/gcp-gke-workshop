In this section, we will create a Cloud Deploy pipeline to deploy our app in test, stage and prod environments.

1. First select **Cloud Deploy** from your product catalog and **enable** it if it's already not enabled.

2. Execute the following  command to add ***clouddeploy.jobRunner*** role to the serice account.

```
gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member=serviceAccount:$(gcloud projects describe $PROJECT_ID \
    --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --role="roles/clouddeploy.jobRunner"
```

3. Now execute the below command to add the **Kubernetes Developer** permissions.

```
gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member=serviceAccount:$(gcloud projects describe $PROJECT_ID \
    --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --role="roles/container.developer"
```

4. Navigate to **IAM** , locate the **cloud build service account** and add below two roles if it does not have it already.

```
Cloud Deploy Releaser
```
```
Service Account User
```

5. Now in your cloud shell navigate to _gcp-gke-workshop/workshop-app_ and execute below command. This will register your pipeline with the Google Cloud Deploy service and with targets (test,stage and prod).

```
gcloud deploy apply --file clouddeploy.yaml --region=us-central1 --project=$PROJECT_ID
```

![Cloud Deploy command](../../../docs/images/cloud-deploy-pipeline-create.png)

6. Once above command execute successfully, navigate to **Cloud Deploy** and you should see one pipeline with name **clouddays-demo**

    ![Cloud Deploy pipeline](../../../docs/images/cloud-deploy-pipeline-view.png)
