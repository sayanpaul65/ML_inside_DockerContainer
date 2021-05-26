# ML_inside_DockerContainer
Task Description 📄

+> Pull the Docker container image of CentOS image from DockerHub and create a new container.

+> Install the Python software on the top of the docker container

+> In Container copy the python file from host to the docker container.

+> Install required libraries required to load ML model

+> Run the python code for prediction.


What is docker ?
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.

No alt text provided for this image
What is Machine Learning ?
Machine learning is a branch of artificial intelligence that includes methods, or algorithms, for automatically creating models from data. Unlike a system that performs a task by following explicit rules, a machine learning system learns from experience. Whereas a rule-based system will perform a task the same way every time (for better or worse), the performance of a machine learning system can be improved through training, by exposing the algorithm to more data.



Now move on to the main task ...

Step 0: Install Docker on your base RHEL 8 (If not already installed).
How we can install docker in the redhat 8 VM

Configure yum for Docker
-Create a file "/etc/yum.repos.d/docker.repo"

Example:-gedit /etc/yum.repos.d/docker.repo

''' [docker]

baseurl=https://download.docker.com/linux/centos/7/x86_64/stable/

gpgcheck=0 '''

After this verify by "yum repolist". You see some more software

Install Docker and start service
-Run three command given below:-

" yum install docker-ce --nobest"
"systemctl start docker"
" systemctl enable dockerNow "
Successfully docker is installed and verify that by "docker info".



Step 1 : Pull the OS image you want to use from Docker Hub.
[In my case I am using Centos]

docker pull centos:latest
No alt text provided for this image
to pull the image



Step 2: Create a container with the downloaded image.
docker run -it --name=container_name centos:latest 

No alt text provided for this image
To start a docker container with the name "LRmodel" and image used is "centos" and the version is "latest".

We can also notice the change in the shell prompt which indicates that we are now inside the container and not in our base OS.

Step 3: Download Python software inside Container.
yum install python

No alt text provided for this image
No alt text provided for this image
Step 4: Install required libraries to load Machine Learning model.
pip3 install <library name>

No alt text provided for this image
No alt text provided for this image


Step 5: Copy the pre-created model from BaseOS to the docker container.
docker cp <src> <container_name>:<dest>

No alt text provided for this image
Here the "ML_LR" directory containing the model is copied to the container "LRmodel".



Step 5: Check whether it is copied successfully or not.
No alt text provided for this image
Let us a have a glimpse of the dataset which is used to train the model.

No alt text provided for this image




Step 5: Create a python code to predict from the experience of the pre-created model.
No alt text provided for this image
No alt text provided for this image
In the python code we have created a model which is loaded from the pre-created model. Inside it we have given a static input of "1.9" which is the year of experience and in return it gives me the output of "43747.12860943" Rupees as the predicted salary.

[I made the code static, it could be made dynamic , that it would ask for input from the user (the year of experience) and in return would predict the Salary in Rupees.]



....................................................................................................................................................

Thank you for your Valuable Time.
