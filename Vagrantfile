Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "dockerdevbox"
  config.vm.network "private_network", ip: "192.168.10.101"
  config.vm.network "forwarded_port", guest: 5432, host: 5432, guest_ip: "localhost", id: "postgres"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "dockerdevbox"
    vb.memory = 2048
    vb.cpus = 2
  end
  config.vm.provision "shell", inline: <<-SHELL
    wget -qO- https://get.docker.com/ | sh
    usermod -aG docker vagrant
    mkdir /etc/systemd/system/docker.service.d
    echo "[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H unix:// -H tcp://0.0.0.0:2375" > /etc/systemd/system/docker.service.d/override.conf
    systemctl daemon-reload
    systemctl restart docker.service
    # starting commonly used containers
    docker run -p 5432:5432 --restart unless-stopped --name postgres -e POSTGRES_USER=user -e POSTGRES_PASSWORD=pass -d postgres
  SHELL
end