1. Create GCP VM.
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
