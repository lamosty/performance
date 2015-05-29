# Ansible Automation

Before benchmarking the performance of various web serving software, we have to install and configure the server. However, if done manually, it is a tedious task and takes a lot of time. One of the solutions to this problem is to use an automation tool. 

Ansible is a modern IT automation tool. It is a command line application which runs from a host computer, executing commands on remote servers. The main parts of Ansible are tasks and modules. 

Ansible Task has a name describing, in short, what it does. The task runs single Ansible module which performs some operations on the server. These modules are subprograms that can usually take several arguments, altering its behavior. 

For better organization, tasks can be grouped into roles and playbooks. Ansible Role is a logical container for multiple related tasks aiming to accomplish a single goal, like installing and setting up Nginx. An Ansible Playbook is a file specifying roles which should be run on specific servers. These servers are listed in a hosts file located within the Ansible project directory. 

Ansible files (except for the hosts) are written in the YAML syntax. It is straightforward to read and understand. We have prepared several playbooks which will provision the whole server so it can be benchmarked. They are located in the appendix of the work.