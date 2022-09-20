# Deploy Helm

## Usage

```yaml
      - uses: licenseware/helm@v1
        with:
          # required 👇
          kubeconfig: ${{ secrets.KUBECONFIG_FILE }}
          # optionals 👇
          action: upgrade -i
          atomic: "1"
          chart-dir: ./helm
          create-namespace: "0"
          helm-version: "3.9.4"
          namespace: default
          release-name: ${{ github.event.repository.name }}
          values: image.repository=ghcr.io/${{ github.repository }},image.tag=${{ github.sha }}
          values-file: ${{ secrets.HELM_VALUES }}
          wait: "1"
```
