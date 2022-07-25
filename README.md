# httpbin

Docker image:
```
git clone git@github.com:chinaran/go-httpbin.git && cd go-httpbin
docker buildx create --name mybuilder --use
docker buildx build --platform linux/amd64,linux/arm64 -t h0tbird/httpbin:latest --push .
```

Initial scaffolding:
```
k -n httpbin create deployment httpbin --dry-run=client --image h0tbird/httpbin -o yaml > templates/deployment.yaml
k -n httpbin create service clusterip httpbin --tcp=80:80 --dry-run=client -o yaml > templates/service.yaml
```

Create files for hosts running this service out of kubernetes:
```
istioctl x workload entry configure \
  -r 1-14-1 \
  -f ./templates/workloadgroup.yaml \
  --clusterID cluster1 \
  --autoregister \
  -o ./tmp/vm-files
```
