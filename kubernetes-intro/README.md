# Выполнено ДЗ №1

 - [ ] В данном домашнем задании вы научитесь формировать локальное окружение, запустят локальную версию kubernetes при помощи minikube, научатся использовать CLI утилиту kubectl для управления kubernetes.

## В процессе сделано:
 - Установлен kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2
 - Создал namespace.yaml
 - Создал pod.yaml
 - Создал congigmap.yaml для настройки вебсервера
 - Приминил конфигурацию: kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f pod.yaml
 - Пробросил порт в wsl: kubectl port-forward pod/web -n homework  80:8000
 - Проверил что файлик скачивается. wget   127.0.0.1:80/index.html
 - проверяем что файл скачен: ls -la | grep index.html

## Как запустить проект:
 - Выполнить kubectl apply -f namespace.yaml  -f configmap-nginx.yaml  -f pod.yaml  Svetozar95_repo\kubernetes-intro

## Как проверить работоспособность:
 - Пробросил порт в wsl: kubectl port-forward pod/web -n homework  80:8000
 - Проверил что файлик скачивается. wget   127.0.0.1:80/index.html
 - проверяем что файл скачен: ls -la | grep index.html

## PR checklist:
 - [] Выставлен label с темой домашнего задания


## Платформа выполнения:
OS: Windows 11
Kubernetes: kind version 0.20.0 в WSL 2.0 с Docker Desktop 4.25.2