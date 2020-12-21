## self-hosted configuration

    ssh to ubuntu vm
    using ubuntu user download and configure runner
    https://github.com/organizations/ventus-ag/settings/actions/add-new-runner?arch=x64&os=linux

    sudo ./svc.sh install
    sudo systemctl start actions.runner.ventus-ag.VMNAME
    sudo systemctl enable actions.runner.ventus-ag.VMNAME
    
    
    sudo apt-get update && sudo apt-get install -y apt-transport-https
    curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
    sudo apt-get update
    sudo apt-get install -y kubectl
    
    
    sudo apt-get update
    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common -y
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo apt-key fingerprint 0EBFCD88
    sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
    sudo apt-get install docker-ce docker-ce-cli containerd.io -y
    sudo usermod -aG docker $USER
    
    sudo reboot
