# helm-deploy-action

A GitHub Action that configures Kubernetes config, sets up Helm and deploys your Helm chart

## Usage

- run `cat ~/.kube/config | base64 | pbcopy` to base64 encode your kubeconfig & copy to your clipboard
- add secret as `KUBE_CONFIG` to your repo, paste value from previous step
- add step to your deployment action:
  ```
  ...
  steps:
      - uses: actions/checkout@v4
  
      - name: Helm Configure & Deploy
            uses: dorukgezici/helm-deploy-action@v1
            with:
              kubeconfig-base64: ${{ secrets.KUBE_CONFIG }}
              installation-name: ${{ env.PROJECT_NAME }}
              chart-path: backend/k8s-helm
              extra-args: "--set image.tag=${{ github.sha }}"
              token: ${{ github.token }}
  ...
  ```

### Inputs

- `kubeconfig-base64`: Kubernetes config file (base64 encoded)
- `installation-name`: Helm installation name
- `namespace`: Kubernetes namespace
- `chart-path`: Path to Helm chart
- `wait-ready`: (boolean) Wait for the installation to be ready
- `extra-args`: Additional arguments to pass to Helm
- `token`: GitHub token
