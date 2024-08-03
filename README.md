# Docker-Cheatsheet

This repository contains all the Docker knowledge you need to get started as a beginner.

## Docker Installation

### Install Docker using the following command on your Linux machine:
```bash
sudo apt install docker.io
```
### Installing Docker on Windows

1. **Download Docker Desktop:**
    - Install the Docker Desktop for Windows by clicking [HERE](https://desktop.docker.com/win/stable/Docker%20Desktop%20Installer.exe).
    - Download the Docker Desktop installer.

2. **Install Docker Desktop:**
    - Run the Docker Desktop installer.
    - Follow the installation instructions on the screen.
    - Once the installation is complete, start Docker Desktop from the Start menu.

3. **Configuration:**
    - Docker Desktop will launch and complete the initial configuration.
    - You may need to enable virtualization in your BIOS/UEFI settings if it's not already enabled.

4. **Verify Installation:**
    - Open a Command Prompt or PowerShell.
    - Run the following command to verify that Docker is installed correctly:
        ```bash
        docker --version
        ```
    - You should see the Docker version information displayed.
  
## Docker Commands

### Container Management
1. **Run a Container:**
    ```bash
    docker container run --publish {host_port}:{container_port} --detach --name {container_name} {image} {bash}
    ```
    - Example: `8080:80` forwards traffic from port 8080 on the host to port 80 in the container.
    - `--detach` runs the container in the background.
    - `--publish` maps host ports to container ports.

2. **Stop a Container:**
    ```bash
    docker container stop {name_or_ID}
    ```

3. **Start a Container:**
    ```bash
    docker container start {name_or_ID}
    ```

4. **List Running Containers:**
    ```bash
    docker container ls
    ```

5. **List All Containers:**
    ```bash
    docker container ls -a
    ```

6. **Show Container Processes:**
    ```bash
    docker container top {name_or_ID}
    ```

7. **Inspect a Container:**
    ```bash
    docker container inspect {name_or_ID}
    ```

8. **View Container Logs:**
    ```bash
    docker container logs {name_or_ID}
    ```

9. **Show Live CPU Usage:**
    ```bash
    docker container stats
    ```

### Interactive Mode
10. **Run a Container in Interactive Mode:**
    ```bash
    docker container run -it --name {container_name} {image} /bin/bash
    ```
    - `-it` flags for interactive terminal (tty).

11. **Start an Interactive Container:**
    ```bash
    docker start -ai {container_name}
    ```
    - `-a` for attach.
    - `-i` for interactive.

### Image Management
12. **List Images:**
    ```bash
    docker image ls
    ```

13. **Remove an Image:**
    ```bash
    docker image rm {image_name}
    ```
    - Or: `docker rmi {image_name}`
    - Use `-f` to force delete.

14. **Pull an Image:**
    ```bash
    docker pull {image_name}
    ```
    - Example: `alpine` is a small Linux distro (4MB).
    - Note: Alpine does not include bash by default, use `sh` instead.

### Network Management
15. **Inspect Container IP:**
    ```bash
    docker container inspect --format '{{.NetworkSettings.IPAddress}}' {name_or_ID}
    ```

16. **Verify Port Mapping:**
    ```bash
    docker container port {name_or_ID}
    ```

17. **List Networks:**
    ```bash
    docker network ls
    ```
    - Example: `bridge` is the default Docker virtual network.

18. **Create a Network:**
    ```bash
    docker network create {network_name}
    ```

19. **Run a Container in a Specific Network:**
    ```bash
    docker container run -d --name {container_name} {image} --network {network_name}
    ```

20. **Connect a Container to a Network:**
    ```bash
    docker network connect {network_name} {container_name}
    ```

21. **Ping Between Containers:**
    ```bash
    docker container exec -it {container_1} ping {container_2}
    ```

### Building Custom Docker Images
22. **Build an Image:**
    ```bash
    docker build -t {image_name} -f {Dockerfile} .
    ```
    - `-t` tags the image.
    - `-f` specifies the Dockerfile.
    - `.` indicates the current directory contains the files needed for the build.

23. **Run a Custom Image:**
    ```bash
    docker container run {image_name}
    ```

---

Author: **Purva Patel**
