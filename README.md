# DesignedandDeployedSecureCloudNetworkWithElkstack- ## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
![This is my Elk Network Diaram](https://github.com/EmilyATheodorakos/DesignedandDeployedSecureCloudNetworkWithElkstack-/blob/main/Images/Elk%20Network%20Diagram.drawio.png)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml and config file may be used to install only certain pieces of it, such as Filebeat.
![This is my Elk playbook](https://github.com/EmilyATheodorakos/DesignedandDeployedSecureCloudNetworkWithElkstack-/blob/main/Ansible/install-elk.yml)
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect against distributed denial-of-service (DDoS) attacks by acting as a reverse proxy and distributing traffic across several severs. Load balancers also help to ensure availability by evenly distributing network traffic the prevent overload. The advantage to a jump box is that it gives a control point to users that can be secured and monitored. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _TODO: What does Filebeat watch for?_ Filebeat watches for log files or locations and log events. 
- _TODO: What does Metricbeat record?_ Metricbeat records metrics and statistics from the system and services on the server. 
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name     | Function | IP Address             | Operating System |
|----------|----------|------------            |------------------|
| Jump Box | Gateway  | 10.0.0.4/20.115.23.169 | Linux            |
| Web1     | Webserver| 10.0.0.9               | Linux            |
| Web2     | Webserver| 10.0.0.8               | Linux            |
| Elk-VM   | Webserver| 10.1.0.4               | Linux            |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Jump-Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 24.128.60.216
Machines within the network can only be accessed by Jump-Box.
- _TODO: 10.0.0.4/20.115.23.169 
Which machine did you allow to access your ELK VM? 
I allowed access through my personal device. 
What was its IP address? 
24.128.60.216
A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses          |
|----------|---------------------|-------------------------------|
| Jump Box | Yes                 | Workstation IP on SSH port 22 |
| Web1     | No                  | 10.0.0.4                      |
| Web2     | No                  | 10.0.0.4                      | 
| Elk-VM   | No                  | Workstation IP on HTTP port 80|
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_The advantage of automating configuration with Ansible is that you can assign multiple commands/codes into to a number of servers using a playbook. 
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
•	Indicate machines and remote user
•	Increase System Memory
•	Install selected services: docker.io, python3-pip,docker module 
•	Download and launch a docker web container on ports 5601:5601,
9200:9200, 5044:5044
•	Enable service docker on boot
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![This is the web1 docker output](https://github.com/EmilyATheodorakos/DesignedandDeployedSecureCloudNetworkWithElkstack-/blob/main/Images/web1_docker_ps_output.png)
![This is the web2 docker output](https://github.com/EmilyATheodorakos/DesignedandDeployedSecureCloudNetworkWithElkstack-/blob/main/Images/web2_docker_ps_output.png)
![This is the Elk docker output](https://github.com/EmilyATheodorakos/DesignedandDeployedSecureCloudNetworkWithElkstack-/blob/main/Images/elk_docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
Web1- 10.0.0.9
Web2- 10.0.0.8

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed:
1)Filebeat
2)Metricbeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat monitors the log files or locations that have been selected and collects long events. This helps to keep things simple by forwarding and centralizing logs and files.  

Metricbeat is a lightweight shipper that collects metrics from your system and services. This is a lightweight way to send statistics about your system and services.  
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the ansible configuration file to run playbooks.
- Update the ansible host file to include ip addresses. 
- Run the playbook, and navigate to Jump-Box to check that the installation worked as expected.
_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? install-elk.yml 
- Where do you copy it? /etc/ansible/install-elk.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? install-elk.yml 
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?_You need to specify in the install-elk.yml which servers are installing elk. In addition you will need to edit the /etc/ansible/host file to add the elk server IP address. 
- _Which URL do you navigate to in order to check that the ELK server is running? 52.173.39.1:5601/app/kibana This will take you to the kabana site. 

