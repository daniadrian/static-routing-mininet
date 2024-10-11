![image](https://github.com/user-attachments/assets/7581e536-db96-48f3-94a7-59abe2875cb6)# static-routing-mininet

static-routing-mininet is a repository designed to help users learn about networking, from traditional static routing to programmable networks using the Mininet environment. The repository includes a script for setting up static routing between two routers (R1 and R2), demonstrating basic IP forwarding and routing principles.

## Requirements
To get started, you'll need to install Mininet on your WSL. Follow these steps to install Mininet:

1.  Clone the Mininet repository to your local machine :
```bash
git clone https://github.com/mininet/mininet.git
cd mininet
```

2. Run the installation script :
```bash
./util/install.sh -a
```

This will install all dependencies required for Mininet, along with Open vSwitch and other components that you'll need for network simulation.

## Static Routing
This project demonstrates static routing between hosts and routers, visualized using the following network topology:

### Static Routing Topology

```mermaid
graph TB
    subgraph "Area 0 (Backbone)"
        R1((R1))
        R2((R2))
        R3((R3))
        R1 --- R2
        R1 --- R3
        R2 --- R3
    end
    
    subgraph "Area 1"
        R1 --- R1_1((R1_1))
        R1 --- R1_2((R1_2))
        R1_1 --- C1_1[C1_1]
        R1_2 --- C1_2[C1_2]
    end
    
    subgraph "Area 2"
        R2 --- R2_1((R2_1))
        R2 --- R2_2((R2_2))
        R2_1 --- C2_1[C2_1]
        R2_2 --- C2_2[C2_2]
    end
    
    subgraph "Area 3"
        R3 --- R3_1((R3_1))
        R3 --- R3_2((R3_2))
        R3_1 --- C3_1[C3_1]
        R3_2 --- C3_2[C3_2]
    end
```

## ADDITIONAL CONFIGURATION !
```bash
sudo nano /etc/sysctl.conf
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
```

example results when running the ospf-lab.py :
```bash
========================================
Warning: Linux bridge may not work with net.bridge.bridge-nf-call-arptables = 1
Warning: Linux bridge may not work with net.bridge.bridge-nf-call-iptables = 1
Warning: Linux bridge may not work with net.bridge.bridge-nf-call-ip6tables = 1
Finished initializing network in: 1.1319239139556885 seconds
```
And, config this too :
```bash
ospf-lab$ sudo modprobe bridge
sudo modprobe br_netfilter
```

The results will be like this :
```bash
bridge                335872  1 br_netfilter
stp                    12288  1 bridge
llc                    16384  2 bridge,stp
```
