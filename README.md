# gpu_cloud_storage
1) создаем storage class
kubectl apply -f tron-k8s-sc.yaml
2) делаем его default - 
kubectl patch storageclass tron-k8s-sc -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
3) Создаем диски 
pv-redis-storage.yaml
pv-tron-panel-volume.yaml
pv-tron-postgress.yaml
pv-tron-rabbitmq-volume.yaml
pv-tron-s3-volume.yaml
