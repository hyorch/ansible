# ANSIBLE


## COMMANDS

### Copy SSH Key
```sh
ssh-keygen
ssh-copy-id -i ~/.ssh/my_key user@host
ssh -i ~/.ssh/my_key user@host
```

### Run Module

```sh
ansible all -m ping -i inventory.ini --private-key /home/jpastor/.ssh/my_key
ansible all -m ping -i inventory.ini --private-key /home/jpastor/.ssh/my_key -u root
ansible all -m ping -i inventory.ini --ask-password

ansible webserver.internal.local -m ping --private-key ~/.ssh/jpastor_key -i inventory.ini
ansible webserver -m ping --private-key ~/.ssh/jpastor_key -i inventory.ini
```