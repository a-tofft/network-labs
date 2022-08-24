# Content
Personal Networking labs utilizing [containerlab](https://github.com/srl-labs/containerlab) & [netsim-tools](https://github.com/ipspace/netsim-tools)

More examples may be found here: https://github.com/ipspace/netsim-examples

# Setup

### Requirements
- docker
- git
- poetry
- python


### Install Images
 - You must download & add necessary images to docker 
 - Arista: https://www.arista.com/en/support/software-download

```bash
# Add image
docker import cEOS-lab-4.27.0F.tar ceos:4.27.0F

# List images
docker images
```
### Install Containerlab 

```bash 
bash -c "$(curl -sL https://get-clab.srlinux.dev)"
```

### Install Packages
```bash
poetry install
```

# Usage

## Download Repository 
```bash 
git clone git@github.com:a-tofft/network-labs.git && cd network-labs
```

## Activate Environment

```bash
poetry shell
```

## Container Lab Files
clab.yml files are used by containerlab to build the desired topology.

```bash
# Move to desired lab
cd <lab_name>

# Deploy lab and start containers
sudo containerlab deploy -t clab.yml

# Shutdown containers & retain configs
sudo containerlab destroy -t clab.yml

# Shutdown containers & remove configs
sudo containerlab destroy -t clab.yml --cleanup
```

## Netsim Lab Files
Netsim-tools utilizes containerlab and generates the necessary clab.yml file as well as configurations. 

```bash
# Move to desired lab
cd <lab_name>

# Create necessary containerlab & config files 
netlab create topology.yml

# Deploy Topology
netlab up topology.yml

# Destroy Lab, also removes startup-configs
netlab down
```