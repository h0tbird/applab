# httpbin

Create files for hosts running this service out of kubernetes:
```console
istioctl x workload entry configure \
  -r 1-18-0 \
  -f ./templates/workloadgroup.yaml \
  --clusterID kube-01 \
  --autoregister \
  -o ./tmp/vm-files
```
