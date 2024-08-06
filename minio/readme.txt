https://github.com/bitnami/charts/tree/main/bitnami/minio/#installing-the-chart

helm template mi oci://registry-1.docker.io/bitnamicharts/minio -f values.yaml --namespace minio | sed '/^#/d' | sed '/helm.sh\/chart/d' | sed '/managed-by: Helm/d' > minio.yaml
k create ns minio

on nodes:
mkdir /var/data-{0,1}
chown 1001:1001 /var/data-0
chown 1001:1001 /var/data-1

k label node infraw1 minio=yes
k label node infraw2 minio=yes
k apply -f ./minio.yaml
k apply -f ./ing.yaml


helm install my-release oci://registry-1.docker.io/bitnamicharts/minio