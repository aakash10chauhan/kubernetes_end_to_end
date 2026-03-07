---

# Amazon EKS (Elastic Kubernetes Service)

## What is Amazon EKS?

Amazon **EKS (Elastic Kubernetes Service)** is a **managed Kubernetes service** provided by AWS.
It allows you to run Kubernetes clusters on AWS **without managing the Kubernetes control plane**.

EKS uses **upstream Kubernetes**, which means standard Kubernetes YAML manifests and tools (like `kubectl` and Helm) work without modification.

---

## Control Plane Managed by AWS

In Amazon EKS, the **Kubernetes control plane** is fully managed by AWS.

AWS manages:

* Kubernetes API Server
* Scheduler
* Controller Manager
* etcd
* High availability across multiple Availability Zones
* Security patches and version upgrades

👉 You **do not manage or see** the control plane nodes.

---

## Worker Nodes in EKS

EKS worker nodes can be run using:
can be setup using 3 way 

* **Amazon EC2** (Managed or Self-managed node groups)
* **AWS Fargate** (Serverless, no node management)

self-managed nodes 
users must provision manually EC2 instances 
installed >kubelet >>kube proxy >>c runtime 


managed node group 
aws managed everthing 
>>easy to maage creted update delete
>>managed by using autoscalling groups 

fargae 

follows serverless structure 



steps to perform the practicals 
lets start guys 

connect your ec2 instance ubuntu 


we need to install  aws cli, kubectl ,
sudo apt update 

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install -i /usr/local/aws-cli -b /usr/local/bin --update

sudo apt-get update
sudo apt install docker.io
docker ps
sudo chown $USER /var/run/docker.sock

Install kubectl

curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client



Install eksctl

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version


