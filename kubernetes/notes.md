Bought: Udemy - From zero to a full Kubernetes environment including apps and monitoring

local setup:
using rancher desktop
runs its own virtual machine
runs the cluster inside it, named `rancher-desktop`
puts the configuration in $HOME/.kube/cofig
had to manually install kubectl (cli to interact with the cluster) and k9s (a cool terminal utility to check the cluster)

alias k='kubectl' for ease of use

what is Kubernetes? - operating system of the cloud, handles running large compute of multiple virtual machines mostly by itself

kubernetes manages clusters (everything we deploy will be within a cluster)
a cluster contains one or more control planes (if multiple how does the etc is in sync???)

control plane has:
    - etcd (a fast key value data store) (brain of the cluster)
    - scheduler (the one provisions the pods, this decides which worker node to put the pod into)
    - api server (kubectl interacts with this api server to do stuff, it knows the url from $HOME/.kube/config)
    - controller manager (monitors the state of the clusters, and something else :-)

cluster contains the worker nodes - virtual machine or physical machine, it has
    - kubelet - the one which keeps the control plane informed
    - container runtime - to run the containers obviously (containerd or dockerd)
    - a network proxy

within nodes we have pods, pods are the smallest running resource inside kubernetes
pods have associated network and storage blocks.

pods can run one or more containers
containers are individual processes that we deploy

eg: we can deploy a nodejs application and a postgres database together into a single pod
so they can communicate via localhost, or we can put them in separate pods and they should
communicate using the network labels (not completely sure how this works and where its resoluted)

the standard is to run one container per pod

