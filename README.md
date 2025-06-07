# Configuring Nginx Load Balancer with Ansible

The playbook automates the installation and configuration of Nginx load balancer.

## Step 1: Setting Up the Inventory File

Create an inventory file to define the hosts (target machine). The following example shows how to configure the target machine IP:

```yaml
---
loadBalancer:
  hosts:
    loadBalancer01:
      ansible_host: <load-balancer-ip>
      ansible_user: ubuntu
webApps:
  hosts:
    webApps01:
      ansible_host: <web-app-01-ip>
      ansible_user: ubuntu
    webApps02:
      ansible_host: <web-app-02-ip>
      ansible_user: ubuntu
    webApps03:
      ansible_host: <web-app-03-ip>
      ansible_user: ubuntu
all:
  children:
    loadBalancer:
    webApps:
      
      
```
## Step 2: Run Playbook

Run the playbook with this command:
```
ansible-playbook -i inventories/hosts.yml --private-key <your-private-key> playbook.yml
```

## How to Test

To test it, simply run this command:
```
curl -kv https://<load-balancer-ip>
```