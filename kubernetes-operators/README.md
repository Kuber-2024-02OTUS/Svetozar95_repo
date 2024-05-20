# Выполнено ДЗ №7

 - Научиться создавать и конфигурировать CR и CRD ресурсы.
 - Научиться создавать и устанавливать в кластер собственные Operators

## В процессе сделано:
 - Написал CRD
 - сделал сервис аккаунт
 - написал дейплоймент
 - сделал кастомтный деплоймент
## Как запустить проект:
 - Выполнить kubectl apply -f crd-mysql.yaml -f service-acc.yaml -f service-acc.yaml -f service-acc.yaml
 
## Как проверить работоспособность:

~~~
root@Jarvis:/mnt/c/Users/sveto/OTUS/k8s/Svetozar95_repo/kubernetes-operators# kubectl get service example-mysql
NAME            TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
example-mysql   ClusterIP   None         <none>        3306/TCP   99s
root@Jarvis:/mnt/c/Users/sveto/OTUS/k8s/Svetozar95_repo/kubernetes-operators# kubectl get pods
NAME                             READY   STATUS    RESTARTS   AGE
example-mysql-6b48bb7bfc-p7bs2   1/1     Running   0          5m23s
mysql-operator-d6c69997d-8l2w6   1/1     Running   0          5m25s
root@Jarvis:/mnt/c/Users/sveto/OTUS/k8s/Svetozar95_repo/kubernetes-operators# kubectl get deployments.apps
example-mysql   mysql-operator
root@Jarvis:/mnt/c/Users/sveto/OTUS/k8s/Svetozar95_repo/kubernetes-operators# kubectl get deployments.apps
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
example-mysql    1/1     1            1           5m32s
mysql-operator   1/1     1            1           5m34s
~~~


## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.30
Kubernetes Cluster: 1.27