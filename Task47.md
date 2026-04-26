### Task:
A python app needed to be Dockerized, and then it needs to be deployed on App Server 2. We have already copied a requirements.txt file (having the app dependencies) under /python_app/src/ directory on App Server 2. Further complete this task as per details mentioned below:


    Create a Dockerfile under /python_app directory:
        Use any python image as the base image.
        Install the dependencies using requirements.txt file.
        Expose the port 3002.
        Run the server.py script using CMD.

    Build an image named nautilus/python-app using this Dockerfile.

    Once image is built, create a container named pythonapp_nautilus:
        Map port 3002 of the container to the host port 8092.

    Once deployed, you can test the app using curl command on App Server 2.

#### Solution:
SSH into the server and run the commands
```
     vi Dockerfile
     docker build -t nautilus/python-app .
     docker images
     docker create --name pythonapp_nautilus -p 8092:3002 nautilus/python-app:latest
     docker start 4faf8fe675fe1d4fb89e5b7bce48dad380c0223ca31164dfdaafa631f723b0e7
     docker ps
     curl http://localhost:8092/
```

add this content into the docker file
```
# Use any Python base image, e.g., python:3.9-slim
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy requirements.txt first to leverage Docker caching
COPY src/requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your application files (including server.py)
COPY . .

# Expose port 3002
EXPOSE 3002

# Run the server.py script
CMD ["python", "src/server.py"]
```
