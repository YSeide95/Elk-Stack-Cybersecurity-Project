# Elk-Stack-Cybersecurity-Project
![Elk_Stack_Diagram1](https://user-images.githubusercontent.com/105944451/169668932-0a70486b-21cb-4e4e-b0c3-e837fea192f7.jpg)
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram]![Elk_Stack_Diagram1](https://user-images.githubusercontent.com/105944451/169668932-0a70486b-21cb-4e4e-b0c3-e837fea192f7.jpg)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Functional and available, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?
•	Load Balancers protect against denial of service attacks (DDoS) because the load balancer analyzes the traffic coming in and determines what server to send the traffic to
•	You can increase the security of your entire network with a jumpbox.A jump bix is a system set up with multi factor authentication usually placed in a network DMZ with very restricted access to the corporate network and no returning Internet access for any protocol.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system system logs.
- _TODO: What does Filebeat watch for? 
•	Filebeat monitors the log files or locations that one specifies, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- _TODO: What does Metricbeat record?_
•	Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache
•	

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
### Access Policies

| Name       | Function | IP Address            | Operating System |
|------------|----------|-----------------------|------------------|
| Jump Box   | Gateway  | 10.0.0.4/13.67.177.59 | Linux            |
| Web 1      | Server   | 10.0.0.7              | Linux            |
| Web 2      | Server   | 10.0.0.8              | Linux            |
| Elk server | Server   | 10.2.0.4/20.125.24.19 | Linux            |


The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:Personal IP Address

Machines within the network can only be accessed by the Jump Box. Which machine did you allow to access your ELK VM? Jump Box Provisioner IP:10.0.0.4 via SSH port 22

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses                       |
|------------|---------------------|--------------------------------------------|
| Jump Box   |         Yes         | Personal IP (workstation)                  |
| Web 1      |          No         | 10.0.0.4 on SSH 22                         |
| Web 2      |          No         | 10.0.0.4 on SSH 22 
                                          
| Elk server |          No         | (work station IP) public IP using TCP 5601



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
•	Ansible allows you to easily deploy multiple tiers of applications through a YAML playbook.
•	No special coding skills are necessary to use Ansible Playbooks
•	System installations and updates can be streamlined


The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
•	Configure elk VM with Docker
•	Install docker.io
•	Install python3
•	Increase Virtual Memory
•	Published ports 5044,5601,9200

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_
•	Web 1: 10.0.0.7 
•	Web 2: 10.0.0.8
•	DVWA-VM3:



We have installed the following Beats on these machines:
: Specify which Beats you successfully installed_
These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

•	Filebeat- Collects the logs for each virtual machine. It collects traffic from specific countries, number of visitors, and errors such as 404.



•	Metricbeat- provides information on metric logs for the virtual machines. Information on CPU, Memory Usage, Network stats.




Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to ansible folder.
- Update the config file to include remote users and ports.Update the hosts file to include IP addresses of the Web Servers and Elk servers.
- Run the playbook, and navigate to Kibana (Elk VM public IP):5601 to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:_
- Which file is the playbook? Filebeat-playbook.yml & metricbeat-playbook.yml

Where do you copy it? To ansible

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Update the Filebeatconfig.yml and specify which machine to install by updating the Host file with the Private IP addresses and selecting which group to run in ansible. Same for metricbeatconfig.yml

- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.Elk-VM.External.IP]:5601/app/kibana.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._


*Bonus*
Elk VM Configuration
•	Copy the Elk Installation & VM Config
•	Run the playbook using: ansible-playbook /etc/ansible/install-elk.yml

Filebeat
•	Download Filebat playbook using curl
o	  curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml

•	Copy Filebeat-config.yml file to /etc/ansible/files
•	Update the filebeat-config.yml file by doing nano /etc/ansible/files/filebeat-config.yml to include ELK private IP 10.2.0.4 under hosts under the elastic search output section. Also add it to the host section in the setup.kibana.  





•	Then run playbook
•	$ ansible-playbook /etc/ansible/roles/filebeat-playbook.yml
Metricbeat

•	Download metricbeat playbook using curl command

curl -L -O https://gist.githubusercontent.com/slape/58541585cc1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat > /etc/ansible/files/metricbeat-config.yml

Copy metricbeat-config.yml file to /etc/ansible/files


•	Update the metricbeat-config.yml file by doing nano /etc/ansible/files/metricbeat-config.yml to include ELK private IP 
•	10.2.0.4 under hosts under the elastic search output section. Also add it to the host section in the setup.kibana. 








![image](https://user-images.githubusercontent.com/105944451/169669100-752e3cd6-d793-4373-ad91-bc113f79f96a.png)
