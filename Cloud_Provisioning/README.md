# Provisionamiento de Cloud Resources en Digitalocean con Ansible Playbooks.

Esta es la segunda práctica compartida en el Meetup, para lograr realizarla necesitarás contar con los siguientes pre-requisitos.

## Prerequisitos.

- Paquetes necesarios: ansible (para ejecutar el playbook).
- Cuenta de DigitalOcean con una API Key extraída para crear resources. 


### Instalación de Ansible.

Este binario puede ser obtenido con el gestor de paquetes de tu sistema linux, en este caso se detallará el proceso para instalarlo desde un sistema operativo Ubuntu 18.04.

1) Añadir el repositorio oficial de Ansible.

````
sudo apt-add-repository ppa:ansible/ansible
````

2. Actualizar dependencias y repositorios en el sistema e instalar ansible.

````
sudo apt update
sudo apt install ansible
````

### Creando una cuenta de DigitalOcean y extrayendo una API Key.

1. Si no tienes una cuenta de digitalocean puedes registrarte usando este [link](https://m.do.co/c/e3c4799e0fa4)

2. Luego de crear tu cuenta puedes acceder a este link: https://cloud.digitalocean.com/account/api/

Das click a generar un nuevo Token y obtendrás un string que debes almacenar muy buen y jamás compartir (este token te permitirá crear recursos, borrar y administrar usando la API de DigitalOcean).

## Creando máquinas virtuales con Ansible-playbook

Cumpliendo estos prerequisitos ya estás listo para crear dos máquinas virtuales haciendo uso del playbook que dejé en la carpeta "Cloud_Provisioning"

En este caso lo que tendrás que hacer es clonar este repositorio y acceder a esa carpeta desde tu terminal.

````
cd Cloud_Provisioning
````

Una vez dentro necesitarás exportar una variable a la términal en la que estés trabajando. Lo puedes hacer de la siguiente manera:

````
export DO_API_TOKEN="inserta-tu-token-entre-estas-comillas"
````

Para probar que tu variable esté bien exportada puedes tratar de imprimirla en tu terminal.

````
echo $DO_API_TOKEN
````

Output:

````
┌🤘-🐧shankyjs@ 💻 shankyjs - 🧱 Cloud_Provisioning on 🌵  master •3 ⌀4 ✗
└🤘-> echo $DO_API_TOKEN
inserta-tu-token-entre-estas-comillas
````

Ahora ya podrás ejecutar los playbooks para crear los droplets o borrarlos de la siguiente manera:

(Para crear los droplets)
````
ansible-playbook -i inventory create_droplet.yml
`````

Al terminar de ejecutar el playbook notarás que se agregaron 2 máquinas virtuales a tu Dashboard de Digitalocean, ahora podrás eliminarlas al terminar la práctica.

(Para borrar los droplets)
````
ansible-playbook -i inventory destroy_droplet.yml
````



- Shanky
