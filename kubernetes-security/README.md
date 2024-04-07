# Выполнено ДЗ №5

- Получить представление о объекте ServiceAccount, его роли в жизненном цикле подов.
- Научиться настраивать bindins для ServiceAccount c различными правами, на уровне namespace так и на уровне всего кластера.
- Понять механизм работы секретов, которые создаются для SA



## В процессе сделано:
 - Ипортировал ямлы из предыдущего ДЗ 
 - создал service-acc-monitoring.yaml и запустил (kubectl apply -f service-acc-monitoring.yaml)
 - создал service-acc-cd-admin.yaml и запустил (kubectl apply -f service-acc-cd-admin.yaml)
 - изменил deployment.yaml
 


## Как запустить проект:
 - Установить helm install nginx-ingress ingress-nginx/ingress-nginx --namespace homework --set controller.service.type=NodePort
 - Выполнить kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f pvc.yaml -f cm.yaml -f deployment.yaml -f service.yaml -f ingress.yaml  из  Svetozar95_repo\kubernetes-volumes
 - сделать ключ на сутки (kubectl create token cd --duration 1440m > cd-token)
 - добавить его (в base64) в  service-acc-cd-admin.yaml
 - выполнить  kubectl apply -f service-acc-monitoring.yaml service-acc-cd-admin.yaml
 - kubeconfig.yaml -  для подключения. Проверял через export перепеменной и проверки подов  kubectl get pods 
 



## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2
Kubernetes Cluster: 1.27