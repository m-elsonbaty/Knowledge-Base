**Setting Up Jenkins with Docker on Ubuntu**

This guide outlines the steps to install and configure Jenkins, a popular continuous integration and continuous delivery (CI/CD) tool, using Docker on an Ubuntu system.

**Prerequisites:**

  - Ubuntu system with root privileges
  - Docker installed

**1. Install Docker Compose**

Docker Compose simplifies multi-container applications. Run the following command as root:

```bash
sudo apt install docker-compose
```

**2. Start and Enable Docker Service**

Ensure Docker is running and enabled for automatic startup:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

**3. Grant Docker Group Permissions**

Add your username to the `docker` group for permission to run Docker commands without `sudo`:

```bash
sudo usermod -aG docker <your_username>
```

**4. Log in to Docker Hub**

Authenticate with Docker Hub to pull Jenkins images:

```bash
docker login
```

**5. Pull Jenkins Docker Image**

Run the following command to download the latest Jenkins Long-Term Support (LTS) image with Java 17:

```bash
docker pull jenkins/jenkins:lts-jdk17
```

**6. Run Jenkins Container**

Start a Jenkins container, mapping ports 8080 (web interface) and 50000 (Jenkins slave) to the host machine, persisting data in the `jenkins_home` volume, and restarting on failure:

```bash
docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk17
```

**7. View Initial Password**

Retrieve the initial password generated during container startup by viewing the container logs:

```bash
docker logs <container_id>
```

**8. Access Jenkins Web Interface**

Open the Jenkins web interface in your browser at `http://localhost:8080`. Use the password obtained from the logs to log in.

**9. Environment Variables**

Manage environment variables within Jenkins from the web interface:

  - Navigate to `http://localhost:8080/env-vars.html/`

**Additional Notes:**

  - Replace `<your_username>` with your actual username in step 3.
  - The `jenkins_home` volume persists Jenkins configuration and data, ensuring they're preserved even if the container restarts.
  - This guide provides a basic setup. Refer to the official Jenkins documentation ([https://jenkins.io/doc/](https://www.google.com/url?sa=E&source=gmail&q=https://jenkins.io/doc/)) for further configuration and customization options.

