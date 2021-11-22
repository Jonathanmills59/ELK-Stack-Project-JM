# ELK-Stack-Project-JM
Created Virtual network and Homework
## Automated ELK Stack Deployment

 
The files in this repository were used to configure the network depicted below.


![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.


/etc/ansible/install-elk2.yml




This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build




### Description of the Topology


The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.


Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
 What aspect of security do load balancers protect? What is the advantage of a jump box?


Load balancers protect the environment from a DDoS attack by slowing/shifting traffic through the network. Load balancers contribute to balancing out the traffic to prevent the network from being overworked. 
The advantage to using a jump box is that it can be secured to offer safe access as well as an origin point to get into the system. It can also be used to put in place rules and other procedures for monitoring the network as well as limiting access to those permitted by the protocols.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
What does Filebeat watch for?
Filebeat watches for any changes made to information in the system as well as collecting all logs events.


What does Metricbeat record?
Metricbeat records all statistic and metric data from the network and servers and outputs it to a location from which it can be accessed and monitored to view the information. 


The configuration details of each machine may be found below.




| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4       | Linux     |
| Web1        | Server     |  10.0.0.6      | Linux     |
| Web2        | Server     |  10.0.0.7      | Linux     |
| ELK-VM    | Server     |  10.1.0.4      | Linux     |


### Access Policies


The machines on the internal network are not exposed to the public Internet. 


Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Access to the jumpbox is only allowed from the home network IP address which changes upon startup and may have to be adjusted accordingly. 75.155.86.198 


Machines within the network can only be accessed by SSH.


Which machine did you allow to access your ELK VM? What was its IP address?_
The Jump box is the only machine that is allowed to access the ELK-VM. The IP address for the jump box is 10.0.0.4
A summary of the access policies in place can be found in the table below.


| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No              |  75.155.86.198         |
| Web1        | No              |  10.0.0.4                   |
| Web2        | No              |  10.0.0.4                   |
| ELK-VM    | No              |  10.0.0.4                   |
### Elk Configuration


Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
The main advantage of automating configuration with Ansible is that it can be run to change multiple servers simultaneously as opposed to going in and making changes individually.


The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
* Install docker.io
* Install python3-pip
* Install Docker container module
* Use docker container module through specific ports
* Enable systemd module on docker boot


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
  



ELK-Stack-Project-JM/Ansible/cloudadmin@ELK-Stack-VM


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web1- 10.0.0.6
Web2- 10.0.0.7


We have installed the following Beats on these machines:
Specify which Beats you successfully installed
* Filebeat
* Metricbeat


These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
Filebeat collects and centralizes Log data whereas Metricbeat collects metrics and statistics and places them in a specified location. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 


SSH into the control node and follow the steps below:
- Copy the filebeat-config file to metricbeat-config.yml.
- Update the configuration file to include the proper IP addresses.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.


_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
The playbook is pentest.yml. You copy it into the /etc/ansible directory.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
You would update the ansible.cfg file to run the ansible playbook on a specific machine. In order to specify which machine to install the ELK server on versus which for filebeat you would update the hosts file which has the information for the server groups that would be used for running an install through the containers.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.ELK-VM.External.IP]:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
