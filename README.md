https://medium.com/avmconsulting-blog/ci-cd-with-kubernetes-minikube-6e9e0b2150b2

Install Docker on Linux
++++++++++++++++++++++++

sudo apt-get update curl -fsSL https://get.docker.com/ | s

sudo usermod -aG docker $USER

When you’re all done, make sure Docker is running:

sudo service docker start


Install Minikube and Kubectl
++++++++++++++++++++++++++++++

curl -LO ​ https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/


curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh; chmod 700 get_helm.sh; ./get_helm.sh

minikube stop; minikube delete; sudo rm -rf ~/.minikube; sudo rm -rf ~/.kub

1. Startup the Kubernetes cluster with Minikube, giving it some extra resources.

minikube start --memory 8000 --cpus 2 --kubernetes-version v1.6.0

2. Enable the Minikube add-ons Heapster and Ingress.
minikube addons enable heapster; minikube addons enable ingress

Inspect the pods in the cluster. You should see the add-ons hipster, influxdb-grafana, and Nginx-ingress-controller.

kubectl get pods --all-namespaces


kubectl get pods -n kube-system | grep 'NAME\|ingress'

kubectl create deployment nginx-demo --image=nginxdemos/hello

kubectl get deployment

kubectl expose deployment nginx-demo --port=80

kubectl apply -f ingress.yml

kubectl get ingress