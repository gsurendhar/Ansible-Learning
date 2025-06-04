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



🔧 Common Ansible Ad Hoc Command Options
Option	| Description|	Example
----------------------|----------------------------------------------------|-------------------------------|
|`-i	`|Inventory file or host list|	`-i inventory.ini`|
|`-m`	|Module name (default is command)|	`-m ping`|
|`-a`	|Module arguments|	`-a "df -h"`| 
|`-e`	|Extra variables|	`-e "ansible_user=admin"` |
|`--ask-pass`	|Prompt for SSH password|	Useful when no key is set up |
|`--ask-become-pass`	|Prompt for sudo password|	For privilege escalation |
|`-u`	|Remote user|	`-u ubuntu` |
|`--become`	|Run operations with sudo (privilege escalation)|	`--become` |
|`--become-user`	|Run as specific user (default is root)|	`--become-user=admin` |
|`-k`	|Shortcut for `--ask-pass` (SSH password prompt)|	`-k `|
|`-K	`|Shortcut for `--ask-become-pass` (sudo password prompt)|	`-K`|
|`-f`	|Forks – number of parallel processes|	`-f 10` |
|`-t`	|Timeout for SSH connections|	`-t 30` |
|`--check`	|Do a dry run (no changes made)|	`--check` |
|`--diff`	|Show differences when changing files|	Useful with copy or template |
|`--limit`	|Limit the run to specific hosts|	`--limit webservers`|
|`--tags`	|Run only tasks with specific tags (used in playbooks)|	Not often used in ad hoc|
|`--list-hosts`	|Show list of targeted hosts and exit|	`--list-hosts`|
|`-v, -vv, -vvv, -vvvv`	|Increase verbosity level|	`-vvv` shows more debug info|
|`--syntax-check`	|Check playbook syntax (not used in ad hoc)|	For `ansible-playbook`|
|`--module-path	`|Path to custom modules|	`--module-path=./library/`|