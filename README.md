Columbia Cyber Security Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


![Elk_Stack_Diagram1](https://user-images.githubusercontent.com/105944451/169670029-961d06e7-2ee9-4b61-8f27-2e64be389f17.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml and configuraton file may be used to install only certain pieces of it, such as Filebeat.

Enter the playbook file.

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
 What aspect of security do load balancers protect? What is the advantage of a jump box?
•	Load Balancers protect against denial of service attacks (DDoS) because the load balancer analyzes the traffic coming in and determines what server to send the traffic to

•	You can increase the security of your entire network with a jumpbox.A jump bix is a system set up with multi factor authentication usually placed in a network DMZ with very restricted access to the corporate network and no returning Internet access for any protocol.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system system logs.

What does Filebeat watch for? 
•	Filebeat monitors the log files or locations that one specifies, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

What does Metricbeat record?_
•	Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache


The configuration details of each machine may be found below.

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
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
•	Configure elk VM with Docker
•	Install docker.io
•	Install python3
•	Increase Virtual Memory
•	Published ports 5044,5601,9200

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Container](https://user-images.githubusercontent.com/105944451/169670118-baa289b1-bf1c-4ccf-81bd-38478d2f365f.png)



Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_
•	Web 1: 10.0.0.7 
•	Web 2: 10.0.0.8


We have installed the following Beats on these machines:
Specify which Beats you successfully installed_
These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Filebeat
Collects the logs for each virtual machine. It collects traffic from specific countries, number of visitors, and errors such as 404.
![Filebeat status](https://user-images.githubusercontent.com/105944451/169670176-5ce93294-692b-4069-a466-6b308f50cc3d.png)



### Metricbeat 
provides information on metric logs for the virtual machines. Information on CPU, Memory Usage, Network stats.
![Metricbeat status](https://user-images.githubusercontent.com/105944451/169670179-7b95dfe7-11ec-4ced-90c0-074661e53d72.png)

