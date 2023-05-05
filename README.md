# Deploy Helm

## Usage

```yaml
      - uses: licenseware/helm@v1
        with:
          kubeconfig: ${{ secrets.KUBECONFIG_FILE }} # JSON/YAML encoded string
          kubeconfig-filepath: /tmp/kubeconfig # mutually exclusive with `kubeconfig`
          action: upgrade -i # upgrade -i, install, uninstall, etc.
          atomic: "1"
          build-dependencies: "0" # helm dep build
          chart-dir: ./helm
          chmod-kubeconfig: "1" # `chmod 600 kubeconfig-filepath`
          cleanup: "1" # delete all the files i.e. kubeconfig & values
          cleanup-on-fail: "1" # delete newly created resources on failure
          create-namespace: "0"
          helm-version: "v3.10.1" # https://github.com/helm/helm/releases
          namespace: default
          release-name: ${{ github.event.repository.name }}
          reuse-values: "0" # possible values: [0, 1] default: 0
          timeout: 10m
          update-dependencies: "1" # helm dep update
          values: image.tag=${{ github.sha }} # comma separated key=value pairs
          values-string: key1=value1,key2=value2 # comma separated key=value pairs
          values-file: ${{ secrets.HELM_VALUES }} # JSON/YAML encoded string
          values-filepath: /tmp/values.yml
          wait: "1"
```
