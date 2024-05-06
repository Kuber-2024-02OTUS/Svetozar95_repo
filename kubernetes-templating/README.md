# Выполнено ДЗ №6

- Получить представление о объекте ServiceAccount, его роли в жизненном цикле подов.
- Научиться настраивать bindins для ServiceAccount c различными правами, на уровне namespace так и на уровне всего кластера.
- Понять механизм работы секретов, которые создаются для SA

## В процессе сделано:
 - установил на локальном пк(в WSL) - helmfile
 - создал namespaces.yaml (с описанием неймспейсов) и запустил (kubectl apply -f namespaces.yaml)
 - Создал heml file для установки kafka в дев и прод окружения - /kafka/helmfile.yaml

## Как запустить проект:
 - Создать необходимые неймспейсы kubectl apply -f namespaces.yaml
 - Установить helm install nginx-ingress ingress-nginx/ingress-nginx --namespace homework --set controller.service.type=NodePort
 - helm install homework-chart  ./ -n homework - основное домашнее задание
 - /kafka/helmfile.yaml - хелм файл

 
## Как проверить работоспособность:

~~~
root@Jarvis:# kubectl -n prod get pods
NAME                         READY   STATUS    RESTARTS        AGE
my-kafka-controller-0        1/1     Running   9 (124m ago)    22d
my-kafka-controller-1        1/1     Running   11 (124m ago)   22d
my-kafka-controller-2        1/1     Running   9 (124m ago)    22d
my-kafka-prod-controller-0   1/1     Running   0               2m17s
my-kafka-prod-controller-1   1/1     Running   0               2m17s
my-kafka-prod-controller-2   1/1     Running   0               2m17s
root@Jarvis:# kubectl -n dev  get pods
NAME                        READY   STATUS    RESTARTS        AGE
my-kafka-controller-0       1/1     Running   9 (124m ago)    22d
my-kafka-controller-1       1/1     Running   9 (124m ago)    22d
my-kafka-controller-2       1/1     Running   10 (124m ago)   22d
my-kafka-dev-controller-0   1/1     Running   0               2m24s
my-kafka-dev-controller-1   1/1     Running   0               2m24s
my-kafka-dev-controller-2   1/1     Running   0               2m24s
root@Jarvis:# kubectl -n homework  get pods
NAME                                                     READY   STATUS    RESTARTS   AGE
nginx-homework-deployment-5cb54fc8c8-6gml5               1/1     Running   0          11m
nginx-homework-deployment-5cb54fc8c8-cskwh               1/1     Running   0          11m
nginx-homework-deployment-5cb54fc8c8-glc6w               1/1     Running   0          11m
nginx-ingress-ingress-nginx-controller-d776646fd-lnhf4   1/1     Running   0          22m
~~~


## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2
Kubernetes Cluster: 1.27