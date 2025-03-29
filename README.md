# v1 - Initial Release

This is the first version of the `build-and-deploy-k8s` Composite Action. It automates the process of:
- Building a Docker image
- Pushing it to GitHub Container Registry
- Deploying it to a Kubernetes cluster

### Usage
```yaml
- uses: ercansualp/build-and-deploy-k8s@v1
  with:
    DOCKERFILE_PATH: 'path/to/Dockerfile'
    DEPLOYMENTFILE_PATH: 'path/to/deployment.yaml'
    IMAGE_NAME: 'my-app'
    IMAGE_TAG: '${{ github.run_id }}'
    REPOSITORY: '${{ github.repository }}'
    USERNAME: '${{ github.repository_owner }}'
    IMAGE_PULL_SECRETS: 'github-registry-creds'
    K8S_NAMESPACE: 'default'
    ROOT_DIRECTORY: '.'
    PERSONAL_ACCESS_TOKEN: '${{ secrets.PASSWORD }}'
    KUBE_CONFIG: '${{ secrets.KUBECONFIG }}'
