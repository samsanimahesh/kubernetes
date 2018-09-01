This example is for demonstrating the capabilities of deployments in kubernetes

To create a deployment and associated service, execute below command

kubectl create -f flask-deployment.yaml

To view the deployments, execute below command

kubectl get deployments 

Deployments will create a specialized ReplicationController called ReplicationSet, to view that execute below command

kubectl get rs

you will be able to see the following output

NAME                          DESIRED   CURRENT   READY     AGE
flask-deployment-85f85c8d96   1         1         1         12s

To scale the deployments execute below command

kubectl scale deployment/flask-deployment --replicas=6

Delete a pod using below command
kubectl delete pod <POD_NAME>

if you execute "kubectl get pods", kubernetes will create a new pod to ensure that 6 replicas always exist

If you want to change the image of the deployment on the fly, execute below command

kubectl set image deployment/flask-deployment flask-deployment=samsanimahesh/flask-hostname-image

To pause the deployment

kubectl rollout pause deployment flask-deployment

To Resume the deployment

kubectl rollout resume deployment flask-deployment

To undo the deployment

kubectl rollout undo deployment flask-deployment

---------------------------------------------------------

identify minikube ip by executing "minikube ip" command

use the ip generated in above step to access the app http://$(minikube ip):31888
