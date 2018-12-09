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

kubeadm config images list --kubernetes-version=v1.12.2
k8s.gcr.io/kube-apiserver:v1.12.2
k8s.gcr.io/kube-controller-manager:v1.12.2
k8s.gcr.io/kube-scheduler:v1.12.2
k8s.gcr.io/kube-proxy:v1.12.2
k8s.gcr.io/pause:3.1
k8s.gcr.io/etcd:3.2.24
k8s.gcr.io/coredns:1.2.2

kubeadm config images list --kubernetes-version=v1.12.2 --config=./config.yaml
docker.io/kubernetes1122/kube-apiserver:v1.12.2
docker.io/kubernetes1122/kube-controller-manager:v1.12.2
docker.io/kubernetes1122/kube-scheduler:v1.12.2
docker.io/kubernetes1122/kube-proxy:v1.12.2
docker.io/kubernetes1122/pause:3.1
docker.io/kubernetes1122/etcd:3.2.24
docker.io/kubernetes1122/coredns:1.2.2



http://www.cnblogs.com/RainingNight/p/using-kubeadm-to-create-a-cluster-1-12.html

sudo kubeadm init --config=./config.yaml

The list of validated docker versions was updated to 1.11.1, 1.12.1, 1.13.1, 17.03, 17.06, 17.09, 18.06. (#68495)
https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG-1.12.md#deprecations-and-removals



sudo kubeadm init --config=./config.yaml
[sudo] password for dc: 
[config] WARNING: Ignored YAML document with GroupVersionKind kubeadm.k8s.io/v1alpha3, Kind=JoinConfiguration
[init] using Kubernetes version: v1.12.2
[preflight] running pre-flight checks
[preflight/images] Pulling images required for setting up a Kubernetes cluster
[preflight/images] This might take a minute or two, depending on the speed of your internet connection
[preflight/images] You can also perform this action in beforehand using 'kubeadm config images pull'
[kubelet] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
[kubelet] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
[preflight] Activating the kubelet service
[certificates] Generated etcd/ca certificate and key.
[certificates] Generated etcd/peer certificate and key.
[certificates] etcd/peer serving cert is signed for DNS names [k8s-master localhost] and IPs [192.168.137.238 127.0.0.1 ::1]
[certificates] Generated etcd/healthcheck-client certificate and key.
[certificates] Generated apiserver-etcd-client certificate and key.
[certificates] Generated etcd/server certificate and key.
[certificates] etcd/server serving cert is signed for DNS names [k8s-master localhost] and IPs [127.0.0.1 ::1]
[certificates] Generated ca certificate and key.
[certificates] Generated apiserver-kubelet-client certificate and key.
[certificates] Generated apiserver certificate and key.
[certificates] apiserver serving cert is signed for DNS names [k8s-master kubernetes kubernetes.default kubernetes.default.svc kubernetes.default.svc.cluster.local] and IPs [10.96.0.1 192.168.137.238]
[certificates] Generated front-proxy-ca certificate and key.
[certificates] Generated front-proxy-client certificate and key.
[certificates] valid certificates and keys now exist in "/etc/kubernetes/pki"
[certificates] Generated sa key and public key.
[kubeconfig] Wrote KubeConfig file to disk: "/etc/kubernetes/admin.conf"
[kubeconfig] Wrote KubeConfig file to disk: "/etc/kubernetes/kubelet.conf"
[kubeconfig] Wrote KubeConfig file to disk: "/etc/kubernetes/controller-manager.conf"
[kubeconfig] Wrote KubeConfig file to disk: "/etc/kubernetes/scheduler.conf"
[controlplane] wrote Static Pod manifest for component kube-apiserver to "/etc/kubernetes/manifests/kube-apiserver.yaml"
[controlplane] wrote Static Pod manifest for component kube-controller-manager to "/etc/kubernetes/manifests/kube-controller-manager.yaml"
[controlplane] wrote Static Pod manifest for component kube-scheduler to "/etc/kubernetes/manifests/kube-scheduler.yaml"
[etcd] Wrote Static Pod manifest for a local etcd instance to "/etc/kubernetes/manifests/etcd.yaml"
[init] waiting for the kubelet to boot up the control plane as Static Pods from directory "/etc/kubernetes/manifests" 
[init] this might take a minute or longer if the control plane images have to be pulled

Unfortunately, an error has occurred:
	timed out waiting for the condition

This error is likely caused by:
	- The kubelet is not running
	- The kubelet is unhealthy due to a misconfiguration of the node in some way (required cgroups disabled)

If you are on a systemd-powered system, you can try to troubleshoot the error with the following commands:
	- 'systemctl status kubelet'
	- 'journalctl -xeu kubelet'

Additionally, a control plane component may have crashed or exited when started by the container runtime.
To troubleshoot, list all containers using your preferred container runtimes CLI, e.g. docker.
Here is one example how you may list all Kubernetes containers running in docker:
	- 'docker ps -a | grep kube | grep -v pause'
	Once you have found the failing container, you can inspect its logs with:
	- 'docker logs CONTAINERID'
couldn't initialize a Kubernetes cluster



。。。。。
[init] this might take a minute or longer if the control plane images have to be pulled
[apiclient] All control plane components are healthy after 22.501779 seconds
[uploadconfig] storing the configuration used in ConfigMap "kubeadm-config" in the "kube-system" Namespace
[kubelet] Creating a ConfigMap "kubelet-config-1.12" in namespace kube-system with the configuration for the kubelets in the cluster
[markmaster] Marking the node k8s-master as master by adding the label "node-role.kubernetes.io/master=''"
[markmaster] Marking the node k8s-master as master by adding the taints [node-role.kubernetes.io/master:NoSchedule]
[patchnode] Uploading the CRI Socket information "/var/run/dockershim.sock" to the Node API object "k8s-master" as an annotation
[bootstraptoken] using token: 9lno0t.othyl6uvkto9vmcn
[bootstraptoken] configured RBAC rules to allow Node Bootstrap tokens to post CSRs in order for nodes to get long term certificate credentials
[bootstraptoken] configured RBAC rules to allow the csrapprover controller automatically approve CSRs from a Node Bootstrap Token
[bootstraptoken] configured RBAC rules to allow certificate rotation for all node client certificates in the cluster
[bootstraptoken] creating the "cluster-info" ConfigMap in the "kube-public" namespace
[addons] Applied essential addon: CoreDNS
[addons] Applied essential addon: kube-proxy

Your Kubernetes master has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:

  kubeadm join 192.168.137.238:6443 --token 9lno0t.othyl6uvkto9vmcn --discovery-token-ca-cert-hash sha256:12bf04b6bd790b66aafb83bfb9a26b68563a009a3317e65961309cde18945508

