# Option 1 (Best for Practical): Local Private Cloud using VirtualBox + OpenStack (DevStack)
🔹 Tools (All Free)
Oracle VM VirtualBox
OpenStack (via DevStack)
## What you achieve
Your own private cloud environment
Create VMs (instances) like AWS EC2
Manage networks, storage, images
## Steps (Simplified for Practical)
1. Install VirtualBox

Download and install:

Oracle VM VirtualBox
2. Create Ubuntu VM
RAM: 4 GB (minimum 2 GB)
Storage: 20–30 GB
Install Ubuntu
3. Install DevStack (OpenStack)

Inside VM:

sudo apt update
sudo apt install git -y
git clone https://opendev.org/openstack/devstack
cd devstack

Create config:

nano local.conf

Paste:

[[local|localrc]]
ADMIN_PASSWORD=admin
DATABASE_PASSWORD=admin
RABBIT_PASSWORD=admin
SERVICE_PASSWORD=admin

Run:

./stack.sh
4. Access Dashboard

After install, open:

http://<vm-ip>/dashboard

Login:

username: admin
password: admin
5. Perform in Exam
Launch instance (VM)
Create network
Upload image
### What to say
“This is a private cloud using OpenStack”
“It provides IaaS like AWS EC2”
“We can create and manage virtual machines”
# Option 2 (Lightweight & Easy): Minikube (Local Cloud-like Kubernetes)
🔹 Tool
Minikube
Steps:
sudo apt install docker.io -y
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube start
kubectl get nodes
What you show
Container orchestration (cloud-native apps)
### What to say
“Simulates cloud container environment”
“Used for scalable deployments”
# Option 3 (Easiest for Marks): OwnCloud / Nextcloud (Private Cloud Storage)
🔹 Tool
Nextcloud
Install:
sudo apt install snapd -y
sudo snap install nextcloud

Open:

http://localhost
What you show
File upload/download like Google Drive