
* Install openstack using devstack
* create ubuntu16.04 image in glance 
  https://computingforgeeks.com/adding-images-openstack-glance/
* Create security groups
* launch instance with private n/w and associate a floating IP
* launch instance with ubuntu 16.04 image creating a keypair
* login the openstack vm with keypair 
  ssh -i my-key.pem ubuntu@172.24.4.5
  
 # Prepare vm to install kubernetes and cloud provider openstack
 
 * Install go  
   wget https://dl.google.com/go/go1.10.3.linux-amd64.tar.gz  
   sudo tar -xvf go1.10.3.linux-amd64.tar.gz 
   sudo mv go /usr/local/ 
 
 * Edit the /etc/environment file 
   GOPATH=/home/ubuntu/go 
   PATH=/usr/local/go/bin:/home/ubuntu/go/bin  
   
 * Install docker  
   sudo apt-get install apt-transport-https ca-certificates curl software-properties-common  
   sudo apt-key fingerprint 0EBFCD88  
   sudo apt-get update
   sudo apt-get install docker-ce  
   sudo usermod -aG docker $USER  
   sed -i '/^ExecStart=\/usr\/bin\/dockerd$/ s/$/ --exec-opt native.cgroupdriver=systemd/' /lib/systemd/system/docker.service  
   sudo systemctl daemon-reload  
   sudo systemctl enable docker  
   sudo systemctl start docker  
   
 * Install make, git,  gcc, dep  
   sudo apt-get install git gcc make python-pip  
   curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh  
   
 * mkdir /home/ubuntu/go/src  
   mkdir /home/ubuntu/go/src/k8s.io  
   cd /home/ubuntu/go/src/k8s.io/  
   git clone https://github.com/adisky/cloud-provider-openstack.git  
   git clone https://github.com/kubernetes/kubernetes  



  
