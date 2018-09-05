This repo is for understanding what is a pod and a Replication Controller.

You need to install minikube and kubectl in your environment using following instructions before running this app

https://kubernetes.io/docs/tasks/tools/install-minikube/

https://kubernetes.io/docs/tasks/tools/install-kubectl/

once installed run below commands

> minikube start

> kubectl create -f flask-pod-rc.yaml

> kubectl create -f flask-pod-rc-svc.yaml

The second one is for creating the service, if you don't create the service you cannot access the application from outside world.

Once you execute above commands, check the number of pods using 

> kubectl get pods

You should be able to see four pods <br>
```js
--------------------------------------------------------------- 
NAME             READY     STATUS    RESTARTS    AGE 
flask-app-c6ww6  1/1       Running    0           6m 
flask-app-hq4wr  1/1       Running    0           6m 
flask-app-jpbh6  1/1       Running    0           6m 
flask-app-n5smr  1/1       Running    0           4m 
---------------------------------------------------------------
```
names might change in your case. 

You can see the service created using 

> kubectl get svc (or) kubectl get services

You should be able to see below output <br>
```js
=============================================================================== 
NAME         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE . 
flask-one    NodePort    10.107.206.82   <none>        5000:31888/TCP   7m 
kubernetes   ClusterIP   10.96.0.1       <none>        443/TCP          20d
===============================================================================
```

The port 31888 in the first line might change in your case.

identify minikube ip by executing "minikube ip" command

use the ip generated in above step to access the app
> http://$(minikube ip):31888

Refresh the application to see the request being forwarded to different pods

Now delete a pod using
> kubectl delete pod <pod-name>

and when you execute "kubectl get pods" you can see a new pod getting created.

The ReplicationController makes sure that it maintains the number of replicas.

