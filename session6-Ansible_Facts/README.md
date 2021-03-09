Session Tasks

Tasks 1:
On Debug playbook add one or more variables called "variables2" with value "This is value 2" call both variables with debug.

Task 2:
Write a Playbook that prints distribution and major version of all managed servers call the playbook - gather_facts.yaml

Task 3:
Install htop, curl and vim on all servers playbook name packages.yaml

Task 4:
Install and start apache on all servers playbook name apache.yaml



Session Notes:

Ansible collects pretty much all the information about the remote hosts as it runs a playbook. The task of collecting this remote system information is called as Gathering Facts by ansible and the details collected are generally known as facts or variables.

 <b> ansible -i iventory.yaml ubuntu setup | less - command <b>will show you page by page all the information about remote servers

DEBUG: module that prints the statement during the execution. 

There is variables that already reserved by the system like "{{ansible_hostname}}" that gets the hostname from the remote servers

<h1><b>Variables:<h1><b>