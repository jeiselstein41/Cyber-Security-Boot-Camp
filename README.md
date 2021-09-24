# Cyber-Security-Boot-Camp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/jeiselstein41/Cyber-Security-Boot-Camp/blob/a68842a8f26194b8238f46b730113e1ccc09c6da/diagrams/Cloud-Diagram.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - The ansible-playbooks elk.yml and the filebeat-playbook.yml are needed to create and implement the Elk-Server._

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
- Load balancers protect the availability and redundancy aspect of security.
- The advantage of a jump box allows for an origination point for launching administrative tasks. The jump box is ultimately a Secure Admin Worktstation or SAW. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat collects data about the file system
- Metricbeat collects machine data such as uptime

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| DVWA-Web1| Azure VM | 10.0.0.6   | Linux            |
| DVWA-Web2| Azure VM | 10.0.0.7   | Linux            |
|ELK-Server| Analytics| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 71.93.144.67

Machines within the network can only be accessed by my home IP address.
- The ELK machine can be accessed by my host machine IP: 71.93.144.67 jump box IP: 10.0.0.5, DVWA-Web1 IP: 10.0.0.6, and DVWA-Web2 IP: 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 71.93.144.67         |
| DVWA-Web1| No                  | 10.0.0.5             |
| DVWA-Web2| No                  | 10.0.0.5             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- it allows for setup in minutes using OpenSSH without installing anything on the servers.

The playbook implements the following tasks:
•	Install Docker.io
•	Install Python-pip
•	Increase Virtual Memory
•	Download and Launch ELK Docker Container (image sebp/elk)
•	Published ports 5044, 5601 and 9200 were made available

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/jeiselstein41/Cyber-Security-Boot-Camp/blob/main/docker_ps_output.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA-Web1 IP:10.0.0.6
- DVWA-Web2 IP:10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
•	Filebeat will be used to collect log files from very specific files such as Apache, Azure tools and web servers.
•	Metericbeat will be used to monitor VM stats, per CPU core stats, per filesystem stats, memory stats and network stats.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to /etc/andsible directory.
- Update the hosts file to include the IPs of each group so that Ansible knows which machines need to be run on a given playbook.
-Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- The .yml files are playbook files that can be run with Ansible. Typically, it's copied into a container where ansible is installed to be deployed.
- The Hosts file allows for grouping of machines so you can dictate where you want resources to be deployed.
- Navigate to [13.78.20.243:5601/app/kibana]

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

•	Sudo docker start [container name]
•	sudo docker ps
•	sudo docker exec -ti [container name] bash
•	sudo ansible-playbook [.yml file to run]

