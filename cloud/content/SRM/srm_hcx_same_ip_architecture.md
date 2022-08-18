---
title: "Application DR architecture keeping same IP"
date: 2022-07-26T13:20:25-04:00
weight: 20
TableOfContents: true
---

### DR steady state
- Protected site: On-Prem
- Recovery site: AVS
- DR Platform: VMware Site Recovery
- Protected VMs: 3 On-Prem VMs replicated SRM Port Group (PG)
- Placeholder VMs: 3 AVS placeholder VMs will be created and kept up to date

![srm_hcx_1](http://drive.google.com/uc?export=view&id=1Um4t5JuVZD0kENd2ccPtOtNNQ167AQsD)


### DR Test 
- DR test platform: Site Recovery Manager (SRM)
- DR test network: Isolated Segment in AVS
 
![srm_hcx_2](http://drive.google.com/uc?export=view&id=1ZiRB-rjECiKYGv_Vxgjfs9qyw3zOUixi)

### DR Migration 
- DR migration platform: Site Recovery Manager (SRM)
- Protected VMs: 3 On-Prem VMs will be shutdown
- Recovery VMs: 3 AVS VMs will be powered on
- Recovery VM network: Layer 2 extended network
- Network extension platform: HCX

![srm_hcx_3](http://drive.google.com/uc?export=view&id=1Ww4Ywm98hOEvCLKy4ff05VgtU2MonFHI)

### DR Event 
- Protected Site: no longer available
- Recovery Site: AVS
- Recovery VMs: all VMs come up on AVS
- Recovery VM network: Layer 3 segment
- Recovery network platform: NSX-t (part of AVS)

![srm_hcx_4](http://drive.google.com/uc?export=view&id=1XEBQl9dfKSqsEIw8_oSP46V-1IbMWkQb)

