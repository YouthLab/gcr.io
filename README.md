# gcr.io
docker lib 4 kubeadm


https://dl.k8s.io/release/stable-1.12.txt

https://opsx.alibaba.com/mirror

kubernetes
Debian / Ubuntu
apt-get update && apt-get install -y apt-transport-https
curl https://mirrors.aliyun.com/kubernetes/apt/doc/apt-key.gpg | apt-key add - 
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://mirrors.aliyun.com/kubernetes/apt/ kubernetes-xenial main
EOF  
apt-get update
apt-get install -y kubelet kubeadm kubectl




https://blog.csdn.net/yjf147369/article/details/80290881
https://github.com/anjia0532/gcr.io_mirror


$ kubeadm config images list --kubernetes-version=v1.11.4
k8s.gcr.io/kube-apiserver:v1.11.4
k8s.gcr.io/kube-controller-manager:v1.11.4
k8s.gcr.io/kube-scheduler:v1.11.4
k8s.gcr.io/kube-proxy:v1.11.4
k8s.gcr.io/pause:3.1
k8s.gcr.io/etcd:3.2.18
k8s.gcr.io/coredns:1.2.2
