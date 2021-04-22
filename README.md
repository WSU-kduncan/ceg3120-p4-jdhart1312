# Project 4 using DockerHub

## Project Overview
The idea behind this project is to create a public repo on DockerHub and access it by using 
a yml file to use the secret username and secret password on the account. Using docker is the 
main idea behind this project. 

## Run Project Locally
### How to install docker
To install docker on WSL2, there are a few commands that need to be ran first. The first command 
is `sudo apt update` to update all of the existing packages. Next, there are a few packages that 
need to be installed before docker can be. This command is as follow: `sudo apt install apt-transport-https ca-certificates curl software-properties-common`. To continue on to downloading docker, 
use the following command to download: `sudo apt install docker.io`. To continue on, use the following  command to add the docker repository: 
`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`. 
For the final command, use `sudo apt update` again to get the final update for the docker packages. 

### How to build a docker container
To start off with building a docker container, create two files. The first file should be a python, 
for example, `main.py`. Put the code in here that you would prefer.

To continue on, create a docker file called `DockerFile`. We must have 3 lines of code to be able 
to build a docker container. The first line needs to be `FROM python:latest`. This used the key 
word 'FROM' to start by importing the base image. Next we want to import the python image, so the 
word 'python' is put after 'FROM', and then use the word 'latest' for the version. 

The next line needs to be `COPY main.py /`. The keyword 'COPY' is used to import it into our image
to launch our python code. The first parameter 'main.py' is the name of the file on the host, or 
whatever file name was put in by the user. Next, as the second parameter, '/' is where the 'main.py' 
will be put on the image.

The third and final line of code needed, is `CMD [ "python", "./main.py" ]`. This defines the command to launch when the docker image is going to be ran by using 'CMD'. The command will be executed by running 'python ./main.py'.

Create the docker image by running the command `docker build -t testpython`.

### How to run the docker container
To run the docker image, it is very simple. After following the previous steps, all that needs to
be done is run the command `docker run testpython`. This runs the docker container. 

### How to view the project
