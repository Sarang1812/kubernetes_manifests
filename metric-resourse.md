1000m  = 1ghz =1 cpu
1000Mi = 1gb RAM
Aalloted 2CPU per node and 2gb of RAM
=====================================
Total Services 7
2000/7 = 285m ---> cpu
2048/7 = 292Mi ---> ram
=====================================
autoScale % considers 50
* pod will autosacl on 50% cpu usages
  i.e 285 % 50 = 142m
======================================  
Autoscale
  kubectl autoscale deploy inventory-service-app --min 1 --max 5 --cpu-percent 50
=======================================
prometheus grafana
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack --namespace prometheus
=======================================
loki,promtail-grafana
helm repo add grafana https://grafana.github.io/helm-charts
helm install promtail grafana/promtail -n prometheus
Url datasource : loki-loki-distributed-query-frontend.prometheus:3100
=========================================
jagger 
helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
helm install jaeger jaegertracing/jaeger
=========================================