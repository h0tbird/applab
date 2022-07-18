# httpbin

```
k -n httpbin create deployment httpbin --dry-run=client --image mccutchen/go-httpbin:latest -o yaml > templates/deployment.yaml
k -n httpbin create service clusterip httpbin --tcp=80:80 --dry-run=client -o yaml > templates/service.yaml
```
