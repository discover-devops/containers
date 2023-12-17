Certainly! Here's a simplified version of your Docker image building guide in GitHub Markdown format:

```markdown
# How to Build Docker Image

## 1. Dockerfile Explained
The basic building block of a Docker image is a **Dockerfile**. It is a simple text file with instructions and arguments. Docker can build images automatically by reading the instructions given in a Dockerfile.

### Dockerfile Instructions
| Instruction | Explanation |
| --- | --- |
| FROM | To specify the base image from a container registry (Docker Hub, GCR, Quay, ECR, etc.) |
| RUN | Executes commands during the image build process |
| ENV | Sets environment variables inside the image |
| COPY | Copies local files and directories to the image |
| EXPOSE | Specifies the port to be exposed for the Docker container |
| ADD | A more feature-rich version of COPY |
| WORKDIR | Sets the current working directory |
| VOLUME | Used to create or mount volumes |
| USER | Sets the user name and UID when running the container |
| LABEL | Specifies metadata information of Docker image |
| ARG | Sets build-time variables |
| SHELL | Sets shell options and default shell for instructions |
| CMD | Executes a command in a running container |
| ENTRYPOINT | Specifies commands that execute when the Docker container starts |

## 2. Build Docker Image Using Dockerfile

### 2.1. Step 1: Create the Required Files and Folders
```bash
mkdir nginx-image && cd nginx-image
mkdir files
touch .dockerignore
```

### 2.2. Step 2: Create a Sample HTML File and Config File
```bash
cd files
vi index.html
# Copy HTML content

vi default
# Copy config file content
```

### 2.3. Step 3: Choose a Base Image
Choose a base image using the `FROM` command in the Dockerfile. Example: `FROM ubuntu:18.04`

### 2.4. Step 4: Create the Dockerfile
Create a Dockerfile in the `nginx-image` folder. Example content:
```dockerfile
FROM ubuntu:18.04
LABEL maintainer="contact@devopscube.com"
RUN apt-get -y update && apt-get -y install nginx
COPY files/default /etc/nginx/sites-available/default
COPY files/index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
```

### 2.5. Step 5: Build Your First Docker Image
```bash
docker build -t nginx:1.0 .
```

### 2.6. Step 6: Test the Docker Image
```bash
docker run -d -p 9090:80 --name webserver nginx:1.0
```

## 3. Push Docker Image To Docker Hub
1. Create a Docker Hub account
2. Log in from the terminal: `docker login`
3. Tag the image with Docker Hub username: `docker tag nginx:1.0 <username>/nginx:1.0`
4. Push the image to Docker Hub: `docker push <username>/nginx:1.0`

## 4. Using Heredoc With Dockerfile
...

## 5. Dockerfile Best Practices
...

## 6. Possible Docker Build Issues
...

## 7. Docker Image Registries
...

## 8. Docker Image vs. Containers
...

## 9. Docker Image Build FAQs
...

## 10. What's Next
...

## 11. Conclusion
...
```

Feel free to adjust the formatting and content to fit your needs.
