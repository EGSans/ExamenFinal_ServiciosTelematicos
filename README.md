# ExamenFinal_ServiciosTelematicos
Este repositorio contiene toda la infraestructura, configuración, scripts, dashboards y evidencias utilizadas para completar el Examen Final de Servicios Telemáticos.
El objetivo fue desplegar, asegurar, monitorear y visualizar una aplicación web usando Docker, Nginx, Vagrant, AWS EC2, Prometheus, Node Exporter y Grafana.


Contenido del repositorio:

ExamenFinal_ServiciosTelematicos/
│
├── MiniWebApp/                # Proyecto web empaquetado localmente
│   ├── docker-compose.yml
│   ├── webapp/ (código Python + Flask)
│   ├── nginx/default.conf     # SSL + Reverse Proxy
│   ├── certs/ (certificados SSL)
│   ├── init.sql               # BD inicial
│   ├── script.sh              # Provisión para Vagrant
│   └── Vagrantfile            # Máquina Vagrant para despliegue local
│
├── prometheus/                # Config de monitoreo
│   ├── prometheus.yml
│   ├── alerts.yml
│   └── docker-compose.yml
│
├── grafana/
│   └── dashboards/            # Paneles JSON exportados
│
├── evidencia/                 # Capturas y pruebas del examen
│
├── README.md                  # Este archivo
└── .gitignore


1. Empaquetado y despliegue local con Docker + Nginx + SSL + Vagrant

1.1 Clonar el repositorio
git clone https://github.com/EGSans/ExamenFinal_ServiciosTelematicos.git


1.2 Levantar la VM con vagrant
Ejecutar el siguiente comando en la misma ruta del proyect donde se encuentra el Vagrantfile
vagrant up

Una vez termine de levantar la máquina vagrant podemos acceder a esta mediante
vagrant ssh 

En el hipervisor de VirtualBox podremos ver la siguiente máquina que corresponde a la que acabamos de levantar

<img width="569" height="81" alt="image" src="https://github.com/user-attachments/assets/87cbdbdc-40a8-4722-9dc0-e8c3be39bc9a" />


