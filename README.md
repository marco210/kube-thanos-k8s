# kube-thanos-k8s
Deploy thanos receiver cluster for Prometheus on kubernetes
## Component
### Thanos
1. Thanos-receive-router
2. Thanos-receive-ingestor
3. Thanos-query
4. Thanos-compact
5. Thanos-store-gateway
### S3 Storage
Minio
### Prometheus

### Kubernetes
#### Service
1. thanos-receive-router
2. thanos-receive-ingestor
3. 
# Network Topology

# Prerequisites
Create namespace `thanos`
Prometheus config:
>remoteWrite: \
>  \- url: "http://thanos-receive-router.thanos.svc.cluster.local:19291/api/v1/receive"`


## Installation
### Create local volumes
1. Create for 3 nodes `Thanos-receive-ingestor` \
i. mkdir -p /mnt/thanos-receive-data\
ii. chown -R ansible /mnt/thanos-receive-data
2. Create for S3 Storage `minio`  \
i. mkdir -p /mnt/minio-data\
ii. chown -R ansible /mnt/minio-data\

### Create Storage
1. thanos-receive-storage-class.yaml
2. thanos-receive-pv.yaml
3. minio-pv.yaml
4. minio-pvc.yaml
