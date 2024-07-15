# playbook-k8s
Ansible Playbook for setting up K8s Cluster

## Requirements
* Tested with Ansible 10

## Manual steps

### Control Node install network plugin
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml
```

### Join Worker Nodes
```bash
kubeadm token create --print-join-command
```