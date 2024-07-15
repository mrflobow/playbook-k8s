# playbook-k8s
Ansible Playbook for setting up K8s Cluster

## Requirements
* Ansible 10
* Debian 12 (tested , others may work)

## Nodenames

Name the nodes with fqdn names. See sample-nodes example file.

## Manual steps

Proceed with the manual steps after ansible playbook completed successfully.

### Check

Check if everything is working on control node.

```bash
kubectl get nodes
````

### Control Node install network plugin
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.0/manifests/calico.yaml
```

### Join Worker Nodes
```bash
kubeadm token create --print-join-command
```