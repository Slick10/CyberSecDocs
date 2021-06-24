## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

C:\Users\SSAD\CyberSecDocs\Diagrams

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  -C:\Users\SSAD\CyberSecDocs\Ansible

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers have an important security role as it defends against DDoS attacks by moving attack traffic to another server. 
- The Jump Box gives the user access from a single node which can be secured and monitired.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jump Box and system network.
- Filebeat is a lightweight shipper that monitors the log files or locations specified and then fowards it to Elasticsearch and Logstash for indexing.   
- Metricbeat collects metrics from the operating system and services running on the server. It will then foward the data to the specified output which can be Elasticsearch and Logstash.  

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address      | Operating System |
|----------|----------|------------     |------------------|
| Jump Box | Gateway  | 104.42.32.250   | Ubuntu 20.04     |
| Web-1    | DVWA     | 10.0.0.5        | Ubuntu 20.04     |
| Web-2    | DVWA     | 10.0.0.6        | Ubuntu 20.04     |
| Web-3    | DVWA     | 10.0.0.7        | Ubuntu 20.04     |
| ELK-VM   | Elk      | 20.98.75.139    | Ubuntu 20.04     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- IP Address: 184.146.58.152

Machines within the network can only be accessed by Jump Box.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 184.146.58.152       |
| ELK VM   | Yes                 | 20.98.75.139         |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |
| Web-3    | No                  | 10.0.0.7             |       

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can limit the services running, streamlined system updates and installation and processes are replicable. 
- One main benefits for using ansible is that it allows IT administrators to automate daily task so they can focus on more important task for the organization. 

The playbook implements the following tasks:
- Install ELK-Playbook 
- SSH in the ELK container 
- Install Filebeat-Playbook
- Install Metricbeat-Playbook

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

- C:\Users\SSAD\CyberSecDocs\Ansible

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- IP addresses of the machines being monitoring.
  - 10.0.0.5
  - 10.0.0.6
  - 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files and sends the data to be index using elasticsearch or logstash. 
- Metricbeat monitors the servers by gathering metrics from the system and services running. It also will forward the data to elasticsearch and logstash.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the docker.io file to container.
- Update the docker file to include the latest updates.
- Run the playbook, and navigate to server to check that the installation worked as expected.

- /etc/ansible/ 
- Edit the ansible host file to add the elk/web servers
- http://20.98.75.139:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- docker run -it cyberxsecurity/ansible /bin/bash
- ansible-playbook /etc/ansible/playbook.yml
