# Setup PySpark with Docker on Ubuntu AWS EC2 instance and Run ML Predictions

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
- Import and Clean a Dataset
- Ongoing
- Ongoing


# Install Docker and pre-configured Docker container with Python, PySpark, Jupyter  Notebook

- EC2 Instance running with Ubuntu 18.04, update packages and check Ubuntu version
```
$sudo apt-get update
$sudo apt-get install
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```
- Download and install the suitable Docker Engine Community version package for the OS  : https://docs.docker.com/install/linux/docker-ce/ubuntu/
```
$sudo apt-get remove docker docker-engine docker.io containerd runc
$sudo wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce_18.03.1~ce~3-0~ubuntu_amd64.deb
sudo dpkg -i docker-ce_18.06.0~ce~3-0~ubuntu_amd64.deb
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
- Pull the latest version of pre-configured Docker container, with Python 2.7.x and 3.x environments, pre-installed versions of pyspark, pandas, matplotlib, scipy, seaborn, and scikit-learn, 
  Apache Spark and Jupyter Notebook from Docker hub : https://hub.docker.com/r/jupyter/pyspark-notebook
```
$sudo docker pull jupyter/pyspark-notebook:latest  
```

- Run the Docker container with name "pyspark" and make it's port 8888 accessible for Jupyter Notebook, add "&" to keep the Notebook server running permanently in background
```
$sudo docker run -p 8888:8888 --name pyspark jupyter/pyspark-notebook --allow-root & 
ubuntu@ip-10-0-4-7:~$ Executing the command: jupyter notebook
[I 20:57:08.610 NotebookApp] Writing notebook server cookie secret to /home/jovyan/.local/share/jupyter/runtime/notebook_cookie_secret
[I 20:57:10.057 NotebookApp] JupyterLab extension loaded from /opt/conda/lib/python3.7/site-packages/jupyterlab
[I 20:57:10.057 NotebookApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[I 20:57:11.238 NotebookApp] Serving notebooks from local directory: /home/jovyan
[I 20:57:11.239 NotebookApp] The Jupyter Notebook is running at:
[I 20:57:11.239 NotebookApp] http://1b544d1b02b6:8888/?token=1a64449f0431befeb5c20e715e19d51bac02404f60843b84
[I 20:57:11.239 NotebookApp]  or http://127.0.0.1:8888/?token=1a64449f0431befeb5c20e715e19d51bac02404f60843b84
```
- Access Jupyter Notebook in a web browser with the Public IP address of the EC2 instance/Server : http://IP.ADDRESS.OF.EC2INSTANCE:8888/?token=ec9221e2e3793361cb56b7ed77b06c4d6a4e3596085ae150

- Start or stop the Docker container "pyspark" as below
``` 
$sudo docker start pyspark 
$sudo docker stop pyspark 
```

# PySpark Basics
Ongoing

# Importing the Dataset
Ongoing

Useful links :
https://hub.docker.com/r/jupyter/pyspark-notebook
https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html

