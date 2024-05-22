# Выполнено ДЗ №7

- Понять, как устроен мониторинг кластера, его компоненты и приложения в кластере.

## В процессе сделано:
 - Установлен Promheteus Operator
 - Установлен кастомный NGINX сразу с экспортером в формате blackbox
 - Настроен ServiseMonitor

## Как запустить проект:
 - Выполнить kubectl apply -f namespace.yaml
 - Установить helm install prom-metrics oci://registry-1.docker.io/bitnamicharts/kube-prometheus  --namespace homework 
 - Выполнить kubectl apply -f configmap-nginx.yaml -f service.yaml



## Как проверить работоспособность:

1) Проброс поорта сервиса
```
root@Jarvis:/mnt/c/Users/sveto/OTUS/k8s/Svetozar95_repo/kubernetes-monitoring# kubectl -n homework  port-forward services/nginx-homework-service 80:8000
Forwarding from 127.0.0.1:80 -> 8000
Forwarding from [::1]:80 -> 8000
```
2) Проверка, что мы получаем метрики
```
root@Jarvis:~# curl 127.0.0.1:80/stub_status
Active connections: 1
server accepts handled requests
 3 3 3
Reading: 0 Writing: 1 Waiting: 0
```

3) Аналогичным способом можно проверить и метрики встроенного экспортера:

 ```
 kubectl -n homework  port-forward services/nginx-homework-service 9113:9113
 ```

 4) Что бы проверить что ServiceMonitor работает:

```
 # kubectl -n homework get servicemonitors.monitoring.coreos.com
NAME                                                 AGE
nginx-prometheus-exporter                            37s

# kubectl -n homework  port-forward services/prom-metrics-kube-promethe-prometheus 9090:9090
Forwarding from 127.0.0.1:9090 -> 9090
Forwarding from [::1]:9090 -> 9090

root@Jarvis:~# curl 127.0.0.1:9090/metrics | grep nginx
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0net_conntrack_dialer_conn_attempted_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
net_conntrack_dialer_conn_closed_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
net_conntrack_dialer_conn_established_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0",reason="refused"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0",reason="resolution"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0",reason="timeout"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="serviceMonitor/homework/nginx-prometheus-exporter/0",reason="unknown"} 0
prometheus_sd_discovered_targets{config="serviceMonitor/homework/nginx-prometheus-exporter/0",name="scrape"} 25
prometheus_target_metadata_cache_bytes{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
prometheus_target_metadata_cache_entries{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
prometheus_target_scrape_pool_sync_total{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 7
prometheus_target_scrape_pool_target_limit{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
prometheus_target_scrape_pool_targets{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
prometheus_target_sync_failed_total{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0
prometheus_target_sync_length_seconds{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0",quantile="0.01"} 0.000419084
prometheus_target_sync_length_seconds{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0",quantile="0.05"} 0.000419084
prometheus_target_sync_length_seconds{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0",quantile="0.5"} 0.000575772
prometheus_target_sync_length_seconds{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0",quantile="0.9"} 0.001027122
prometheus_target_sync_length_seconds{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0",quantile="0.99"} 0.001027122
prometheus_target_sync_length_seconds_sum{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 0.006801554000000001
prometheus_target_sync_length_seconds_count{scrape_job="serviceMonitor/homework/nginx-prometheus-exporter/0"} 7
100 98729    0 98729    0     0  18.4M      0 --:--:-- --:--:-- --:--:-- 18.8M


```

## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.30
Kubernetes Cluster: 1.27