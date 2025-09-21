## You should follow the following steps for push helm chart
```
# 1) login (use a PAT with read:packages, write:packages)
helm registry login ghcr.io -u ketan-cloverinfotech --password <PAT>

# 2) push (omit chart name in the path)
helm push sample-metrics-app-0.1.0.tgz \
  oci://ghcr.io/ketan-cloverinfotech/kube-prometheus-stack-official

# 3) install later (include chart name + version)
helm install sample \
  oci://ghcr.io/ketan-cloverinfotech/kube-prometheus-stack-official/sample-metrics-app \
  --version 0.1.0 \
  --namespace monitoring --create-namespace

```
