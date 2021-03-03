Please follow the live [document](https://docs.google.com/document/d/17OwlITE-yPWNj3Vi5RtQfz3ItvSkOfnbaVMnzlZyGTg)

Ubuntu 20.04 VM

Install docker 

sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - 

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \ stable"
   
sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo chmod 666 /var/run/docker.sock


Install kubectl 

$ sudo curl -L "https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl" -o /usr/local/bin/kubectl
$ sudo chmod +x /usr/local/bin/kubectl
$ kubectl version --short --client

Install Terraform

curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -  
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"  
sudo apt-get update && sudo apt-get install terraform
terraform –version

Install Kind

curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.10.0/kind-linux-amd64  
chmod +x ./kind  
sudo mv ./kind /usr/local/bin

Create cluster


$ kind create cluster --name app --config kind-config.yaml
$ kind get cluster
$ kubectl cluster-info --context kind-app
$ terraform init
$ terraform apply
$ kubectl get all –all-namespaces
$ terraform destroy
