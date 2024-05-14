Follow the below steps :
	1. docker volume create my_data    ----> create a volume
  2. Create a Dockerfile.
	3. Build the image.
  4. docker run -it --mount source=my_data,target=/app f10b347b0599 /bin/bash
	5. It opens a bash terminal, In the Bash terminal execute `echo "Hello, Docker Volumes!" > /data/test.txt
     ` 
	6. execute - exit
	7. docker volume inspect my_data   ---> copy the path.
  8. sudo ls /var/lib/docker/volumes/my_data/_data | cat test_file.txt

 Now you can see the data from the host system which we have added inside the container.
 Thank You.
  
	
	
