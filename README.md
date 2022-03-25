# ANSIBLE


## COMMANDS

### Copy SSH Key
```sh
ssh-keygen
ssh-copy-id -i ~/.ssh/my_key user@host
ssh -i ~/.ssh/my_key user@host
```

### Sudo no password
```sh
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER
```

### Run Ad-hoc  Commands

```sh
ansible all -m ping -i inventory.ini --private-key /home/jpastor/.ssh/my_key
ansible all -m ping -i inventory.ini --private-key /home/jpastor/.ssh/my_key -u root
ansible all -m ping -i inventory.ini --ask-password

ansible webserver.internal.local -m ping --private-key ~/.ssh/jpastor_key -i inventory.ini
ansible webserver -m ping --private-key ~/.ssh/jpastor_key -i inventory.ini

ansible webserver -a "/sbin/reboot" --private-key ~/.ssh/jpastor_key -i inventory.ini
ansible webserver -m ansible.builtin.copy -a "src=/etc/hosts dest=/tmp/hosts" --private-key ~/.ssh/jpastor_key -i inventory.ini
ansible webserver -m ansible.builtin.apt -a "name=apache2 state=present" --private-key ~/.ssh/jpastor_key -i inventory.ini
```

## Run Playbok
```sh
ansible-playbook apache2.yml --private-key  ~/.ssh/jpastor_key -i inventory.ini -b -u jpastor
ansible-playbook apache2_withrole.yml --private-key  ~/.ssh/jpastor_key -i inventory.ini
```