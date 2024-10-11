# static-routing-mininet

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
