# SFTP

##Notes and Scripts     

###On Unix Server:   
SSH Server changes:   
sudo nano /etc/ssh/sshd_config   
Subsystem sftp internal-sftp -l INFO   
no password   
publickeyauth = yes   
sudo systemctl restart ssh   

###For inbound:
(In user's home directory)
mkdir ~./ssh
chmod 0700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 0644 ~/.ssh/authorized_keys
Upload Public Key to ./ssh
cat ssh-public-key-openssh >> authorized_keys

###For Outbound:
Run ssh-keygen to create public\private key
Copy public key to destination server

movefiles.sh
#!/bin/bash
sftp -oPort=6522 -b commands.txt remoteuser@192.168.7.34

commands.txt
#Upload file
put testfile.txt /home/nick
exit

###Commands
sftp> put - Upload file
sftp> get - Download file
sftp> cd path - Change remote directory to 'path'
sftp> pwd - Display remote working directory
sftp> lcd path - Change the local directory to 'path'
sftp> lpwd - Display local working directory
sftp> ls - Display the contents of the remote working directory
sftp> lls - Display the contents of the local working directory
