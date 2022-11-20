# httpbin

Docker image:
```
git clone git@github.com:chinaran/go-httpbin.git && cd go-httpbin
sed -i 's/80/8080/g' Dockerfile
docker buildx create --name mybuilder --use
docker buildx build --platform linux/amd64,linux/arm64 -t h0tbird/httpbin:latest --push .
```

Initial scaffolding:
```
k -n httpbin create deployment httpbin --dry-run=client --image h0tbird/httpbin -o yaml > templates/deployment.yaml
k -n httpbin create service clusterip httpbin --tcp=80:8080 --dry-run=client -o yaml > templates/service.yaml
```

Create files for hosts running this service out of kubernetes:
```
istioctl x workload entry configure \
  -r 1-16-0 \
  -f ./templates/workloadgroup.yaml \
  --clusterID kube-01 \
  --autoregister \
  -o ./tmp/vm-files
```

Trouble-shooting with `netshoot`:
```
k -n httpbin exec -it sleep-55ffcd8d69-nv92w -- zsh
```
