##How to use ssh on debian.

#Step 1:Install SSH Server
On the system that acts as a server, run the following command:

<sudo apt install openssh-server>

Enter your password when prompted, then press Y to continue the installation. In this case, the output states that the newest version is already installed

You can check the status of the SSH service with the following command:

<sudo systemctl status ssh>

##Start and Stop the SSH Server

Since SSH controls connections, it can be handy to know how to start and stop the service.

To stop the SSH host server, enter the following:

<sudo service ssh stop>

If you check the status of the service at this point the system indicates that SSH is inactive. It also indicates the exact date and time it stopped.

##To start the SSH service, use the following command:

sudo service ssh start

Stopping the service only lasts until the next reboot.

To turn off SSH indefinitely, enter:

<sudo systemctl disable ssh>

To re-enable the SSH service, simply replace disable with enable.

#Step 2:Get Your Server IP Address
If you’re configuring a server locally, you can display the IP address from a terminal window with the following command:

<ip a>

The IP address will be in a format like this:

<192.168.0.1>

If you’re connecting to a server that’s already configured, you’ll want to get the IP address from the server’s administrator. Or, you can log in using the server’s hostname or domain name.

##Install SSH Client Service (Optional)
If you’re connecting to a server that’s already set up, or you’ve completed the previous steps on your server, open a terminal window on your client system and update the package list:

<sudo apt-get update>

By default, most Linux systems have the SSH client installed. If yours doesn’t, enter the following command:

<sudo apt-get install openssh-client>

#Step 3:Connecting to a Server Using SSH

Enter the following command to connect to the server using a secure shell:

<ssh UserName@IPAddressOrHostname>

Replace the UserName with the username of an authorized user on the server. After the @ sign, use the IP address from Step 4, or you can use the domain name. You can also specify a hostname if the server is configured to use one.

When connecting for the first time, the system may prompt you for confirmation. Type ‘yes‘ and then ‘enter‘.

The remote system will prompt you for a password. Use the password that goes with the username you’ve provided.

The command prompt will change to username@hostname, indicating that the commands you are running are being executed on the remote server.

##Firewall and Security Settings
B
y default, Debian uses the UFW firewall which can interfere with secure shell traffic.

To allow SSH access, use the command:

<sudo ufw allow ssh>

SSH traffic goes through port 22.

To implement the necessary security measures, use your firewall application (or router configuration) to set up port forwarding. You’ll need to refer to your documentation for specifics. However, the strategy is to forward traffic requests coming in on port 22 to the IP address of the machine behind the firewall.

You can also configure your firewall or router to accept SSH traffic on a different port, it’s an added step, but then you can route that incoming traffic to port 22 on your server. This is a helpful solution when opening up your server to internet traffic. Why? Many intrusion attempts come in on port 22 trying which try to access SSH. Changing the port will restrict access to only those who know the correct port, thereby limiting unauthorized connections.



