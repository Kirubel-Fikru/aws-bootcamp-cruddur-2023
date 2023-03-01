# Week 1 — App Containerization

## Business Scenario

Your company has received the code repositories for the demo application from the contracted web-development firm. The company wants you to investigate the codebases, and ensure you can get them running.

The fractional CTO has suggested we first begin containerizing the applications for both developer and production use, and their reasons stayed why:

● To avoid lack of documentation of application and OS configuration
● To ensure the effort of application and OS configuration is factored in before investing lots of feature development
● If we decide to hire our technical team members we can quickly replicate these environments in any preferred choice.

The fractional CTO has asked that everything be developed in Gitpod, (a Cloud Developer Environment). This will allow the CTO at a press of a button launch the developer environment in a clean state to help with any tricky or emergency implementations, and ensure developer accountability.

Gitpod was since it supports multiple Version Control Services (VCS).. The company has invested considerable effort already in Atlassian JIRA working with the web-dev firm, and repo’s highly likely might be moved to Atlassian BitBucket to take advantage of better integrations within the Atlassian’s ecosystem.

##  Dockerfile

```
FROM python:3.10-slim-buster
#This line sets the base image for the Docker image we're building to python:3.10-slim-buster.
#This is a slimmed-down version of the official Python 3.10 image, based on the Debian "Buster" distribution.
WORKDIR /backend-flask
# This line sets the working directory for the Docker container to /backend-flask.
COPY requirements.txt requirements.txt
# This line copies the requirements.txt file from the host machine to the working directory in the Docker container.
RUN pip3 install -r requirements.txt
# This line installs the Python packages listed in requirements.txt using pip3.

COPY . .
# This line copies all the files and directories from the host machine to the working directory in the Docker container.
ENV FLASK_ENV=development
#This line sets the FLASK_ENV environment variable to development.
EXPOSE ${PORT}
# Exposes the port specified by the ${PORT} environment variable. 
# Note that this line does not actually publish the port to the host machine; that is done when the container is run.
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
# This line specifies the default command to run when the Docker container is started. 
# In this case, it runs the Flask application using python3 and the flask run command, with the host set to 0.0.0.0 and the port set to 4567.
```

## Build Container
`docker build -t backend-flask ./backend-flask`

* **docker build**: This is the Docker command that we're running.
* **-t backend-flask**: This option sets the name of the Docker image that we're building to backend-flask.
* .**/backend-flask**: This specifies the build context, which is the directory that contains the Dockerfile and any other files needed to build the Docker image. In this case, the build context is ./backend-flask, which means that Docker will look for the Dockerfile in the backend-flask directory.


![Docker Build](../screenshots/docker%20build.png)

## Run Container
`docker run --rm -p 4567:4567 -it backend-flask`

* **docker run**: This is the Docker command that we're running. 
* **--rm**: This option tells Docker to automatically remove the container when it stops running. This can help prevent clutter from accumulating on your system.
* **-p 4567:4567**: This option maps the container's port 4567 to the host machine's port 4567. This allows you to access the container's web server from your host machine's web browser.
* **-it**: This option tells Docker to run the container in interactive mode and allocate a pseudo-TTY. This allows you to interact with the container's shell and see its output in your terminal.
* **backend-flask**: This is the name of the Docker image that you want to run.
