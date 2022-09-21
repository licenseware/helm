# Deploy Helm

## Usage

```yaml
      - uses: licenseware/helm@v1
        with:
          # required 👇
          kubeconfig: ${{ secrets.KUBECONFIG_FILE }} # JSON/YAML encoded string
          # optionals 👇
          action: upgrade -i # upgrade -i, install, uninstall, etc.
          atomic: "1"
          chart-dir: ./helm
          create-namespace: "0"
          helm-version: "v3.9.4" # https://github.com/helm/helm/releases
          namespace: default
          release-name: ${{ github.event.repository.name }}
          values: image.tag=${{ github.sha }} # comma separated key=value pairs
          values-file: ${{ secrets.HELM_VALUES }} # JSON/YAML encoded string
          wait: "1"
```
