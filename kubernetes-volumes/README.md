# Выполнено ДЗ №4

 - Научиться создавать в кластере объкты, описывающие персистентные хранилища и научиться подключаться их к подам;
 - Научиться создавать объект ConfigMap и монтировать его как valume;
 - Получиться представление об объекте StorageClass и механизме provisioning для PV;



## В процессе сделано:
 - Ипортировал ямлы из предыдущего ДЗ 
 - создал cm.yaml и запустил (kubectl apply -f cm.yaml)
 - создал pvc.yaml и запустил (kubectl apply -f pvc.yaml)
 - изменил deployment.yaml


## Как запустить проект:
 - Установить helm install nginx-ingress ingress-nginx/ingress-nginx --namespace homework --set controller.service.type=NodePort
 - Выполнить kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f pvc.yaml -f cm.yaml -f deployment.yaml -f service.yaml -f ingress.yaml  из  Svetozar95_repo\kubernetes-volumes




## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2