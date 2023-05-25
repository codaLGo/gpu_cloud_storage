# gpu_cloud_storage
1) создаем storage class
kubectl apply -f tron-k8s-sc.yaml
2) делаем его default - 
kubectl patch storageclass tron-k8s-sc -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
3) Создаем диски: 
pv-redis-storage.yaml
pv-tron-panel-volume.yaml
pv-tron-postgress.yaml
pv-tron-rabbitmq-volume.yaml
pv-tron-s3-volume.yaml
4) Создаем ингресс - https://kubernetes.github.io/ingress-nginx/deploy/
kubectl create namespace ingress-nginx

helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace


Проверяем:
kubectl get service ingress-nginx-controller --namespace=ingress-nginx
kubectl get ingressClasses



** можно выбрать ingress из таблицы
https://docs.google.com/spreadsheets/d/191WWNpjJ2za6-nbG4ZoUMXMpUK8KlCIosvQB0f-oq3k/edit#gid=907731238

kubectl delete ingressClasses nginx
