- By default there is two groups "all" and "ugroupped".

- ansible --list-host -i inventory.yaml all --- will list you the all available hosts in that you have with the contorol node and if you want to check it by group name you can run the following command ansible --list-host -i inventory.yaml ungroupped or it can be prod or dev as well.

there is a defult varibales that ansible stores in the memory. For example "group_name" 


<h1><b>Session Tasks</b></h1>

<b>Tasks 1:</b>
Define a yaml format inventory. Create a group called "prod" in your inventory file. Write a playbook that pings servers, only if "prod" group is defined in inventory.yaml
