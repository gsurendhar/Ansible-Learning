```
ansible all -i <IP-ADDRESS>  -e ansible_user=<USER-NAME> -e ansible_password=<PASSWORD> -m <MODULE> 
```

✅ -i
Inventory
Specifies the inventory file or host list.

Example:
```
ansible all -i inventory.ini -m ping
```
This tells Ansible to use inventory.ini to find the hosts.


✅ -e
Extra variables
Allows you to pass extra variables to the playbook or command.

Example:
```
ansible all -i inventory.ini -m shell -a "echo hello" -e "ansible_user=ubuntu"
```
This overrides or sets ansible_user=ubuntu.


✅ -m
Module
Specifies which module to run (like ping, shell, copy, etc.).

Example:
```
ansible web -m ping
```
This uses the ping module on the group web.


✅ -a
Arguments
Passes arguments to the module specified with -m.

Example:
```
ansible web -m shell -a "uptime"
```
This runs the uptime command using the shell module.


Full Example:
```
ansible all -i hosts -m shell -a "df -h" -e "ansible_user=admin"
```
Run the `df -h` command

Using the `shell` module

On all hosts in `hosts` inventory

As the user `admin`