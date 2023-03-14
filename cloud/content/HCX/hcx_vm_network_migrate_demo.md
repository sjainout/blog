---
title: "Migrate VM and Network - Lab Demo"
date: 2023-03-13T10:17:35-04:00
TableOfContents: true
weight: 40
---

This document covers lab demo covering following sequence of steps:
1. Extend network from on-prem to AVS
2. Migrate VM from on-prem to AVS
3. Enable Mobility Optimized Networking in AVS
4. Migrate network segment in AVS

## Management

![1 Management Lab](http://drive.google.com/uc?export=view&id=16tXD5-uua5gsFJIQkqIKVSJ3AqizNu0y)

Lab environment has been setup with the following:
- Express Route connection between on-prem (Chicago) and AVS (Azure USA West region)
- HCX deployment in both on-prem and AVS
- HCX site pair between on-prem and AVS


## Network Extension

![2 Network Extension Lab](http://drive.google.com/uc?export=view&id=1Z1yILuMLMbZG6GmencXPi-d4OA_Cmgmc)

Demo video contains the following:
- Extend vlan 1193 from on-prem to AVS
- Use on-prem gateway as default 

<br> 
</br> 
{{< youtube kCOBz-vjIFU >}}

## VM Migration

![3 VM Migration Lab](http://drive.google.com/uc?export=view&id=14OqFKHI77okIAAuHRSNCXp5exXdovePq)

Demo video contains the following:
- Migrate VM from on-prem to AVS 
- VM is mapped to extended network using same IP
- Verify reachability to on-prem GW over network extension tunnel
- Verify reachability to other VM in same AVS via network extension tunnel
- Check AVS NSX-T settings

<br> 
</br> 
{{< youtube 0wI2IqQ4jg0 >}}

## Mobility Optimized Networking

![4 MON Lab](http://drive.google.com/uc?export=view&id=15Guj9_WFtEw2o4M4hOxNA1uwe5JUiMGp)

Demo video contains the following:
- Enable HCX mobility optimized networking (MON) for extended vlan
- Enable HCX MON for pre-migrated VM 
- Verify reachability to on-prem GW over network extension tunnel
- Verify reachability to other VM in same AVS with direct local switching
- Check AVS NSX-T settings

<br> 
</br> 
{{< youtube sKXUVZjblOo >}}

## Network Migration

![4 Network Migration Lab](http://drive.google.com/uc?export=view&id=18XYNsMYXaOF0WWSx-jazxP7UKRzd6rTP)

Demo video contains the following:
- Unextend network segment in AVS to convert extended segment to local AVS layer 3 segment 
- Verify reachability to on-prem GW and other VM in same AVS 
- Check NSX-T routes

Additional step required:
- Manually remove on-prem GW configuration (not shown in video) 

<br> 
</br> 
{{< youtube v5S8Aiubql0 >}}

