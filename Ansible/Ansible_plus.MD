# Ansible Installation

Commandes supplémentaires 
### Pre-requisites

ansible installé sur la machine 

### Installation steps:

1. générer la clé 
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
    ```  
    
    Ajouter à la VM ansible les Alias applicatifs et adresses ip des serveurs de deploiement
    ```sh
      vi /etc/ansible/hosts
    ```
    
     Pousser la clé vers le serveur distant ( connexion au serveur ansible)
    ```sh
      ssh-copy-id adresse_ip
    ```
    ```sh
     ssh-copy-id adresse_ip
    ```

   Message :
    ```sh

      /usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/ansadmin/.ssh/id_rsa.pub"
      The authenticity of host 'adresse_ip (adresse_ip)' can't be established.
      ECDSA key fingerprint is SHA256:SBLRxxxyW/xxxxxxxxxxxxxxxxxxxxxxxxxxx.
      ECDSA key fingerprint is MD5:c4:xx:xx:3a:xx:xx:bb:xx:57:92:xx:xx:xx:xx:5a:xx.
      Are you sure you want to continue connecting (yes/no)? yes
      /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
      /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
      ansadmin@adresse_ip's password:

      Number of key(s) added: 1

      Now try logging into the machine, with:   "ssh 'adresse_ip'"
      and check to make sure that only the key(s) you wanted were added.
    ```
    
      Connexion avec ansible all
    ```sh
     ansible all -m ping
    ```
   
   Résultat
   ```sh
         [WARNING]: Platform linux on host adresse_ip is using the discovered Python interpreter at /usr/bin/python, but future installation of another Python interpreter    could change this. See
         https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information.
         adresse_ip | SUCCESS => {
          "ansible_facts": {
              "discovered_interpreter_python": "/usr/bin/python"
          },
          "changed": false,
          "ping": "pong"
      }
  ```

  Connexion avec ansible all
    ```sh
    ansible all -m command -a uptime
    ```

```sh
ansible all -a uptime
```
==> Test non concluant

Récupérer l'asresse ip du serveur actuel
```sh
ifconfig
```

on peut également utiliser localhost

```sh
ssh-copy-id adresse ip
```

Test concluant mnt
```sh
ansible all -a uptime
```

```sh
cd /opt/docker/
```

```sh

cat regapp.yml
---
- hosts: ansible

  tasks:
  - name : create docker image
    command: docker build -t regapp:latest .
    args:
      chdir: /opt/docker

```

```sh
ansible-playbook regapp.yml --check
```

```sh
ansible-playbook regapp.yml
```

```sh
docker images
docker tag 0dc772956e85 alexanglais/regapp:latest
```

```sh
docker images
```

```sh
docker push alexanglais/regapp
```
   
   
