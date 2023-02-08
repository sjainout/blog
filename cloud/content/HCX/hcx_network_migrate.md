---
title: "Migrate Network with HCX"
date: 2023-02-06T17:39:04-05:00
TableOfContents: true
weight: 30
---

VMware's Hybrid Cloud eXtension (HCX) platform can be used to:
1. Migrate Virtual Machine from source datacenter to AVS
2. Migrate Network segment from source datacenter to AVS

In this article we'll explore steps which can be taken to seemlessly migrate network from VMware based source datacenter over to AVS. 

## Network Migration States 

We'll explore the transition with the following states:
1. <b>Initial State:</b> where source datacenter has network connection to AVS private cloud. 
2. <b>Intermediate Network Extension State:</b> where a layer 2 network segment has been extended to AVS.
3. <b>Intermediate Optimized Local Routing State (Optional):</b> where local smart routing is enabled within AVS.
4. <b>Final Network Migration State:</b> where network gateway is migrated to AVS.

### Initial State

![Initial State](http://drive.google.com/uc?export=view&id=1M85_3wtcGzbv-L35dKiYNfUVhSa1eEG9)
- On-Prem
	- Routing advertisement subnet: 10.10.10.0/24
	- Network gateway: 10.10.10.1
- AVS	
	- Routing advertisement subnet: 10.20.20.0/24
	- Network gateway: 10.20.20.1
- HCX
	- Administrator action: deploy HCX 

### Intermediate Network Extension State

![Intermediate State](http://drive.google.com/uc?export=view&id=1vsob29dWFPzX1MBOmQ3-KSo90hkYf3RI)
- On-Prem
	- Routing advertisement subnet: 10.10.10.0/24
	- Network gateway: 10.10.10.1
- AVS	
	- Routing advertisement subnet: 10.20.20.0/24
	- Network gateway: 10.20.20.1
- HCX
	- Network extension: 10.10.10.0/24
	- Network gateway: 10.10.10.1 
	- Network gateway location: On-Prem
	- Mobility optimized networking: not enabled
	- AVS NSX-T1 segment attachment: not enabled
	- Administrator action: extend 10.10.10.0/24 network to AVS
	- Administrator action: migrate all VMs in 10.10.10.0/24 network to extended network in AVS

### Intermediate Optimized Local Routing State (Optional)

![Intermediate Optional State](http://drive.google.com/uc?export=view&id=1Vji5FzRgFusea12bPAzcd-n96y2KoOml)
- On-Prem
	- Routing advertisement subnet: 10.10.10.0/24
	- Network gateway: 10.10.10.1
- AVS	
	- Routing advertisement subnet: 10.20.20.0/24
	- Network gateway: 10.20.20.1
	- Routing advertisement subnet: 10.10.10.13/32
- HCX
	- Network extension: 10.10.10.0/24
	- Network gateway: 10.10.10.1 
	- Network gateway location: On-Prem
	- Mobility optimized networking: enabled
	- AVS NSX-T1 segment attachment: enabled
	- AVS NSX-T1 VM attachement: 10.10.10.13
	- Administrator action: enable MON on extended network and also on all VMs in extended network 


### Final Network Migration State

![Final State](http://drive.google.com/uc?export=view&id=1jgppwYmhbrq996EI06SZT2TvS4zpGGlq)
- On-Prem
	- Routing advertisement: None
	- Network gateway: None
	- Administrator action: delete GW 10.10.10.1 from local router
- AVS	
	- Routing advertisement subnet: 10.20.20.0/24
	- Routing advertisement subnet: 10.10.10.0/24
	- Network gateway: 10.10.10.1
	- Network gateway: 10.20.20.1
- HCX
	- Administrator action: unextend 10.10.10.0/24 network

## References
- [Network Extension Requirement](https://docs.vmware.com/en/VMware-HCX/4.5/hcx-user-guide/GUID-0C746416-850E-46F7-85DD-4D4326A23785.html)
- [Network Extension Restrictions](https://docs.vmware.com/en/VMware-HCX/4.5/hcx-user-guide/GUID-DBDB4D1B-60B6-4D16-936B-4AC632606909.html)	

