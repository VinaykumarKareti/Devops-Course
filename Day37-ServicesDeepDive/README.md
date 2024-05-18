Steps to follow this practical: 
-------------------------------
-------------------------------

### Step 1: Start Minikube

1. **Install Minikube**:
   Make sure you have Minikube installed. If not, follow the instructions [here](https://minikube.sigs.k8s.io/docs/start/).

2. **Start Minikube**:
   ```sh
   minikube start --driver=docker
   ```
   This command starts a Minikube cluster using the Docker driver. Ensure Docker is installed and running on your machine.

### Step 2: Create Deployment and Service YAML files

1. **Deployment YAML (deployment.yaml)**:
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: nginx-deployment
     labels:
       app: nginx
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: nginx
     template:
       metadata:
         labels:
           app: nginx
       spec:
         containers:
         - name: nginx
           image: nginx:1.14.2
           ports:
           - containerPort: 80
   ```

2. **Service YAML (service.yaml)**:
   ```yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: my-nginx-service
   spec:
     type: NodePort
     selector:
       app: nginx
     ports:
       - port: 80
         targetPort: 80
         nodePort: 30007
   ```

### Step 3: Deploy the NGINX Application

1. **Apply Deployment**:
   ```sh
   kubectl apply -f deployment.yaml
   ```

2. **Apply Service**:
   ```sh
   kubectl apply -f service.yaml
   ```

### Step 4: Verify Deployment and Service

1. **Check Pods**:
   ```sh
   kubectl get pods
   ```

2. **Check Service**:
   ```sh
   kubectl get svc
   ```

3. **Describe Service**:
   ```sh
   kubectl describe svc my-nginx-service
   ```

### Step 5: Access the Service from Inside Minikube

1. **SSH into Minikube**:
   ```sh
   minikube ssh
   ```

2. **Curl the Service**:
   ```sh
   curl 10.111.0.197:80
   ```
   Replace `10.111.0.197` with the ClusterIP from the `kubectl describe svc my-nginx-service` output.

3. **Exit Minikube SSH**:
   ```sh
   exit
   ```

### Step 6: Access the Service from Outside Minikube

1. **Get Minikube IP**:
   ```sh
   minikube ip
   ```
   This command outputs the Minikube IP, e.g., `192.168.49.2`.

2. **Access the Service Using NodePort**:
   ```sh
   curl http://192.168.49.2:30007
   ```

### Step 7: Use Minikube Tunnel if Needed

If the service is not accessible from outside Minikube, set up a tunnel:

1. **Run Minikube Tunnel**:
   ```sh
   minikube tunnel
   ```
   This command might need to run in a separate terminal. It sets up network routes that allow you to access NodePort services.

2. **Test Access Again**:
   ```sh
   curl http://192.168.49.2:30007
   ```

### Step 8: Stop Minikube Tunnel

To stop the tunnel, interrupt the process:

1. **If Running in Foreground**:
   Press `Ctrl+C` in the terminal where the tunnel is running.

2. **If Running in Background**:
   Find the process and kill it:
   ```sh
   ps aux | grep 'minikube tunnel'
   kill <PID>
   ```
   Or use:
   ```sh
   pkill -f 'minikube tunnel'
   ```



**If any issue related to connection failed when tried with minikube ip address
use the bellow


![image](https://github.com/VinaykumarKareti/Devops-Course/assets/105053576/f5f03e17-cfdd-408a-896f-42be997b97ac)




### Summary

1. Start Minikube.
2. Create and apply Deployment and Service YAML files.
3. Verify that the pods and service are running.
4. Access the service from inside Minikube using Minikube SSH.
5. Access the service from outside Minikube using Minikube IP and NodePort.
6. If necessary, set up a Minikube tunnel to expose the NodePort services to your host machine.
7. Stop the Minikube tunnel when done.

Following these steps should allow you to successfully deploy and access an NGINX application on Minikube from both inside and outside the cluster.
