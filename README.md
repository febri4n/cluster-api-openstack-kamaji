# cluster-api-openstack-kamaji
Cluster API OpenStack with Kamaji Control Plane Provider

Sebelum mencoba CAPI OpenStack Kamaji, pastikan:
1. Kamaji berjalan, test dahulu dengan membuat tenant. Disini kamaji menggunakan OCCM dan octavia sebagai service nya.
2. Cluster API berjalan, test juga dengan membuat 1 buat cluster. Disini CAPI tidak menggunakan OCCM, dia akan menggunakan clouds.yaml dan pastikan gunakan application credentials dibandingkan menggunakan username/password. Dibawah env saya masukan di bashrc, atau bisa dengan membuat file
```bash vim ~/.bashrc
export KUBECONFIG=/home/ubuntu/.kube/config
export CLUSTER_TOPOLOGY=true
export OPENSTACK_DNS_NAMESERVERS="8.8.8.8"
export OPENSTACK_FAILURE_DOMAIN="AZ_Public01_JBBK"
export OPENSTACK_CONTROL_PLANE_MACHINE_FLAVOR="GP.2C4G-intel"
export OPENSTACK_NODE_MACHINE_FLAVOR="GP.2C4G-intel"
export OPENSTACK_IMAGE_NAME="capi-ubuntu-2204-kube-v1.30.2"
export OPENSTACK_SSH_KEY_NAME="febri4n"
export OPENSTACK_EXTERNAL_NETWORK_ID=f9881508-7de0-488e-a4ff-c437f4c8687f
export KUBERNETES_VERSION="v1.30.2"
```
```bash
wget https://raw.githubusercontent.com/kubernetes-sigs/cluster-api-provider-openstack/master/templates/env.rc -O /tmp/env.rc
source /tmp/env.rc clouds.yaml openstack
```
3. Jika CAPI dan Kamaji sudah berjalan, maka bisa mencoba CAPI OpenStack Kamaji