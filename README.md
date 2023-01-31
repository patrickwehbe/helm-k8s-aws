# Deploy to Kubernetes
This GitHub Actions workflow deploys a Node.js application to a Kubernetes cluster on AWS.

## Triggers
The workflow is triggered when code is pushed to the main branch.

## Environment Variables
AWS_REGION: The AWS region to deploy the cluster in.
IMAGE_NAME: The name of the Docker image to be built and deployed.

## Jobs
### Setup
Checks out the code from the repository
Configures AWS CLI with the access key and secret key stored as secrets
Installs Helm v3.4.0
### Create-resources
Creates an S3 bucket
Creates an EKS cluster
### Build-image
Checks out the code again
Builds and pushes the Docker image with the name nodejs-app and the tag ${{ env.GITHUB_SHA }}
### Deploy
Deploys the application using Helmfile and the helmfile sync command
### Test
Runs tests and prints the message Running tests


### Secrets
The following secrets must be added to the GitHub repository for this workflow to run:

* AWS_ACCESS_KEY_ID
* AWS_SECRET_ACCESS_KEY
