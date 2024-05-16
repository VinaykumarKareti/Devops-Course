**Steps to Follow:**
------------------------
------------------------

1. **Install Kubectl and Minikube**

   Ensure you have both Kubectl and Minikube installed on your system.

2. **Start Minikube**

   Start Minikube using one of the following commands based on your preferred settings:
   ```
   minikube start
   minikube start --memory=4096 --driver=virtualbox
   minikube start --memory=4096 --driver=docker
   minikube start --memory=4096 --driver=hyperkit
   ```

3. **Use the Pod Configuration File (pod.yaml)**

   Prepare a YAML file named `pod.yaml` that describes the Pod configuration.

4. **Create the Pod**

   Execute the following commands to create the Pod and check its status:
   ```
   kubectl create -f pod.yaml
   kubectl get pods
   kubectl get pods -o wide
   ```

5. **Access the Pod**

   Since the Pod is not exposed externally, access it by logging into the Minikube cluster using SSH:
   ```
   minikube ssh
   ```

6. **Access the Pod Application**

   Use `curl` to access the application running inside the Pod using its Cluster IP address:
   ```
   curl <Cluster Ipaddress of pod>
   ```

These steps outline the process of setting up and interacting with a Pod in a Minikube Kubernetes cluster. Adjust the commands and configurations as needed based on your specific environment and requirements.
