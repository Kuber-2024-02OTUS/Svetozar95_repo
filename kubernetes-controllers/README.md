# Выполнено ДЗ №2

 - В данном домашнем задании вы научитесь формировать Replicaset, Deployment для своего приложения. Научатся управлять обновлением своего приложения. Так же научатся использовать механизм Probes для проверки работоспособности своих приложений.

## В процессе сделано:
 - Установлен kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2
 - Создал namespace.yaml
 - Создал deployment.yaml
 - Создал congigmap.yaml для настройки вебсервера
 - Приминил конфигурацию: kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f deployment.yaml
 - Пробросил порт в wsl: kubectl port-forward pod/web -n homework  80:8000
 - Проверил что файлик скачивается. wget   127.0.0.1:80/index.html
 - проверяем что файл скачен: ls -la | grep index.html

##  Задание со звездочкой 

Добавить к манифесту deployment-а спецификацию, обеспечивающую запуск подов деплоймента, только на нодах кластера, имеющих метку homework=true

ВЫПОЛНЕНО. Лог в файле .txt

## Как запустить проект:
 - kubectl label nodes  kind-worker  homework=true
 - kubectl label nodes  kind-worker2  homework=true
 - Выполнить kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f deployment.yaml  из  Svetozar95_repo\kubernetes-controllers

## Как проверить работоспособность:
 - Пробросил порт в wsl: kubectl port-forward pod/web -n homework  80:8000
 - Проверил что файлик скачивается. wget   127.0.0.1:80/index.html
 - проверяем что файл скачен: ls -la | grep index.html

## PR checklist:
 - [ДА] Выставлен label с темой домашнего задания


## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2