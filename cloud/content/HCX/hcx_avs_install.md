---
title: "HCX AVS Install"
date: 2022-07-20T22:33:23-04:00
TableOfContents: true
weight: 10
---

## AVS side HCX Manager Deployment Information
[AVS HCX Deployment](https://docs.microsoft.com/en-us/azure/azure-vmware/install-vmware-hcx#install-vmware-hcx-advanced)
 
## On-Prem side HCX Pre-Deployment Information
1. [Deployment details](https://docs.microsoft.com/en-us/azure/azure-vmware/install-vmware-hcx)
2. [On-prem HCX install requirements](https://docs.vmware.com/en/VMware-HCX/4.2/hcx-user-guide/GUID-A631101E-8564-4173-8442-1D294B731CEB.html)
3. [On-prem HCX ports](https://ports.esp.vmware.com/home/VMware-HCX) 
4. On-prem HCX IP requirements:
	1. 4x IP Addresses for HCX Appliances
		1. 3x management IPs
			1. 1x will be for the HCX Manager
			2. 1x will be for each Interconnect Appliance for Migration
			3. 1x will be for each Network Extension Appliance
		2. 1x vMotion IP for each Interconnect Appliance if vMotion network is isolated (optional)
5. DNS A record is needeed for on-prem HCX connector to map it’s static IP with it's FQDN name
6. Additional details which will be needed during deployment and configuration: 
	- vCenter URL
	- PSC URL
	- vCenter admin credentials 
	- DNS Server IP
	- NTP Server IP
	- Proxy Server (optional)
	- Storage for HCX deployment 
	- Cluster w/ test workload VMs 
	- vDS w/ Port Group for L2 extension
7. (Optional) [On-Prem NSX requirement for HCX deployment](https://docs.vmware.com/en/VMware-HCX/4.5/hcx-user-guide/GUID-30D954B5-C5CD-474A-B964-5A9DBDF1DA9E.html)
8. (Optional) [Network Extension Requirement](https://docs.vmware.com/en/VMware-HCX/4.5/hcx-user-guide/GUID-0C746416-850E-46F7-85DD-4D4326A23785.html)
9. (Optional) [Network Extension Restrictions](https://docs.vmware.com/en/VMware-HCX/4.5/hcx-user-guide/GUID-DBDB4D1B-60B6-4D16-936B-4AC632606909.html)	

---
