[简体中文](https://sealyun.com/post/sealos/)

build a production kubernetes cluster

# Features
- [x] support etcd cluster and TLS, using static pod to init etcd cluster, so monitor and management will be easy
- [x] kubernetes master cluster
- [x] calico etcd TLS, calico using etcd cluster
- [x] dashboard, heapster coreDNS addons
- [x] master haproxy, using static pod
- [x] master keepalived
- [x] join nodes, change kube-proxy configmap, change kubelet config
- [x] promethus support, using promethus operator
- [x] [istio support](https://sealyun.com/pro/istio/)

# ship on docker
## you need already has [sealyun offline package](https://sealyun.com/pro/products/) 
copy it to `/data` dir 
```
docker run --rm -v /data/kube1.13.0.tar.gz:/data/kube1.13.0.tar.gz -it -w /etc/ansible fanux/sealos:v1.13.0 bash
```

generate ssh public key (in docker):
```
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen -t rsa -b 2048 # please click "Enter" to end
ssh-copy-id $IP # $IP is the virtual machine or machine ip address. 
```
check:
``` 
ssh $IP
```

# install all
Config your own hosts
```
# cd /etc/ansible
# vim hosts
```

```
# ansible-playbook roles/install-all.yaml
```

# uninstall all
```
# ansible-playbook roles/uninstall-all.yaml
```

# version support
| | kubernetes v1.12| kubernetes v1.13|
|--- | --- |--- |
| sealos v1.0.0| ✓ ||
| sealos v1.13.0| |✓|

# 公众号：
![sealyun](https://sealyun.com/kubernetes-qrcode.jpg)
