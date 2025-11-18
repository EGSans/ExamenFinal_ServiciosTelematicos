# ExamenFinal_ServiciosTelematicos
Este repositorio contiene toda la infraestructura, configuración, scripts, dashboards y evidencias utilizadas para completar el Examen Final de Servicios Telemáticos.
El objetivo fue desplegar, asegurar, monitorear y visualizar una aplicación web usando Docker, Nginx, Vagrant, AWS EC2, Prometheus, Node Exporter y Grafana.


Contenido del repositorio:

<img width="694" height="570" alt="image" src="https://github.com/user-attachments/assets/0ede040e-e8b3-4a0f-b893-6a90fca4f376" />


1. Empaquetado y despliegue local con Docker + Nginx + SSL + Vagrant

1.1 Clonar el repositorio
git clone https://github.com/EGSans/ExamenFinal_ServiciosTelematicos.git


1.2 Levantar la VM con vagrant
Ejecutar el siguiente comando en la misma ruta del proyect donde se encuentra el Vagrantfile:
vagrant up

Una vez termine de levantar la máquina vagrant podemos acceder a esta mediante:

vagrant ssh 

En el hipervisor de VirtualBox podremos ver la siguiente máquina que corresponde a la que acabamos de levantar

<img width="569" height="81" alt="image" src="https://github.com/user-attachments/assets/87cbdbdc-40a8-4722-9dc0-e8c3be39bc9a" />




1.3 Construir y ejecutar los contenedores

Una vez dentro de la máquina virtual accedemos a la ruta de nuestro proyecto para levantar los contenedores

cd /vagrant/MiniWebApp

docker compose build ( crea las imágenes de los contenedores)

docker compose up -d (levanta los contenedores con las imágenes previamente creadas)

1.4 Acceso desde el navegador (host)

http://localhost:8080 (como tenemos configurada la redirección de http a https en nuestro archivo nginx/default.conf nos enviará directamente a nuestro sitio en el puerto 8443)
https://localhost:8443 (nuestro sitio https con certificado SSL autofirmado)


<img width="1912" height="982" alt="image" src="https://github.com/user-attachments/assets/41806402-50fd-4459-925a-7f40dfa0d469" />


<img width="693" height="812" alt="image" src="https://github.com/user-attachments/assets/0704978e-3051-4eb0-b47a-aad85d53cbaa" />






2. Despliegue en AWS EC2

   Para este punto se levantó una instancia en AWS con las siguientes características:

   Tipo:t3.micro
   Sistema: Ubuntu 22.04
   Reglas de entrada (necesarias para el desarrollo de los puntos 2,3 y 4):

   <img width="973" height="238" alt="image" src="https://github.com/user-attachments/assets/9f531651-a131-4c9c-999d-bf044a836ec6" />









