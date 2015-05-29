# Installing Required Software on the Server

We are going to install all the required software on our testing server. Clone the *wordpress-ansible* GitHub repository[^1] to your local computer. In the folder, we can find a few playbooks, hosts file, variables and roles. We will be referring to this folder by the name "wordpress-ansible" in the work. 

The first step is editing the hosts file. Put the IP address or hostname of your testing server in the file and assign it to the webservers group. 

Secondly, we need to install Ansible on our local computer. Official Ansible documentation[^2] explains how to do it. 

The next step is to edit the group variables for our testing server. Open the `group_vars/webservers` file and modify it to your needs. If you are satisfied with the default values, there is no need to change it. 

After completing all the previous steps, navigate to the wordpress-ansible folder in your command line and execute following command:

```bash
ansible-playbook -i hosts install-all-software.yml
```

During the installation process, Ansible will inform you about the status of executed tasks, whether they went successfully or not. 

We are now ready to benchmark web serving software.

[^1]: GitHub: [Ansible playbooks for installing multiple kinds of server stacks with performance optimizations and security in mind](https://github.com/lamosty/wordpress-ansible)

[^2]: Ansible Docs: [Installation](http://docs.ansible.com/intro_installation.html)