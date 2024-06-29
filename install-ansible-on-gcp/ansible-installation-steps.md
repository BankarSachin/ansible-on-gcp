__Install Control Node__

1. Create GCP COntrol Node VM.
```
To be eligible for Free tier machine use below combinations
machine-type=e2-micro
zone=us-central1-c 
diskTypes=pd-standard

keep machine name as ansible-control-node
```
2. ssh to new VM ansible-control-node
3. Create ansible user.And assign him admin rights
```
useradd -m -s /bin/bash ansadmin 
passwd ansadmin
echo "ansadmin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
```
4. Generate SSH pubic and private keys which would be used by passwordless authentication later on
```
ssh-keygen
```
5. Check and install python. Ansible needs python. Its built on top of python
```
apt install python3
apt install python3-pip
```
6. Install ansible
```
apt-get install python3-pip
```
7. Check ansible installation
```
ansible --version
```
**Install Managed Node**
1. Create GCP Managed Node VM.
```
To be eligible for Free tier machine use below combinations
machine-type=e2-micro
zone=us-central1-c 
diskTypes=pd-standard
```

2. ssh to new VM ansible-control-node
Create ansible user.And assign him admin rights
```
useradd -m -s /bin/bash ansadmin 
passwd ansadmin

echo "ansadmin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
```

3. Check password based authentication 
```
sudo vi /etc/ssh/sshd_config

check for PasswordAuthentication . Its values should be no
```

**SSH to Control Node**
1. Add IP address of managed node into hosts file
```
vi /etc/ansible/hosts
add IP of managed node
```
2. copy ssh key to host node 
```
Be sure you have sudo su - ansadmin. Because we had generated keys for this user
ssh-copy-id <ip of managed node>

Restart ssh service
systemctl restart sshd
```
3. ssh  to managed node to check connectivity
```
ssh <IP Address>
```