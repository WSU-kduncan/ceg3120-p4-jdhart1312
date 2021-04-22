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
To be able to find the IP Address, use `docker inspect -f \ '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' \`. This will print the IP Address for the docker container, then it will be able to be ran on local host. 

## Configure AWS CLI
### AWS IAM user with admin credentials
To be able to run AWS CLI and configure, it is best to run the terminal with the admin privileges to make sure everything runs perfectly.

### How I installed
The way I installed AWS CLI was I went to their website, `https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html`. Download the appropriate AWS CLI that is needed for the computer, and then follow the instructions to be able to download everything. 

### How to configure
The way to configure AWS CLI is to run 'Windows Powershell' as an administrator. After running powershell, start with running the command `aws` to be able to determine that AWS CLI is installed. After checking AWS, run `aws configure` and put in the necessary information needed to continue. 

## Create DockHub Public Repo
To create a DockerHub public repository, create a free account on dockerhub. After creating an account, click on `repositories` in the top right corner, then click `create repository`. Add the name and description to your liking, and make the visibility public or private, also to the your liking. After that, click create, and the repository is completed. 

## Configure GitHub Secrets
The credentials needed for github secrets are the dockerhub username and password. To set these secrets, it is rather simple. On github, go to the repo that you would like to be able to add the secrets to. Click on the `settings` button on the nav bar. Then click the `secrets` button on the side bar. After clicking the secrets button, click `New Repository Secret`. File in the secret name and secret value to the liking of the user. 

## Configure GitHub Workflow
To get started on the github workflow, follow the following link `https://docs.github.com/en/actions/guides/publishing-docker-images#publishing-images-to-docker-hub`. Make a file named `namehere.yml`, then copy and paste the example into the yml file. Change the variable `repository: my-docker-hub-namespace/my-docker-hub-repository` to the repository needed by the user.
