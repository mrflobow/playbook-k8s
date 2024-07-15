# playbook-k8s
Ansible Playbook for setting up K8s Cluster

## Requirements
* Ansible 10
* Debian 12 (tested , others may work)

## Manual steps

Proceed with the manual steps after ansible playbook completed successfully.

### Check

Check if everything is working on control node.

```bash
kubectl get node
````

### Control Node install network plugin
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml
```

### Join Worker Nodes
```bash
kubeadm token create --print-join-command
```