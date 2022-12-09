# cloudflared-kustomization

For use with [FluxCD](https://fluxcd.io) to deploy [dashaun/cloudflared-arm64-docker](https://github.com/dashaun/cloudflared-arm64-docker)

## Add the GitRepository

```bash
flux create source git cloudflared \
  --url=https://github.com/dashaun-cloud/cloudflared-kustomization \
  --branch=main \
  --export > ./clusters/cluster00/cloudflared-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization cloudflared \
  --target-namespace=default \
  --source=cloudflared \
  --path="./kustomize" \
  --prune=true \
  --export > ./clusters/cluster00/cloudflared-kustomization.yaml
```
