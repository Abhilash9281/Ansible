# Ansible
Files to manage automation and get the things done..

As per the requirements, things need to be done:
•	All the servers or the workstations and nodes should be up and running in AWS ec2 instances.
•	All those nodes should be ssh to the Ansible workstation where we will be managing all the nodes as required for the project.
The projects requirements:
DEVELOPER and TESTING NODE:
•	For the developing code for docker we used UBUNTU system where we require things like DOCKER, JAVA, MAVEN, HTTP.
•	Make sure that all things are up and running according to the requirements by Running basic command of each tool.
•	For Testing we are using REDHAT/CENTOS system where we will pull the code from Git-hub and images from docker hub.
•	In the testing node again need to install the above-mentioned tools.
•	SSH into the test node and
-	Make sure that the Dockerfile is running without any errors, if any create branch and fix the bug and push the code to develop branch in the git-hub.
-	Make sure that everything thing is ordered and tag in github.
-	After fixing every bug merege the file from develop to main master branch and create a release. 
KUBERNETES Workstation:
•	The kubernetes require the below dependencies to be installed and running.
-	NTP.
-	ETCD.
-	Make sure that python is installed and up-to date.

(ALL the files about to mention, which are used to manage are in the GitHub)
url: https://github.com/Abhilash9281/Ansible
Things done to achieve the above-mentioned requirements:
•	All the nodes are ssh and added to host file, 
•	I Make sure that all the nodes are communicating with ansible by ssh to each node and pinging.
•	Gone through the Ansible Config file and Created directory and a local Git repo to develop and test the playbooks.
Developer Node:
-	Created and tested yaml files using different modules as mentioned below:
•	Created a yaml file dock.yaml containing Command and action module to install docker, java, maven, and http.
•	Also created docker.yaml  using when where we can mention when to run and install the mentioned module and package based on the Server type (Debian or Redhat)
Testing Node:
-	Since this is a Redhat distribution, instead of writing the whole new code, we used the same docker.yaml which can run and install based on distribution by gathering facts (ansible <host> -m setup -a ‘filter=ansible_os_family’).
-	SSH-ed into node and pull the source code from git-hub and created a branch for testing.
-	Run the docker commands and tested the Dockerfile and merged to develop branch for further development.

 Kubernetes node:
•	For the Kubernetes node there are some basic dependencies to be installed to work properly
•	Here to approach new format I used include modules, I wrote individual yaml files to run the different modules and commands and even to include some files and variables.
•	For this I created and main yaml file include.yaml  and other file namely  commands.yaml, packages.yaml, handlers.yaml, copy.yaml.
-	Commands.yaml contains the command modules to run the basic commands to check the packages installed correctly or not.
-	Packages.yaml contains the packages module based on the Debian or Redhat distribution (yum.yaml & apt.yaml)
-	Handlers.yaml contains service module to check the service is enabled and started.
-	Copy.yaml contains copy module to transfer some file to the mode from the workstation.
All these files are included according in include.yaml to get the required state of the node.
