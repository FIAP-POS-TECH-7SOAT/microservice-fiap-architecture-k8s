aws eks update-kubeconfig --region us-east-1 --name lanchonete-fiap      

-> install ingress no cluster

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace


<!-- Verify nginx -->
kubectl get pods -n ingress-nginx
kubectl get svc -n ingress-nginx

kubectl apply -f .\config-map
kubectl apply -f .\lanchonete-products-deployment.yml
kubectl apply -f .\lanchonete-products-service.yml   
kubectl apply -f .\lanchonete-orders-deployment.yml
kubectl apply -f .\lanchonete-orders-service.yml
kubectl apply -f .\lanchonete-payment-deployment.yml
kubectl apply -f .\lanchonete-payment-service.yml
kubectl apply -f .\lanchonete-productions-deployment.yml
kubectl apply -f .\lanchonete-productions-service.yml
kubectl apply -f .\ingress.controller.yml



kubectl delete -f .\config-map   
kubectl delete -f .\lanchonete-products-deployment.yml
kubectl delete -f .\lanchonete-products-service.yml   
kubectl delete -f .\lanchonete-orders-deployment.yml
kubectl delete -f .\lanchonete-orders-service.yml   
kubectl delete -f .\lanchonete-payment-deployment.yml
kubectl delete -f .\lanchonete-payment-service.yml   
kubectl delete -f .\lanchonete-productions-deployment.yml
kubectl delete -f .\lanchonete-productions-service.yml
kubectl delete -f .\ingress.controller.yml

kubectl config use-context docker-desktop  