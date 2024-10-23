kubectl create configmap mysql-init-scripts --from-file=init.sql

kubectl apply -f mysql-deployment.yaml
kubectl apply -f mysql-service.yaml
kubectl apply -f flask-app-deployment.yaml
kubectl apply -f flask-app-service.yaml

curl -X POST http://<flask-app-ip>:<port>/add \
-H "Content-Type: application/json" \
-d '{"value": "Sample data"}'


curl http://<flask-app-ip>:<port>/fetch
