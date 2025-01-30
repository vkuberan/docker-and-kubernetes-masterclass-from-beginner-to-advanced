# Basic NGINX Setup
- **Project Overview**
    - The project focuses on customizing an **NGINX** server using Docker.
    - It serves as a foundational project, suitable for both beginners and those familiar with Docker.
- **Project Goals**
    - Run an **NGINX** container using the specific image tag 1.27.0.
    - Access the interactive shell inside the running container.
    - Install a text editor (**Vim** or **Vi**) inside the container.
    - Modify the `index.html` file to deliver custom content.
- **Learning Outcomes**
    - Helps in understanding key Docker concepts like container interaction and file modification.
    - Prepares users for more advanced projects in future lessons.
- **Encouragement for Practice**
    - Users can pause the video and try the steps on their own.
    - The goal is to ensure the **NGINX** server delivers the customized content.
  
![basic-nginx-setup.png](../images/basic-nginx-setup.png)

This project focuses on customizing an NGINX server using Docker, making it ideal for both beginners and those already familiar with Docker. The goal is to run an NGINX container with the **1.27.0** image tag, access its interactive shell, install **Vim** or **Vi**, and modify the `index.html` file to serve custom content. This exercise reinforces key Docker concepts, such as container interaction and file modification, while setting the stage for more advanced projects. Users are encouraged to try these steps independently to ensure the server delivers customized content.

# Running NGINX Container

- **Using a Specific NGINX Version**
  - Instead of using the latest tag, it is recommended to use a specific version (`1.27.0`) for stability. 
  - The latest tag changes as new versions are released, which can cause incompatibility issues.
- **Pulling the NGINX Image**
  - Use `docker pull nginx:1.27.0` to download the exact version. 
  - Verify the download using docker images.
- **Running the NGINX Container**
  - Execute docker run with key options:
    - `-d` (detached mode) to run in the background. 
    - `-p 80:80` to map local port 80 to container port 80. 
    - `--name web_server` to assign a custom name. 
  - If no version is specified, Docker assumes the latest, which may lead to inconsistencies. 
- **Verifying the Running Container**
  - Use `docker ps` to confirm the container is active. 
  - Test accessibility with `curl localhost`, which should return a response from the running **NGINX** server. 
- **Next Steps**
  - The container is running successfully, but more configurations will be explored in the upcoming lessons.

To ensure stability, it is best to use a specific version of the `NGINX` image (`1.27.0`) instead of relying on the latest tag, which can change over time and cause incompatibilities. The image can be pulled using `docker pull nginx:1.27.0` and verified with docker images. To run the container, use `docker run -d -p 80:80 --name web_server nginx:1.27.0`, ensuring it runs in detached mode with proper port mapping and a custom name. Without specifying a version, Docker defaults to the latest, potentially leading to unexpected behavior. Once the container is running, `docker ps` confirms its status, and `curl localhost` verifies the `NGINX` response. With the basic setup complete, more configurations will follow in the next lessons.

# Customizing Content Inside the NGINX Container

- **Starting and Accessing the NGINX Container**
  - Verify if the container is running using `docker ps`. 
  - If it is stopped, restart it using `docker start web_server`. 
  - Use `docker exec -it web_server sh` to open an interactive shell inside the container.
- **Installing Vim and Accessing the HTML File**
  - By default, **_Vim_** is not installed in the NGINX container. 
  - Install it using apt-get update followed by `apt-get install vim`. 
  - Locate the `index.html` file at `/usr/share/nginx/html/index.html`.
- Editing the HTML File with Vim
  - Open the file in **_Vim_** using vim `/usr/share/nginx/html/index.html`. 
  - Use **_Vim_** commands to edit the content:
    - `9dd` to delete nine lines. 
    - `i` to enter insert mode, modify the message, and then save with `:wq`.
- **Verifying the Changes** 
  - Run `cat /usr/share/nginx/html/index.html` to check if the content was updated.
  - Use `curl localhost` to confirm the changes.
  - If the browser still shows the old content, clear cache or rely on `curl`.
- **Next Steps**
  - The project demonstrates modifying container files and installing packages.
  - Further discussions on limitations and improvements will follow in the next lesson.

To ensure the **NGINX** container is running, check with `docker ps` and restart it if necessary. Use `docker exec -it web_server sh` to enter the container. Since `Vim` is not pre-installed, update the package list with `apt-get update` and install `Vim` using `apt-get install vim`. The `index.html` file, located at `/usr/share/nginx/html/index.html`, can be modified by opening it in `Vim` (`vim /usr/share/nginx/html/index.html`). Use commands like 9dd to delete multiple lines and `i` to enter insert mode and edit the text. Save changes with `:wq` and verify using `cat` or `curl localhost`. If the browser still displays the old content, clear the cache or rely on curl. This project highlights how to modify container files and install packages, with further discussions on improvements in the next lesson.
         