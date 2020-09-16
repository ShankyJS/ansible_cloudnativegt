# Ad Hoc commands practice

## 1) Crea un folder para almacenar los archivos de esta practica

````BASH
mkdir adhoc_commands && cd $_
````

## 2) Crea un archivo llamado ansible.cfg

````BASH
touch ansible.cfg && nano $_
````

Agrega dentro de este archivo la siguiente configuración para Ansible:

````Ansible
[defaults]
host_key_checking = False
````

## 3. Crea un archivo llamado inventory y agrega las ips de tus hosts

Ansible tiene la capacidad de detectar los hosts que agregues a un archivo de texto plano, puedes colocar las ips solamente o tambien puedes seccionarlo por grupos.

````BASH
touch inventory && nano $_
````

Si tienes un servidor puedes colocarlo con el siguiente formato o también puedes hacer pruebas apuntando a tu localhost.

(Contenido de archivo inventory)

````ansible
[hosts]
127.0.0.1
````

## 4. Instalación de Ansible

Puedes instalar Ansible de varias maneras, ya sea con pip (Python package manager), o con cualquier gestor de paquetes en UNIX, ya sea apt, dnf, yum, homebrew.

En este caso daré algunos ejemplos de como instalar Ansible en sistemas UNIX. 

En Fedora:

````bash
sudo dnf install ansible
````

En RHEL y CentOS:

````bash
sudo yum install ansible
````

Ubuntu y amigos:

````bash
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
````

## 5. Probando AdHoc commands

Algunos comandos que puedes probar con el inventory que queramos, ten cuidado debido que con este inventory estas trabajando en tu maquina local.

````Ansible
ansible hosts -i inventory -u YOUR_USERNAME -m MODULE
````

¿Cómo probar si realmente puedo comunicarme con las máquinas virtuales o nodos?

````Ansible
ansible hosts -i inventory -u shankyjs -m ping
````

Este comando nos retornara algo parecido a esto:

````Ansible
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
````

En ocasiones tendras que hacer algo como:

````SSH
exec ssh-agent bash
ssh-add ~/.ssh/id_rsa
````

Otros tipos de comandos:

````ansible
ansible all -i inventory --become -m shell -a "command"
````
