Steps to follow for this practical :
---------------------------------------
---------------------------------------


1. **Create Three Docker Images**:
   - Use the `docker run` command to create containers based on these images.
     ```bash
     docker run -d --name login nginx:latest
     docker run -d --name logout nginx:latest
     docker run -d --name payments --network=<Custom_Network_Name> nginx:latest
     ```

2. **Access the Bash Terminal of the 'login' Container**:
   - Open a bash terminal inside the 'login' container to perform commands.
     ```bash
     docker exec -it login bash
     apt update
     apt-get install iputils-ping -y
     ping -V
     exit
     ```

3. **Retrieve IP Address of the 'logout' Container**:
   - Obtain the IP address of the 'logout' container using `docker inspect`.
     ```bash
     docker inspect logout
     ```

4. **Ping between Containers**:
   - Access the 'login' container again and ping the IP address of the 'logout' container.
     ```bash
     docker exec -it login bash
     ping <IPaddress of logout container>
     ```

5. **Verify Data Transmission**:
   - Observe data transmission between the 'login' and 'logout' containers.

6. **Repeat for the 'payments' Container**:
   - Obtain the IP address of the 'payments' container and attempt to ping from the 'login' container.
     ```bash
     docker exec -it login bash
     ping <IPaddress of payments container>
     ```

7. **Observations**:
   - Notice that data transmission occurs successfully between the 'login' and 'logout' containers, demonstrating communication within the same network.
   - However, data transmission between the 'login' and 'payments' containers fails due to isolation within different networks.

By following these steps, you'll gain hands-on experience with Docker containers, networking, and inter-container communication.
