# Kind 사용 방법
- Kind Cluster 설치 
 
```sh
kind create cluster --config kind-svc-1w.yaml --name myk8s --image kindest/node:v1.31.0
```

- 기본 툴 설치
```sh
docker exec -it myk8s-control-plane sh -c 'apt update && apt install tree psmisc lsof wget bsdmainutils bridge-utils net-tools ipset ipvsadm nfacct tcpdump ngrep iputils-ping arping git vim arp-scan -y'
for i in worker worker2 worker3; do echo ">> node myk8s-$i <<"; docker exec -it myk8s-$i sh -c 'apt update && apt install tree psmisc lsof wget bsdmainutils bridge-utils net-tools ipset ipvsadm nfacct tcpdump ngrep iputils-ping arping -y'; echo; done
```
