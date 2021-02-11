# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<ENDSCRIPT
  sudo yum install -y epel-release
  sudo yum -y update
  sudo yum make cache
  sudo yum install -y net-tools
  sudo yum install -y wget
  YOURPORT=8080
  PERM="--permanent"
  SERV="$PERM --service=jenkins"
  
  firewall-cmd $PERM --new-service=jenkins
  firewall-cmd $SERV --set-short="Jenkins ports"
  firewall-cmd $SERV --set-description="Jenkins port exceptions"
  firewall-cmd $SERV --add-port=$YOURPORT/tcp
  firewall-cmd $PERM --add-service=jenkins
  firewall-cmd --zone=public --add-service=http --permanent
  firewall-cmd --reload

  sudo dnf install java-1.8.0-openjdk-devel
  sudo wget –O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
  sudo rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
  sudo yum install -y jenkins java-1.8.0-openjdk-devel
  sudo systemctl daemon-reload
  sudo systemctl start jenkins
  sudo systemctl enable jenkins

  sudo yum check-update
  curl -fsSL https://get.docker.com/ | sh
  sudo systemctl enable docker
  sudo systemctl start docker
  
  sudo usermod -aG docker jenkins
  sudo chmod 666 /var/run/docker.sock

  sudo yum install python3-pip -y
  sudo pip3 install -U pytest

  sudo yum install -y git


ENDSCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/8"
  config.vm.network "forwarded_port", guest: 8080, host: 8888
  config.vm.provision "shell", inline: $script
end
