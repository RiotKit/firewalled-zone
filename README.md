hop-node
========

Ansible playbook for creating proxy nodes, secure networks with double firewalls behind internal networks.

Example configuration: one node on every level
----------------------------------------------

### exit-node-1

```yaml
node_role: exit
wg_internal_ip: 10.223.0.1
peers:
    - name: firewall-node-1
```

### firewall-node-1

```yaml
node_role: firewall
wg_internal_ip: 10.223.0.2
peers:
    - name: exit-node-1
      externalIp: 1.2.3.4
    - name: internal-node-1
```

### internal-node-1

```yaml
node_role: internal
wg_internal_ip: 10.223.0.3
peers:
    - name: firewall-node-1
      externalIp: 5.4.3.2
```
