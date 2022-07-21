# httpbin

```
k -n httpbin create deployment httpbin --dry-run=client --image mccutchen/go-httpbin:latest -o yaml > templates/deployment.yaml
k -n httpbin create service clusterip httpbin --tcp=80:8080 --dry-run=client -o yaml > templates/service.yaml
```

Create files for hosts running this service out of kubernetes:
```
istioctl-1-14-1 -r 1-14-1 x workload entry configure -f ./templates/workloadgroup.yaml -o /tmp/vm-files --clusterID cluster1
```
