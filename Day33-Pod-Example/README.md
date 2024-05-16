Steps to follow the practical: 
---------------------------------
---------------------------------

1. Install Kubectl and minikube.
2. Then Start minikube.
   minikube start
   (or)
   minikube start --memory=4096 --driver=virtualbox
   (or)
   minikube start --memory=4096 --driver=docker
   (or)
   minikube start --memory=4096 --driver=hyperkit
3. Use the pod.yaml
4. execute :
   kubectl create -f pod.yaml
   kubectl get pods
   kubectl get pods -o wide
5. to access the application or pod wi=e didn't expose the pod to outside, so to access the pod first login to the cluster.
   minikube ssh
6. curl <Cluster Ipaddress of pod>

