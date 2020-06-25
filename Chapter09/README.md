- cd to Chapter09

- compare the app.js in v1, v2 and v3 folders

- use ingress to expose endpoint outside the cluster (for example, my hostname)
minikube addons enable ingress

- deploy the first version
kubectl apply -f kubia-deployment.yaml --record

- see deployment status
kubectl rollout status deployment kubia-deployment

- see the new created pods
kubectl get pod

- delete one and see what happens
kubectl delete pod <a-pod-name>
kubectl get pod

- see the replicasets created and how its sufix is equal to the pod "middle name"
kubectl get replicasets

- see the ingress created
kubectl get ingress

- executing endpoint to see rolling update
while true;sleep 1; do curl kubia.example.com; done

- doing a deployment
change image to v2
kubectl apply -f kubia-deployment.yaml
see what happens to the curls

- doing a rollback
kubectl rollout undo deployment kubia-deployment

- doing a new deployment to v3
change image to v3
kubectl apply -f kubia-deployment.yaml
see what happens to the curls

- delete every resouce in current namespace
kubectl delete all --all && kubectl delete ingress kubia-ingress
