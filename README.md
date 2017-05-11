# ansible-php71-mysql56
Installs and configures PHP+Nginx+MySql server on CentOS6.
- PHP7.1
- MySQL5.6
- Nginx/1.10.3

# Quick Setup
### Prerequisite
* Mac OR Windows
* Vagrant(1.8.1+)
* VirtualBox(12.0.7+)

### Provisioning environment
1. Download git repository
  ```
  cd ansible-php71-mysql56
  vagrant up
  ```

# Development Setup
### Prerequisite
* Mac(macOS Sierra)
* Vagrant(1.8.1+)
* VirtualBox(12.0.7+)
* Ansible(2.2.2+)
  ```
  1. wget https://bootstrap.pypa.io/get-pip.py get-pip.py
  2. python get-pip.py
  3. pip install ansible
  ```

### Provisioning environment
1. Download git repository
   ```
   git clone https://github.com/linzhengen/ansible-php71-mysql56.git
   ```
1. Provisioning
   ```
   cd ansible-php71-mysql56
   vagrant up
   ansible-playbook -i inventories/vagrant playbooks/vagrant.yml
   ```
# Production Setup
### Prerequisite
- Remote server
  - CentOS6

- Local PC
  - Mac(macOS Sierra)
  - Ansible(2.2.2+)
    ```
    1. wget https://bootstrap.pypa.io/get-pip.py get-pip.py
    2. python get-pip.py
    3. pip install ansible
    ```


### Provisioning environment
1. Download git repository
   ```
   git clone https://github.com/linzhengen/ansible-php71-mysql56.git
   ```
1. Replace with production setting
   - public ip
     ```
     cd ansible-php71-mysql56
     sed -i -e "s/xxx.xxx.xxx.xxx/{production_global_ip}/" ./inventories/production/hosts ./inventories/production/default
     ```

   - rootpass
     ```
     sed -i -e "s/rootpass/{root_pass}/" ./inventories/production/default
     ```

1. Provisioning
   ```
   cd ansible-php71-mysql56
   brew install sshpass
   ansible-playbook -i inventories/production/default playbooks/secure.yml
   ansible-playbook -i inventories/production playbooks/iptables.yml
   ansible-playbook -i inventories/production playbooks/prodction.yml
   ```





