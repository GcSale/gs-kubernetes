# GsKubernetes
Cluster orchestration

Install dependencies and charts:
```shell script
kubectl create ns gcsale-test
kubectl create secret -n gcsale-test docker-registry regcred --docker-server=<your-registry-server> \
  --docker-username=<your-name> \
  --docker-password=<your-pword> \
  --docker-email=<your-email>

helm dependency update k8s/dealer-backend-service/
helm dependency update k8s/root_app/

helm upgrade --install -n gcsale-test dealer-backend-chart k8s/dealer-backend-service/
helm upgrade --install -n gcsale-test admin-frontend-chart k8s/admin-frontend-service/
helm upgrade --install -n gcsale-test root-chart k8s/root_app/