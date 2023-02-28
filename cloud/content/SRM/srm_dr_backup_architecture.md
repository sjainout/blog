---
title: "HA, DR, plus Backup Architecture"
date: 2022-10-26T09:56:17-04:00
weight: 30
TableOfContents: true
---

### Steady State

![ha_dr_backup_steadystate_1](http://drive.google.com/uc?export=view&id=19O5Es0A8ZKCMzRhwL-euPOcBi8876x87)

#### Application Requirement and Data synchronization platform
0. Tier 0
	- Recovery Time Objective (RTO): 0; Recovery Point Objective (RPO): 0
	- Example: Shared services (Active Directory, Network Firewall, Load Balancer)
	- Synchronization: Application platform-based replication (active-active)
	- Storage: Integrated

1. Tier 1
	- RTO: minutes; RPO: seconds
	- Example: Financial and Business critical applications
	- Synchronization: Application platform-based replication (active-standby)
	- Storage: Integrated (AV36)

2. Tier 2
	- RTO: hours; RPO: minutes
	- Example: Production applications
	- Synchronization: DR platform-based replication
	- Storage: Integrated (AV36)

3. Tier 3
	- RTO: hours; RPO: hours
	- Example: Test applications
	- Synchronization: DR platform-based replication
	- Storage: Network mounted (ANF)

4. Tier 4
	- RTO: days; RPO: daily
	- Example: Development applications
	- Synchronization: Backup platform-based replication
	- Storage: External (Blob)


#### Recommended Actions
- Deploy sufficient AVS hosts for:
	- Tier 0 applications
	- Tier 1 applications 
	- Tier 2 storage placeholders
- Setup Disaster Recovery platforms to continuously replicate data for:
	- Tier 2 applications 
	- Tier 3 applications (check to see which DR platforms support this)
- Setup Backup platforms to periodically replicate data to Blob storage for:
	- Tier 2 - 4 applications 
- Recovery Test:
	- Periodically conduct DR and Backup Recovery test 
	- Isolated network environment can be setup using NSX-t in AVS



### Recovery State

![ha_dr_backup_recoverystate_2](http://drive.google.com/uc?export=view&id=1rdkenTlnUNNmf73D-pukPfpQeWxh9q7W)

#### Application Recovery Sequence

1. Tier 0
	- Recovery is immediate (active)
	- Recovery Platform: Application HA

2. Tier 1
	- Recovery is in seconds (standby > active)
	- Recovery Platform: Application HA

3. Tier 2
	- Recovery is in minutes (DR placeholder > guest OS bootup)
	- Recovery Platform: DR

4. Infrastructure Expansion
	- Add new AVS host(s) to vSAN clusters (hours) for Tier 3 - 4

5. Tier 3
	- Recovery is in hour(s) (DR placeholder > guest OS bootup)
	- Recovery Platform: DR

6. Tier 4
	- Recover subset of backed up applications
	- Recovery is in hours/day(s) (Blob storage > AVS storage)
	- Recovery Platform: Backup

