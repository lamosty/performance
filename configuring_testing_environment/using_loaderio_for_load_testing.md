# Using loader.io for Load Testing

Apart from having a server running a WordPress-based site, we need a tool for load testing the server. Initially, we used a popular command line utility called "ab" (standing for Apache Bench). However, this approach also required a second server from which the ab utility would be run. What is more, storing the tests results and plotting them on charts with ab is not trivial.

We found a simple cloud-based load testing service called "loader.io"[^1]. In a subscription, free of charge, we get 10,000 clients (requests) per test and one target host. For our purposes, these parameters are enough.

After creating an account at loader.io and adding a target host (our testing VPS server), we are presented with a dialog to verify the ownership of the server. While putting the token manually in a text file to our WordPress site directory will allow loader.io to verify the server, it is better to come up with an Ansible playbook which would automate this task for us. Below is the YAML definition file of the playbook.

```
---
- name: Loader.io host verification >
 
  hosts: webservers
  remote_user: root
  vars:
    token: <YOUR-TOKEN-HERE>
 
  tasks:
  - name: Install loader.io verification token
    shell: echo {{ token }} > {{ token }}.txt
    args:
      chdir: "{{ remote_wordpress_dir }}"
      creates: "{{ remote_wordpress_dir}}/{{ token }}.txt"
```

Replace `<YOUR-TOKEN-HERE>` placeholder with your verification token and save the playbook as "loader.io-verification.yml". Whenever we provision a new testing WordPress site, we only need to run the loader.io-verification.yml playbook to have the token inserted to the site.

[^1]: Loader.io: [Application Load Testing Tools for API Endpoints with loader.io](http://loader.io/s/XoYdj)
