# helm-deploy-action

A GitHub Action that configures Kubernetes config, sets up Helm and deploys your Helm chart

## Usage

### Inputs

- `kubeconfig-base64`: Kubernetes config file (base64 encoded)
- `installation-name`: Helm installation name
- `namespace`: Kubernetes namespace
- `chart-path`: Path to Helm chart
- `extra-args`: Additional arguments to pass to Helm
- `token`: GitHub token
