# ELK-Stack-Project
ELK Stack Project for 2021
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/Jwulfe/ELK-Stack-Project/blob/main/Week12HW.JPG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk YML](https://github.com/Jwulfe/ELK-Stack-Project/blob/main/ElkYML)
  - [Filebeat Playbook YML](https://github.com/Jwulfe/ELK-Stack-Project/blob/main/FileBeat%20Playbook%20YML)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessable, in addition to restricting access to the network.
- The load balancer is used to make sure that the site or server is accessable even during times of very high traffic. The Jumpbox is a machine that interacts with the infrustructure and the outside net and is the only box to do so. It ensures the security of the network to limit the access of the outside web.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat is used to log and centralize files on a network
- Metricbeat records different logistics on the network including hardware usage, or metrics of a system.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.7   | Linux            |
| Web1     | VM 1     | 10.0.0.5   | Linux            |
| Web2     | VM 2     | 10.0.0.6   | Linux            |
|Elk Server|Monitoring| 10.0.1.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Jumpbox: 10.0.0.7

Machines within the network can only be accessed by the jumpbox ssh.
- The jumpbox can access ELK server and use Ansible and the appropriate Docker to access and modify it.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |        No           |       Personal IP    |
| Web1     |        No           |       10.0.0.7       |
| Web2     |        No           |       10.0.0.7       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage of automating the configuration is that the execution is done at the time of running the playbook, as well as removes the possibility of human error to incorrectly configure the ELK machine.

The playbook implements the following tasks:
- Install Docker; set up docker; run docker; start docker; connect to docker
- Download the configuration code
- Create a config file with the code in the ansible filepath
- Create a playbook yml file to run the config file in the ansible filepath
- Run the playbook yml file

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![DockerPS](https://github.com/Jwulfe/ELK-Stack-Project/blob/main/DockerPSImage.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1: 10.0.0.5
- Web2: 10.0.0.6

We have installed the following Beats on these machines:
- We have installed Filebeat and Metricbeat to monitor the machines.

These Beats allow us to collect the following information from each machine:
- Filebeat tracks the files and analytics that are on the machines while Metricbeat logs the machines performance figures and other performance metrics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Metric and Filebeat file to the ansible: roles: files directory.
- Update the config file to include the private IP address of the ELK Server.
- Run the playbook, and navigate to ELK-Serv to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it? The filebeat_playbook.yml file is the playbook and copied it to the ansible hosts directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- You would have to update the filebeat.yml file and designate the appropriate IP address of the machines you want to instal the ELK server and Filebeat on in the .yml file.
- http://104.43.134.17:5601
