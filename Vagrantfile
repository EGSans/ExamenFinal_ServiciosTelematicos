Vagrant.configure("2") do |config|
  # Imagen base de Ubuntu 22.04
  config.vm.box = "ubuntu/jammy64"

  config.vm.hostname = "cloudnova-devops"

  # Red privada (opcional)
  config.vm.network "private_network", ip: "192.168.56.10"

  # Reenvío de puertos
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 8443

  # Recursos de la VM
  config.vm.provider "virtualbox" do |vb|
    vb.name = "cloudnova-devops"
    vb.memory = 2048
    vb.cpus = 2
  end

  # Provisioning: instalar Docker, git, etc.
  config.vm.provision "shell", inline: <<-SHELL
    # Actualizar paquetes
    apt-get update -y
    apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release git

    # Repositorio oficial de Docker
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
      gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

    echo \
      "deb [arch=$(dpkg --print-architecture) \
      signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
      https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" \
      > /etc/apt/sources.list.d/docker.list

    apt-get update -y
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin

    # Dar permisos al usuario vagrant para usar docker sin sudo
    usermod -aG docker vagrant

    systemctl enable docker
    systemctl start docker
  SHELL
end
