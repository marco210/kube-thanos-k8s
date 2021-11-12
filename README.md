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
![Markdown](https://github.com/marco210/kube-thanos-k8s/blob/main/images/2021-11-12%2010_15_03-kube-thanos.png)
# Prerequisites
Create namespace `thanos`
> kubectl create namespace thanos
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
### Create config
1. secret.yaml
2. thanos-receive-router-configmap.yaml

### Create Thanos-receive-router
1. thanos-receive-router-service.yaml
2. thanos-receive-router-serviceAccount.yaml
3. thanos-receive-router-deployment.yaml

### Create Thanos-receive-ingestor
1. thanos-receive-ingestor-default-service.yaml
2. thanos-receive-ingestor-serviceAccount.yaml
3. thanos-receive-ingestor-default-statefulSet.yaml

### Create Thanos-bucket
1. thanos-bucket-service.yaml
2. thanos-bucket-serviceAccount.yaml
3. thanos-bucket-deployment.yaml

### Create S3 Storage minio
1. minio-service.yaml
2. minio.yaml

### Create Thanos-Store
1. thanos-store-service.yaml
2. thanos-store-serviceAccount.yaml
3. thanos-store-statefulSet.yaml

### Create Thanos-Query
1. thanos-query-service.yaml
2. thanos-query-serviceAccount.yaml
3. thanos-query-deployment.yaml

### Create Thanos-Compact
1. thanos-compact-service.yaml
2. compact-serviceAccount.yaml
3. thanos-compact-statefulSet.yaml


### Create ServiceMonitor
1. thanos-query-serviceMonitor.yaml
2. thanos-store-serviceMonitor.yaml
3. thanos-compact-serviceMonitor.yaml

# REFRENCES
https://github.com/thanos-io/kube-thanos
