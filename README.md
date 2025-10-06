# helm

## Step 1: Install Helm chart
```
helm install clover-monitoring   oci://ghcr.io/ketan-cloverinfotech/clover-monitoring/clover-monitoring  -n monitoring
**Upgrade**
helm upgrade clover-monitoring   oci://ghcr.io/ketan-cloverinfotech/clover-monitoring/clover-monitoring   --version 0.1.1   -n monitoring
```
