# Spring Boot Role
=========

Description
------------
This role deploys a Spring Boot application on Ubuntu servers:
- Installs required dependencies
- Deploys application JAR/WAR
- Configures systemd service
- Connects dynamically to MySQL backend
- Supports multi-webserver deployment with dynamic hostvars

Requirements
------------

- Ubuntu 18.04/20.04+
- Ansible >= 2.9
- Java installed (OpenJDK 11+ recommended)
- Access to MySQL server

Role Variables
--------------

Defined in `vars/main.yml`:
```yaml
app_name: "rahulverse-user-portal"
app_user: "ubuntu"
db_host: "172.31.x.x"
db_port: 3306
```

Dependencies
------------

mysql role should be applied before if deploying DB as part of the project

Example Playbook
----------------
```yaml
- hosts: webserver
  become: true
  vars_files:
    - ../roles/springboot/vars/main.yml
    - ../roles/mysql/vars/main.yml
  vars:
    db_host: "{{ hostvars['db']['ansible_host'] }}"
    db_port: 3306
  roles:
    - roles/springboot
```

License
-------

BSD

Author Information
------------------

Rahul Paswan
GitHub: [https://github.com/Rahul-Kumar-Paswan](https://github.com/Rahul-Kumar-Paswan)  
Portfolio: [https://rahulpaswanverse.vercel.app](https://rahulpaswanverse.vercel.app)