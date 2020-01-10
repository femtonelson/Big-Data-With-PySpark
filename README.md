# Setup PySpark with Docker on Ubuntu AWS EC2 instance


# Introduction
Apache Spark™ is a open-source unified analytics engine for large-scale data processing. It achieves high performance for both batch and streaming data, 
using a state-of-the-art DAG scheduler, a query optimizer, and a physical execution engine. It powers a stack of libraries among which is Spark SQL.
It can be used interactively from Scala, R, SQL and Python shells. 
The PySPark API enables the interaction between the Python shell and the Spark SQL component using SQL and Dataframes.

Docker is a program that performs operating-system-level virtualization, also known as ‘containerization’. 
Docker creates a layer on top of a machine’s OS called a Docker container. Docker containers can be preconfigured with scripts to install specific software 
and provide customized functionality. Dockerhub is a website that contains various preconfigured docker containers that can be quickly run on your computer. 
One of these is the jupyter/pysparknotebook.

In this activity, we will :
- Download and install the Docker engine on Ubuntu server (AWS EC2 instance).
- Run a suitable pre-configured docker container on the server, to provide a functional PySpark environment in local mode on a single node


# Install Docker and pre-configured Docker container with Python, PySpark, Jupyter  Notebook

- EC2 Instance running with Ubuntu 18.04, update packages and check Ubuntu version
```
$sudo apt-get update
$sudo apt-get upgrade -y
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```
- Download and install the suitable Docker Engine Community version package for the OS  : https://docs.docker.com/install/linux/docker-ce/ubuntu/
```
$sudo wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce_18.03.1~ce~3-0~ubuntu_amd64.deb
$sudo apt install -y libltdl-dev
$sudo dpkg -i docker-ce_18.03.1~ce~3-0~ubuntu_amd64.deb
```
- Check the installation status, Successful ! Check Docker version.
```
$sudo docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.
$docker version
Client:
 Version:           18.06.0-ce
 API version:       1.38
 Go version:        go1.10.3
 Git commit:        0ffa825
 Built:             Wed Jul 18 19:09:54 2018
 OS/Arch:           linux/amd64
 Experimental:      false
```
- Pull the latest version of pre-configured Docker container, with Python 3.x environment, pre-installed versions of pyspark, pandas, matplotlib, scipy, seaborn, and scikit-learn, 
  Apache Spark and Jupyter Notebook from Docker hub : https://hub.docker.com/r/jupyter/pyspark-notebook
```
$sudo docker pull jupyter/pyspark-notebook:latest  
```

- Run the Docker container with name "pyspark" and make it's port 8888 accessible for Jupyter Notebook, add "&" to keep the Notebook server running permanently in background
```
$sudo docker run -p 8888:8888 --name pyspark jupyter/pyspark-notebook & 

To access the notebook, open this file in a browser:
copy and paste one of these URLs:
	http://0ace2fcc811e:8888/?token=b90051e75f2f56d065da4e9c3258a858530ab41afa9609d7
 or http://127.0.0.1:8888/?token=b90051e75f2f56d065da4e9c3258a858530ab41afa9609d7
```
- Access Jupyter Notebook in a web browser with the Public IP address of the EC2 instance/Server : http://IP.ADDRESS.OF.EC2INSTANCE:8888/?token=ec9221e2e3793361cb56b7ed77b06c4d6a4e3596085ae150

- Start or stop the Docker container "pyspark" as below
``` 
$sudo docker start pyspark 
$sudo docker stop pyspark 
```

Useful links :
- https://hub.docker.com/r/jupyter/pyspark-notebook
- https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html

