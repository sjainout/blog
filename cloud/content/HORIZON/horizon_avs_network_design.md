---
title: "Horizon AVS Network Designs"
date: 2023-02-27T10:16:52-05:00
TableOfContents: true
weight: 10
---

## Horizon AVS Network Design Options

Premise: Horizon in AVS uses hybrid architecture, where,
- Horizon shared services are installed in Azure vNet
- Horizon desktops are installed in AVS

This post covers only the following designs:
1. Horizon desktop access Internet via vNet
2. Horizon desktop access Internet directly via AVS

### Horizon desktop access Internet via vNet

![Horizon AVS Architecture 2](http://drive.google.com/uc?export=view&id=12hguLLSWgzYNhy8BacJCR43MLOtJn7GZ)

AVS Network Connections:
1. On-prem to Azure region using WAN Express Route
2. AVS to On-Prem using Express Route Global Reach
3. AVS to Hub vNet via local Express Route circuit

Azure Network Connections:
1. On-Prem to Azure region using WAN Express Route terminating in Hub vNet
2. Infrastructure Shared services in spoke vNet connected to hub vNet via vNet Peering
3. Horizon Shared services in spoke vNet connected to hub vNet via vNet Peering

Azure Hub vNet details:
1. Express route gateway setup to establish connection to both AVS and on-prem
2. NVA setup for internet and network security
3. Azure Route Server setup BGP connection with NVA
4. NVA advertises 0.0.0.0/0 to Azure Route Server
5. On-prem WAN Edge router discards 0.0.0.0/0 advertisement coming from Azure region
6. vNet peering connection to Horizon shared services vNet
7. vNet peering connection to Infrastructure shared services vNet

Traffic flows:

![Horizon AVS Flows 1](http://drive.google.com/uc?export=view&id=1jgRzs6QQZm0l7ei9nYMZw4cNtF37OTdc)

1. On-prem end-user access > WAN Express Route > Hub vNet > Horizon spoke vNet > Horizon Connection Server
2. Internet end-user access > vNet NVA > vNet Peering > Horizon vNet > Load Balancer > UAG
3. Horizon shared services > vNet Peering > Spoke vNet > AD
4. Horizon shared services > vNet Peering > Hub vNet > local express route circuit to AVS > Horizon desktop
5. Horizon shared services > vNet Peering > Hub vNet > NVA > Internet
6. Horizon shared services > vNet Peering > Hub vNet > WAN express route > on-prem end-user 
7. Horizon desktop > AVS express route global reach > on-prem end-user
8. Horizon desktop > AVS express route to hub vNet > NVA > Internet based end-user 
9. Horizon desktop > AVS express route to hub vNet > NVA > Internet site 

### Horizon desktop access Internet directly via AVS
 
![Horizon AVS Architecture 2](http://drive.google.com/uc?export=view&id=1uRBtqmggCjnw8eV3Rluef_yMKRTpgUc8)

AVS Network Connections:
1. AVS to On-Prem using Express Route Global Reach
2. AVS to Hub vNet via local Express Route circuit
3. AVS to Internet directly via NSX Edge Public IP  

Azure Network Connections:
1. On-Prem to Azure region using WAN Express Route terminating in Hub vNet
2. Infrastructure Shared services in spoke vNet connected to hub vNet via vNet Peering
3. Horizon Shared services in spoke vNet connected to hub vNet via vNet Peering

Azure Hub vNet details:
1. Express route gateway setup to establish connection to both AVS and on-prem
2. NVA setup for internet and network security for Azure native VMs and services
3. No BGP configuration, just UDRs for traffic re-direction
4. vNet peering connection to Horizon shared services vNet
5. vNet peering connection to Infrastructure shared services vNet

Traffic flows:

![Horizon AVS Flows 2](http://drive.google.com/uc?export=view&id=1Qx4G9YS901cePFJ6lTMakbguNscLYcEL)

1. On-prem end-user access > WAN Express Route > Hub vNet > Horizon spoke vNet > Horizon Connection Server
2. Internet end-user access > vNet NVA > vNet Peering > Horizon vNet > Load Balancer > UAG
3. Horizon shared services > vNet Peering > Spoke vNet > AD
4. Horizon shared services > vNet Peering > Hub vNet > local express route circuit to AVS > Horizon desktop
5. Horizon shared services > vNet Peering > Hub vNet > NVA > Internet
6. Horizon shared services > vNet Peering > Hub vNet > WAN express route > on-prem end-user 
7. Horizon desktop > AVS express route global reach > on-prem end-user
8. Horizon desktop > AVS express route to hub vNet > NVA > Internet based end-user 
9. Horizon desktop > AVS NVA > PIP > Internet site 

