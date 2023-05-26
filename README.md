# httpbin

Docker image:
```console
git clone git@github.com:chinaran/go-httpbin.git && cd go-httpbin
sed -i 's/80/8080/g' Dockerfile
docker buildx create --bootstrap --use --name mybuilder
docker buildx build --platform linux/amd64,linux/arm64 -t h0tbird/httpbin:latest --push .
```

Create files for hosts running this service out of kubernetes:
```console
istioctl x workload entry configure \
  -r 1-17-2 \
  -f ./templates/workloadgroup.yaml \
  --clusterID kube-01 \
  --autoregister \
  -o ./tmp/vm-files
```

Trouble-shooting with `netshoot`:
```console
k -n httpbin exec -it sleep-55ffcd8d69-nv92w -- zsh
```
