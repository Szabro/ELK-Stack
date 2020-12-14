## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Szabro/Project13/blob/main/Diagrams/ELK-Stack-Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/Szabro/Project13/blob/main/Ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics & statistics.

The configuration details of each machine may be found below.

| Name          | Function        | IP Address   | Operating System |
|---------------|-----------------|--------------|------------------|
|               |                 |              |                  |
| Jump Box      | Gateway         | 40.78.90.158 | Linux            |
| Web-1         | Virtual Machine | 10.0.0.5     | Linux            |
| Web-2         | Virtual Machine | 10.0.0.6     | Linux            |
| Web-3         | Virtual Machine | 10.0.0.7     | Linux            |
| ELK_Ubuntu_VM | ELK Monitor     | 10.1.0.4     | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 99.71.140.210

Machines within the network can only be accessed by Jump Box.
- Jump Box @ 40.78.90.158

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible |     Allowed IP Addresses    |
|----------|---------------------|-----------------------------|
| Jump Box | Yes/No              | 10.0.0.5 10.0.0.6 10.0.0.7  |
|          |                     |                             |
|          |                     |                             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it reduces the margin for error for unfirom configuration deployment and ensures all machines are configured the same.

The playbook implements the following tasks:
- Install docker.io
- Increase virtual memory
- Set parameters for virtual memory configuration
- Install python3
- Install python docker
- Download & launch ELK container for ports  5601, 9200, & 5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Szabro/Project13/blob/main/Diagrams/Docker-ps-command.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 @ 10.0.0.5
- Web-2 @ 10.0.0.6
- Web-3 @ 10.0.0.7

We have installed the following Beats on these machines:
- Web-1 @ 10.0.0.5
- Web-2 @ 10.0.0.6
- Web-3 @ 10.0.0.7

These Beats allow us to collect the following information from each machine:
- Filbeat: collect logs and other data 
- Metricbeat: to collect metric data
- Packbeat: to collect network data
- Auditbeat: to collect audit data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to /etc/ansible/.
- Update the install_elk.yml file to include
  - the remote user
  - hosts
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.