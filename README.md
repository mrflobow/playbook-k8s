# playbook-k8s
Ansible Playbook for setting up K8s Cluster

## Requirements
* Ansible 10
* Debian 12 (tested , others may work)

## Nodenames
Make sure hostnames are set for the nodes. Ideally full qualified domain name.
If you have a local dns server add the names to it. 
The nodes should be able to resolve the hostnames.
Name the nodes with fqdn names. See sample-nodes example file.

```bash
sudo hostnamectl set-hostname k8s-control.mydomain.com
```

## Configuration Variable Overrides

| Name | Default Value | Description |
| --- | --- | --- |
| k8s_mgmt_user | mrflobow | User on control node , you use to run command kubectl |


## Manual steps

Proceed with the manual steps after ansible playbook completed successfully.

### Check

Check if everything is working on control node.

```bash
kubectl get nodes
```

### Control Node install network plugin
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.0/manifests/calico.yaml
```

### Join Worker Nodes

Get the join command 

```bash
kubeadm token create --print-join-command
```

Use the response command with sudo on eacht worker node.

## Run ansible

```bash
ansible-playbook k8s.yml -i <inventoryfile>
```