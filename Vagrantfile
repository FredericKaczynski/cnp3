# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "hashicorp/precise32"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y python-sphinx
     sudo apt-get install -y make
     sudo apt-get install -y python-setuptools
     sudo apt-get install -y mscgen
     sudo apt-get install -y graphviz
     sudo apt-get install -y texlive
     sudo apt-get install -y texlive-pictures
     sudo apt-get install texlive-latex-extra
     sudo apt-get install dvipng
     sudo apt-get install texlive-fonts-recommended
     sudo apt-get install -y poppler-utils
     sudo apt-get install -y inkscape
     sudo easy_install -U sphinxcontrib-mscgen
     sudo easy_install -U sphinxcontrib-tikz
     # for tikz
     sudo apt-get install netpbm
     # need standalone.cls that is not in texlive :-(
     sudo -u vagrant wget  -q http://mirrors.ctan.org/install/macros/latex/contrib/standalone.tds.zip -O /tmp/standalone.tds.zip
     sudo -u vagrant wget -q http://mirrors.ctan.org/macros/latex/contrib/titlesec.zip	-O /tmp/titlesec.zip
     sudo -u vagrant wget -q http://mirrors.ctan.org/macros/latex/contrib/wrapfig.zip -O /tmp/wrapfig.zip
     sudo mkdir /usr/share/texmf-texlive/tex/latex/needspace
     sudo wget -q http://ftp.rz.uni-wuerzburg.de/pub/tex/latex2e/contrib/misc/needspace.sty -O /usr/share/texmf-texlive/tex/latex/needspace/needspace.sty
     sudo -u vagrant wget -q http://mirrors.ctan.org/macros/latex/contrib/multirow.zip -O /tmp/multirow.zip	
     sudo apt-get install unzip
     sudo unzip -u /tmp/standalone.tds.zip -d /usr/share/texmf-texlive/tex/latex
     sudo unzip -u /tmp/titlesec.zip -d /usr/share/texmf-texlive/tex/latex
     sudo unzip -u /tmp/wrapfig.zip -d /usr/share/texmf-texlive/tex/latex
     sudo unzip -u /tmp/multirow.zip -d /usr/share/texmf-texlive/tex/latex
     sudo texhash 
     # fix epstopdf which is broken
     sudo sed -i -e '1i#!/usr/bin/perl\' /usr/share/texmf-texlive/scripts/epstopdf/epstopdf.pl
     SHELL
end
