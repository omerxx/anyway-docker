Anyway’s docker environment
===========================

Docker is an open source project to pack, ship and run any application as a lightweight container.

 ![docker png](docker.png)

The idea is to deploy a container (light weight environment) that has all our app dependencies installed and ready to go.
As a developer you can do one of both:

* Use the container do write your code (using vim/nano or any other GNU text editing tool - not recommended)
* Use a git repo cloned to your local machine and use the container as a remote server running the app

The container loads itself with the command given in the instructions, it has the DB on it, deployed and ready to work (at /anyway/local.db)
With every local code change, the container would restart itself and the changes would be immediately available in your web browser.
The current image is based on an Ubuntu linux with java. 

Read more on the docker [Github project] (https://github.com/docker/docker)


Instructions
-----------------------
* Please complete ANYWAY’s [“getting the code” section] (https://github.com/hasadna/anyway#getting-the-code) before starting

**1.** Install docker prerequisites - [Docker toolbox] (https://www.docker.com/docker-toolbox)

**2.** Run "Docker terminal”

**3.** Go to the **anyway** directory and run:

    docker run -it --restart="always" -p 80:5000 -v $PWD:/opt/anyway -w /opt/anyway omerxx/anyway-docker /bin/bash -c 'export DATABASE_URL=sqlite:////anyway/local.db && python main.py --open'
**4.** Access the app at the virtual machine’s IP (usually `192.168.99.100`); <br> 
To retrieve a docker machine address: `docker-machine ip default`
(no need for port specification, simply an IP; e.g `192.168.99.100`)


More
-----------------------
To install requirements again, redeploy DB or any requirement involving the dependencies installation, 
simply rebuild the image; get it from [here] (https://github.com/omerxx/anyway-docker/blob/master/Dockerfile), 
then go to its local path and `docker build -t omerxx/anyway .`

## Docker commands

Set your VM with the current running shell session: 

    eval "$(docker-machine env default)"


List your local docker images: 

    docker images
    
List your running containers: 
    
    docker ps
    
List all containers ever: 

    docker ps -a

Stop a running container (id is listed in `docker ps`): 

    docker top <container-id> 

Deleting an image(from `docker images`): 

    docker rmi <image-id>
 


Questions and ideas
-----------------
Talk to Omer by [mail] (omerxx@gmail.com) or by Slack (omerxx)

