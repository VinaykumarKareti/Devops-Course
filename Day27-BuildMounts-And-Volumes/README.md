Steps to follw this practical :
-----------------------------------------
-----------------------------------------

Sure, here are the steps to follow:

1. Create a Docker volume named `my_data`:
   ```bash
   docker volume create my_data
   ```

2. Create a Dockerfile for your image.

3. Build the Docker image using your Dockerfile.

4. Run a container interactively with the volume mounted:
   ```bash
   docker run -it --mount source=my_data,target=/app f10b347b0599 /bin/bash
   ```

5. Inside the Bash terminal of the container, execute:
   ```bash
   echo "Hello, Docker Volumes!" > /app/test.txt
   ```

6. Exit the Bash terminal (`exit` command).

7. Inspect the `my_data` volume to find its path:
   ```bash
   docker volume inspect my_data
   ```

   Copy the path displayed in the output.

8. On the host system, list the contents of the volume's data directory:
   ```bash
   sudo ls <path_from_inspect_output>/_data | cat test.txt
   example
    sudo ls /var/lib/docker/volumes/my_data/_data | cat test_file.txt
   ```

Now you should see the content (`Hello, Docker Volumes!`) from inside the container's volume directory on the host system.
