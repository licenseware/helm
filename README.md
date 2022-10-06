# Deploy Helm

## Usage

```yaml
      - uses: licenseware/helm@v1.2
        with:
          kubeconfig: ${{ secrets.KUBECONFIG_FILE }} # JSON/YAML encoded string
          kubeconfig-file: /tmp/kubeconfig # mutually exclusive with `kubeconfig`
          action: upgrade -i # upgrade -i, install, uninstall, etc.
          atomic: "1"
          build-dependencies: "1" # helm dep build
          chart-dir: ./helm
          create-namespace: "0"
          helm-version: "v3.9.4" # https://github.com/helm/helm/releases
          namespace: default
          release-name: ${{ github.event.repository.name }}
          update-dependencies: "0" # helm dep update
          values: image.tag=${{ github.sha }} # comma separated key=value pairs
          values-file: ${{ secrets.HELM_VALUES }} # JSON/YAML encoded string
          values-filepath: /tmp/values.yml
          wait: "1"
```
