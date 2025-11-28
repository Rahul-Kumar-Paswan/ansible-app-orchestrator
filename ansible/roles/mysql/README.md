# MySQL Role
=========

Description
------------
This role installs and configures MySQL server on Ubuntu, including:
- MySQL root user setup with password
- Remote access for root and application user
- Application database creation
- Dynamic `bind-address` configuration
- Optional integration with Ansible Vault for secrets

Requirements
------------

- Ubuntu 18.04/20.04+
- Ansible >= 2.9
- Python3 and PyMySQL library

Role Variables
--------------

Defined in `vars/main.yml`:
```yaml
mysql_root_password: "RootPass123!"
mysql_database: "rahulverse_db"
mysql_user: "rahulverse_user"
mysql_password: "UserPass123!"
db_host: "localhost"
```

Example Playbook
----------------
```yaml
- hosts: dbserver
  become: true
  vars_files:
    - ../roles/mysql/vars/main.yml
  roles:
    - roles/mysql
```

License
-------

BSD

Author Information
------------------

Rahul Paswan
GitHub: [https://github.com/Rahul-Kumar-Paswan](https://github.com/Rahul-Kumar-Paswan)  
Portfolio: [https://rahulpaswanverse.vercel.app](https://rahulpaswanverse.vercel.app)