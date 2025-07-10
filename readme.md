# Automating Infrastructure Management with Ansible 

## Create 3 ec2 instances 
One of the ec2 instance will be named as 'ansible' rest two of them would be 'web' and 'db' servers. Configuration of ec2 instances would be Amazon 2023 linux t2.micro with public ssh and http access.


## Login to ansible server

Install ansible
```bash
sudo yum install ansible -y
```

## Transfer ssh public key from anisble server to web and db server authorized keys
On ansible server do this. Press enter twice after 'ssh-keygen'
```bash
cd .ssh
ssh-keygen
cat id_rsa.pub
```
Copy id_rsa.pub key and go to 'web' and 'db' server and paste it to autherized keys path ( cd .ssh ). Try connecting via ssh from anisble to web and db servers.

## Clone project

```bash
git clone https://github.com/bryanjoachim/ansibleroles.git

```

## Go to iventory.ini and make chnages with your own server public ip

```bash
nano inventory.ini

```

## Go to repository settings and click on 'Secerts and variables' and 'New repository secret'
Copy ansible server private key from 'cd .ssh' id_rsa and paste it on Secret. You can name it as 'ANSIBLE_SSH_PRIVATE_KEY'

## Push deployments to web and db

```bash
ansible-playbook -i inventory.ini playbook.yml

```




