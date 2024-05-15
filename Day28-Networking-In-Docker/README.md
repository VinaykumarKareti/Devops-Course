Steps for this pratical :
-------------------------
-------------------------

1. create three images of name - login, logout and payments
2. Example Docker CMD is- docker run -d --name Imag_name nginx:latest
3. Note:- while creating the payments container, run the below  command:
   docker run -d --name=payments --network=<Custom_Network_Name> nginx:latest
4. Till now, we have created 3 containers, Now execute the bellow command:
   docker exec -it login bash
5. It opens the bash terminal inside the container, Now execute the command:
   >> apt update
   >> apt-get install iputils-ping -y
   >> ping -V
   >> exit
7. Now copy the Ip address of the logout conatainer, to copy the Ipaddress follow the command:
   docker inspect logout
8. Now again execute the command:
   docker exec -it login bash
   # go inside the login container
   >> ping <IPaddress of logout container>
9. You will see the data is transmiting between the containers.
10. In the Same copy the IPAddrees of payments container, and do the same process.
11. You will find there is no data is trnsmiting bettween the payments and login container.

 Thank You.
