##  Building and Pushing a Docker Container

This article guides you through creating a Docker container for your resume website, allowing you to package your code and dependencies for easy deployment. 

**1. Building the Docker Image:**

* `docker build -t website .`: This command builds a Docker image named "website" using the instructions in a file named "Dockerfile" (assumed to be present in your current directory). The dot (.) indicates the current directory as the context for building the image.

**2. Running the Container:**

* `docker run -itd -p 80:80 --name website website`: This command starts a container based on the "website" image.
    * `-itd`:  
        * `-i`: Runs the container in interactive mode, allowing you to attach to it later.
        * `-t`: Allocates a pseudo-TTY (terminal) for interactive sessions.
        * `-d`: Runs the container in detached mode, allowing the process to continue in the background.
    * `-p 80:80`: Maps the container's port 80 (web server) to your host machine's port 80, making the website accessible through a browser.
    * `--name website`: Assigns a friendly name "website" to the container for easier identification.

**3. Tagging the Image:**

* `sudo docker tag website togo407/website:latest`: This command creates a tag named "togo407/website:latest" for the existing "website" image. 
    * `togo407`: Replace with your Docker Hub username.
    * `latest`: This tag refers to the most recent version of the image.

**4. Pushing the Image to Docker Hub:**

**(Requires a Docker Hub account)**

* `sudo docker login`: Authenticates you with Docker Hub so you can push your image.
* `sudo docker push togo407/website:latest`: Pushes the tagged image ("togo407/website:latest") to your Docker Hub repository.

**5. Managing Docker Containers:**

These commands help you manage Docker containers:

* `sudo docker stop fb5077dc1bcd`: Stops a specific container by its ID (replace with the actual container ID)
* `sudo docker ps -a`: Lists all containers, including stopped ones.
* `sudo systemctl restart docker`: Restarts the Docker service.
* `sudo systemctl status docker`: Checks the status of the Docker service.
* `sudo docker rm 4e4c99047548`: Removes a stopped container by its ID (replace with the actual container ID).
* `sudo docker images`: Lists all Docker images on your system.
* `sudo docker rmi 0d4a9c69cef6`: Removes a specific Docker image by its ID (replace with the actual image ID).
