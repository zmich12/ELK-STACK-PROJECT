# ELK-STACK-PROJECT
ELK stack project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Diagrams/ELK-Project.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-install.yml file may be used to install only certain pieces of it, such as Filebeat.

  - (Ansible/)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available to access, in addition to restricting access to the network.
- Load balancers can provide protection against ddos and other overloading of the platform. 
- A jump box prevents direct access to the stack

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.
- Filebeat watches for log file changes.
- Metricbeat records metrics on the system.

The configuration details of each machine may be found below.

| Name                 | Function      | IP Address | Operating System |
|----------------------|---------------|------------|------------------|
| Jump-Box-Provisioner | Gateway       | 10.0.0.1   | Linux            |
| Web1                 | VM            | 10.0.0.5   | Linux            |
| Web2                 | VM            | 10.0.0.6   | Linux            |
| ELK-SERVER           | ELK Stack     | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- (Home IP Address)

Machines within the network can only be accessed by SSH on Jump-Box-Provisioner.
- Jump-Box-Provisioner 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | Home IP Address      |
| Web1                 | No                  | 10.0.0.4             |
| Web2                 | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows the process to be replicated and automated. It also allows for a much quicker provisioning and to pull the most up to date files. 

The playbook implements the following tasks:
- Installs Docker
- Installs Python3
- Download and launch ELK container

The result of running `docker ps` after successfully configuring the ELK instance shows the container ID and the command line prompt:
`RedAdmin@ELK-SERVER`

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.5 
- Web2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files 
-- e.g. MySQL, Apache
- Metricbeat collects metrics from the system
--  e.g. uptime, resources used

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Jump-Box-Provisioner.
- Update the playbook file to include the Web1 and Web2 IP addresses
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
