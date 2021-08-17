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

lxc launch images:debian/11 master
lxc launch images:debian/11 worker1
lxc launch images:debian/11 worker2

lxc list
+---------+---------+-----------------------+------------------------------------------------+-----------+-----------+
|  NAME   |  STATE  |         IPV4          |                      IPV6                      |   TYPE    | SNAPSHOTS |
+---------+---------+-----------------------+------------------------------------------------+-----------+-----------+
| master  | RUNNING | 10.249.240.49 (eth0)  | fd42:e564:aff6:b622:209f:83ff:fe10:dcff (eth0) | CONTAINER | 0         |
+---------+---------+-----------------------+------------------------------------------------+-----------+-----------+
| worker1 | RUNNING | 10.249.240.222 (eth0) | fd42:e564:aff6:b622:216:3eff:fe05:5d7e (eth0)  | CONTAINER | 0         |
+---------+---------+-----------------------+------------------------------------------------+-----------+-----------+
| worker2 | RUNNING | 10.249.240.123 (eth0) | fd42:e564:aff6:b622:216:3eff:fe54:c138 (eth0)  | CONTAINER | 0         |
+---------+---------+-----------------------+------------------------------------------------+-----------+-----------+

lxc exec worker1 bash
  ping worker2.lxd
  adduser dev-user
  apt install openssh-server

ssh dev-user@10.249.240.49
###############################
```

