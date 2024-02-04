# description ansible:
```
1-group_vars directory for varibles in any group in main inventory

2-host_vars directory for varibles in any host in main inventory

3-inventory directory 

4-log directory have a file for save logs ansible running

5-playbooks directory:
    describtions: 
    5-1: this directory contains multi file yaml differences , any file 
        conect with a sub directory in roles directory   
    5-2: file config.yml for import other file in the directory and 
        running all settings for   ansible command


6-roles directory:
    description: 
    
    6-1:for every yaml file in playbooks directory (without config file)
        we have a directory with name file
    6-2:files directory for static file use in server
    6-3:templates directory for use file with varibles

7-ansible.config file is settings global ansible and configuration customize

```

# install ansible and run project
```
1: clone project to the machin
    1-1: cd to favroite directory
    1-2: git clone 

2: install dependency
    2-1: sudo apt update
    2-2: sudo apt install software-properties-common
    2-3: sudo add-apt-repository ppa:ansible/ansible
    2-4: sudo wget -O - https://keyserver.ubuntu.com/pks/lookup?op=get&search=0xE251165069C45C89 & apt-key add -
    2-5: sudo apt update
    2-6: sudo apt install ansible
    2-7: sudo apt update
    2-8: sudo apt install python3-pip python3-dev libffi-dev libssl-dev libjansson-dev

3: install environment and python dependency
    3-1: python -m venv venv
    3-2: source venv/bin/activate
    3-3: pip install -r requirements.txt
   
4: test ansible
    4-1: ansible --version
    4-2: ansible-playbook playbook/test.yml
```

# ansible commands

```
1: for test one playbook in your machin
    1-1: change hosts in playbook to localhost
    1-2: ansible-playbook <path to playbook> --ask-become-pass

2: Checks the reachability of all hosts in your Ansible
    2-1: ansible all -m ping 

3: Gathers facts about all hosts, collecting system
    3-1: ansible all -m setup

4: Copies a file from the control machine to all hosts.
    4-1: ansible all -m copy -a "src=<path> dest=<path>"

5: Creates a file with specified content on all hosts.
    5-1:ansible all -m copy -a "dest=<path> content='<text-writing>' mode=0777"

6: Removes a file from all hosts.
    6-1:ansible all -m file -a "path=<path> state=absent"

7: Validates the syntax of an Ansible playbook before execution, catching potential errors early on.
    7-1:ansible-playbook --syntax-check <path-to-file>.yml
```

# ssh config
```
ssh-keygen -t rsa

ssh-copy-id username@server_address

ssh username@server_address
```