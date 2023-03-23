# Ansible Installation

Commandes supplémentaires 
### Pre-requisites

ansible installé sur la machine 

### Installation steps:
#### on Amazon EC2 instance

1. Install python and python-pip
   ```sh
    ssh-keygen
   ```
   Message : 
   ```sh

    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/ansadmin/.ssh/id_rsa):
    Created directory '/home/ansadmin/.ssh'.
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /home/ansadmin/.ssh/id_rsa.
    Your public key has been saved in /home/ansadmin/.ssh/id_rsa.pub.
    The key fingerprint is:
    ```
    Trouver les clés publique et privée
    ```sh
    [ansadmin@Ansible_Server .ssh]$ ll /home/ansadmin/.ssh
      total 8
      -rw------- 1 ansadmin ansadmin 1675 Mar 23 11:56 id_rsa
      -rw-r--r-- 1 ansadmin ansadmin  405 Mar 23 11:56 id_rsa.pub
      [ansadmin@Ansible_Server .ssh]$
    ```  
    
    Ajouter les Alias applicatifs et adresses ip des serveurs de deploiement
    ```sh
      vi /etc/ansible/hosts
    ```
