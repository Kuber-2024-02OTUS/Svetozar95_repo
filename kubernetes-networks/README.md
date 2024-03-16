# Выполнено ДЗ №2

 - научитесь создавать и конфигурировать объекты типа Service;
 - научитесь использовать объекты типа Service для взаимодействия между приложениями в кластере;
 - получите представление об объекте типа Ingress, научитесь создавать и конфигурировать объекты этого типа.

## В процессе сделано:
 - Ипортировал ямлы из предыдущего ДЗ (убрал только правило nodeSelector)
 - Перенастроил кластер kind
 - устновил в helm в wsl  (snap install helm --classic)
 - Добаивл репозиторий nginx-ingress (helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx)
 - обновил репозиторий helm (helm repo update)
 - установил ingonx-ingress (helm install nginx-ingress ingress-nginx/ingress-nginx --namespace homework --set controller.service.type=NodePort)
 - проверил что под запущен (   kubectl get pods -n kube-system)
 - создал service.yaml и запустил (kubectl apply -f service.yaml)
 - создал ingress.yaml и запустил (kubectl apply -f ingress.yaml)


## Как запустить проект:
 - Установить helm install nginx-ingress ingress-nginx/ingress-nginx --namespace homework --set controller.service.type=NodePort
 - Выполнить kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f deployment.yaml -f service.yaml -f ingress.yaml  из  Svetozar95_repo\kubernetes-networks


## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2