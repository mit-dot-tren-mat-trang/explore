# Bamboo Firewall

## User Acceptance Testing (UAT) Bamboo Firewall on Rocky linux 9

Repository of the Ansible playbook to install bamboo firewall on Rocky linux for manage and agent nodes: [GitHub - bamboo-firewall-v2/calico-rocky-playbook](https://github.com/bamboo-firewall-v2/calico-rocky-playbook)

### Test environment

- Test environment setup contains 3 servers, all running Rocky linux 9.

![Architect image](./files/Architect.svg)

- Configuration of 3 servers:

| No |  Hostname  |       IP       | Interfaces |    Role    |  Zone | Project |  Namespace |
|:--:|:----------:|:--------------:|:----------:|:----------:|:-----:|:-------:|:----------:|
| 1  | manage-aio | 172.16.194.130 | eth1       | management | gray  | example | production |
| 2  | lb01       | 172.16.194.131 | eth1       | lb01       | white | example | production |
| 3  | app01      | 172.16.194.132 | eth1       | app01      | black | example | production |

- Policies:

| No | IP source      | Port source | IP destination | Destination port | Protocol | Description                                                  |   |
|----|----------------|-------------|----------------|------------------|----------|--------------------------------------------------------------|---|
| 1  | any            | any         | any            | 22               | TCP      | Allow ssh connection to all hosts                            |   |
| 2  | 172.16.194.131 | any         | 172.16.194.132 | [80, 443]        | TCP      | Allow APP to receive HTTP & HTTPS requests from LB           |   |
| 3  | any            | any         | 172.16.194.131 | [80, 443]        | TCP      | Allow LB to receive HTTP & HTTPS requests from outside world |   |

- Bamboo Firewall frontend home

![Adminer home](./files/adminer-home.png)

### Installation

- Ansible playbook tasks:
  - Setup hosts file
  - Update system
  - Install ipset, calico-felix (all hosts)
  - For management hosts
    - Install docker, docker-compose
    - Create config directories and files
    - Copy default schema fille
    - Run docker compose
  
### Apply policies

- GNP
![Adminer GNP](./files/adminer-gnp.png)

- HEP
![Adminer HEP](./files/adminer-hep.png)

- GNS
![Adminer GNS](./files/adminer-gns.png)

### Iptables & ipset record

- iptables records:
  - Allow http & https from anywhere access load balancer
  - Allow send http & https from load balancer to app

![iptables-http](./files/iptables-http.png)

- ipset record:

![ipsetgrep](./files/ipset-grep.png)
![ipset detail](./files/ipset-detail.png)

## Update new version of calico

- Calicoctl version: 3.28.0

![Calicoctl version](./files/calico-version.png)

- Calico felix version: 3.28.0, release file: [pngocthach/calico](https://github.com/pngocthach/calico/releases/download/v0.0.2/calico-felix-amd64.tar.gz)

![Calico felix version](./files/felix-version.png)

- Etcd version: 3.5.14

![Etcd version](./files/etcd-version.png)

### Issues

- Missing libpcap

![Missing libpcap](./files/missing-libpcap.png)

### Result

- All functions run normally
