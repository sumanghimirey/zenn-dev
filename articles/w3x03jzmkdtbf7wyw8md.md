---
title: "Troubleshooting Docker Deployment Issues with Artifact Registry and *** App Engine"
emoji: ""
type: "test-data"
topics: ['test-data']
published: False
---

# Troubleshooting Docker Deployment Issues with Artifact Registry and *** App Engine

Troubleshooting Docker Deployment Issues with Artifact Registry and *** App Engine

Are you facing a critical problem while deploying your application using Docker with Artifact Registry and *** App Engine? If you are encountering the following error related to a *** service (such as Secret Manager) even though you are using a service account for deployment:

```
Error: ERROR: root: Access to *** service was denied (403)
```

I have some ideas and solutions that might help you overcome this issue. One of the possible solutions is to configure the `***_APPLICATION_CREDENTIALS` environment variable in your Dockerfile. By utilizing the Application Default Credentials (ADC), you can provide the necessary access permissions to solve this problem.

Here are the steps you can follow to resolve the issue:

1. Open your Dockerfile and add the following line to configure the `***_APPLICATION_CREDENTIALS` environment variable:
```
ENV ***_APPLICATION_CREDENTIALS /path/to/service/account/key.json
```
Make sure to replace `/path/to/service/account/key.json` with the actual path to your service account key file.

2. If you are using GitHub Actions for your deployment, you will also need to add the same environment variable to your workflow file. Update your GitHub Actions workflow YAML file and add the following lines under the `env` section:
```
env:
  ***_APPLICATION_CREDENTIALS: ${{ secrets.***_APPLICATION_CREDENTIALS }}
```
This will enable the GitHub Action to use the service account credentials during the deployment process.

By following these steps, you should be able to resolve the access denied error and successfully deploy your application using Docker with Artifact Registry and *** App Engine.

I hope this information is helpful to you. If you have any further questions or need more assistance, please feel free to reach out.


![](/images/yAyyZ09Ua3CYiQoLa40Y/W3x03jzmkdtBf7WYw8md/114526bc-2e48-4acc-97f3-2681af5ebd3b.jpg)