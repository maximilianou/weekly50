# weekly50
# gitops kubernetes

[![GitOps Continuous Delivery on Kubernetes with Flux lfs269 Certificate, Linux Fundation](https://github.com/maximilianou/weekly50/blob/main/share/maximiliano-usich-gitops-continuous-delivery-on-kubernetes-with-flux-lfs269-certificate.png?raw=true)](https://github.com/maximilianou/weekly50/blob/main/share/maximiliano-usich-gitops-continuous-delivery-on-kubernetes-with-flux-lfs269-certificate.png?raw=true)

<https://ti-user-certificates.s3.amazonaws.com/e0df7fbf-a057-42af-8a1f-590912be5460/3499b883-e4e1-41cf-8487-1553fdd33103-maximiliano-usich-gitops-continuous-delivery-on-kubernetes-with-flux-lfs269-certificate.pdf>

#### Typescript TDD jest ts-jest base project reference:
<https://github.com/mtiller/ts-jest-sample/>

#### CI - Continuous Integration Kubernete Native Tool
<https://tekton.dev/>

#### CD - Continuous Deploy Kubernetes Native Tool
<https://fluxcd.io/>

<https://github.com/fluxcd/flux2-multi-tenancy>

#### CD - Continuous Delivery Kubernetes Native Tool - Blue/Green - Canary
<https://flagger.app/>

### Kubernetes Linux Fundation learning path, now lxd lxc to run localhost containers/virtual machines

```
lxc image list images: debian
lxc image list images: debian/11

lxc launch images:debian/11 master2 --vm
lxc launch images:debian/11 worker1 --vm
lxc launch images:debian/11 worker2 --vm

lxc list
+---------+---------+-------------------------+------+-----------------+-----------+
|  NAME   |  STATE  |          IPV4           | IPV6 |      TYPE       | SNAPSHOTS |
+---------+---------+-------------------------+------+-----------------+-----------+
| master2 | RUNNING | 172.17.0.1 (docker0)    |      | VIRTUAL-MACHINE | 0         |
|         |         | 10.249.240.82 (enp5s0)  |      |                 |           |
+---------+---------+-------------------------+------+-----------------+-----------+
| worker1 | RUNNING | 10.249.240.77 (enp5s0)  |      | VIRTUAL-MACHINE | 0         |
+---------+---------+-------------------------+------+-----------------+-----------+
| worker2 | RUNNING | 10.249.240.239 (enp5s0) |      | VIRTUAL-MACHINE | 0         |
+---------+---------+-------------------------+------+-----------------+-----------+

lxc exec worker1 bash
  ping worker2.lxd
  adduser dev-user
  apt install openssh-server

ssh dev-user@10.249.240.77
###############################
```

- Kubernetes Architecture
  - kubectl ( API call curl )
  - control plane ( cp ) nodes
    - kubelet
    - kube-proxy
    - kube-apiserver
    - kube-scheduller
    - etcd
    - kube-controller-manager
    - cloud-controller-manager
  - worker nodes
    - kubelet
    - kube-proxy
    - docker/cri-o
    - iptables/ipvs

<https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/>
```
  root@master:~# apt install -y apt-transport-https ca-certificates curl

  root@master:~# curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

  root@master:~# echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" |  tee /etc/apt/sources.list.d/kubernetes.list

  root@master:~# apt -y update; apt -y install kubelet kubeadm kubectl;

  root@master:~# apt-mark hold kubelet kubeadm kubectl
kubelet set on hold.
kubeadm set on hold.
kubectl set on hold.

# The kubelet is now restarting every few seconds, as it waits in a crashloop for kubeadm to tell it what to do.

```

```
# kubeadm Upgrade Version
  apt-get update && \
  apt-get install -y --allow-change-held-packages kubeadm=1.22.x-00

  kubeadm version

  kubeadm upgrade plan

  kubeadm upgrade apply v1.22.x
```

```
# kubectl Upgrade Version
  apt-get update && \
  apt-get install -y --allow-change-held-packages kubelet=1.22.x-00 kubectl=1.22.x-00
    
  systemctl daemon-reload
  systemctl restart kubelet

  kubectl uncordon <node-to-drain>

  kubectl get nodes

```

```
# docker - install in master
	apt -y install apt-transport-https software-properties-common ca-certificates curl gnupg lsb-release; echo  'deb [arch=amd64] https://download.docker.com/linux/debian  bullseye stable' | tee /etc/apt/sources.list.d/docker.list > /dev/null ;  curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - ; add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian bullseye stable" ; apt -y update; apt -y remove docker docker-engine docker.io containerd runc; apt -y install docker-ce docker-ce-cli containerd.io;
	## add dev-user in /etc/group docker:998:dev-user

   dev-user@master:~$ docker run --rm gcr.io/google_containers/hyperkube:v1.18.6  kube-apiserver --help

   docker run --rm gcr.io/google_containers/hyperkube:v1.18.6 kube-scheduler --help

   docker run --rm gcr.io/google_containers/hyperkube:v1.18.6 kube-controller-manager --help
   
```

```
  root@master2:~# kubeadm init --ignore-preflight-errors=all

  root@worker1:~# kubeadm join 10.249.240.82:6443 --token fgilf3.9szn56gv8v6spm3w \
	--discovery-token-ca-cert-hash sha256:45eca92addd6789cdef90b0d965b93d7252a8270e0602de01124ef6813cdf56e

  root@worker2:~# kubeadm join 10.249.240.82:6443 --token fgilf3.9szn56gv8v6spm3w \
	--discovery-token-ca-cert-hash sha256:45eca92addd6789cdef90b0d965b93d7252a8270e0602de01124ef6813cdf56e

  root@master2:~# cat /etc/kubernetes/admin.conf \
                      > ~/.kube/config
```


```

```
