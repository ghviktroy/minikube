# minikube
#Развертывание в Minikube
#Сборка и загрузка образов:
#bash
eval $(minikube docker-env)
docker build -t webapp-image ./web
docker build -t db-image ./db
minikube cache add webapp-image
minikube cache add db-image

#Применение конфигураций:
kubectl apply -f k8s/

#Проверка статуса:
kubectl get all -o wide

#Инвентаризация кластера (пример в Excel)
№Нода	ОС	Количество ядер	Память	IP-адрес	Установленное ПО
minikube	Container-Optimized OS	2	4GB	192.168.49.2	Docker, kube

#Доступ к веб приложению
minikube service web-service
