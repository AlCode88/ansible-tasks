Inventory files can be .YAML or .yml this is how you can define yaml formats. 
“ - - - “ is the begging of he Yaml in Ansible but there are some scenarios when you put two “- - -“ and that means it is a begging of the completely new section in that file and will be treated as a completely disconnected from the top. That is the big note for the kubernetees users. It is used in Kubernetees a lot.
We will create a new folder and call it production and we will write a new session_5.yaml inside that production folder. 

For the sake of example if we configure the name of our ansible host server IPs in the same line and will not put “:” in the end it will not take it as a key:value and you will get the following error.
00.000.00.00
00.000.00.00
If you put “:” in the end then it should be successful because it now represents key value.

Echo $? - is how you check the error code in the Linux.
And depending on error you will get a code number code “0” means success and the rest is Standard Error. 
-0-100,   -100+,    200(success), 200+,    -300+(redirection), -400+(something is wrong with the server)   -500+ (something is wrong with the client).

Now we will be configuring  the SSH port from the default to the custom and will be writing a playbook and establish connection to our default assigned port. 
The default SSH port is 22. 
And Default Protocol for the SSH connection is TCP(Transmission Control Protocol) - 3 way handshake.  

So what if we change the port from port 22 to the other port is ansible smart enough to know that and connect it to the different ssh port? 
First you need to manage and change the port the SSH configuration of that server inside the  /etc/ssh/sshd_config is the default location of the ssh deamon configuration file. And we need to modify it we can do vi or vim /etc/ssh/sshd_config  


When you will run vi /etc/ssh/sshd_config you will see this configuration and you need to run the selected command when you will be making any changes of the SELinux configuration. 
semanage port -a -t ssh_port_t -p tcp #portnumber
And what we have to do is under #port 22 we need to uncomment it and we can define there our own specific port and there are 65,535 ports are available and they have HIGH numbers, RESERVED numbers like port 80, 443 etc. And lets give the port very high number like 55500 save and quite.
When you do the configuration change you need to restart the system where you did the configuration change. So in our case we did configuration of sshd and we need to restart sshd deamon systemctl restart sshd and after restarting the system we need to run the selected command - semanage port -a -t ssh_port_t -p tcp 55500  the last number is our custom port. Exit from the Centos Server and check the connection on port 22 if you can be able to make that connection, if yes so it means you did not make changes. Connection refuse is the right error. 
And in order to ssh back to the Centos server we need to run the ssh -p port number (55500 in our case)root@ip  and we have to be able to ssh now.







By default Ansible knows that the connection should be established on port 22 but if you changed the port you should let the ansible know that you specified another port which is in our case was port 55500 for the Centos server. So to do that we need to define it in the host file in the Centos side. This is was our default inventory file before the change of port.  
