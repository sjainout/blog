---
title: "AVS NSXT NVA Architectures"
date: 2022-07-22T16:13:18-04:00
---

Customer can deploy self-managed NVAs like FireWall, Loadbalancer, etc, inside of AVS Private Cloud. From NSX-T's point of view it is just another Virtual Machine (VM).

![AVS NVA Architecture Choices](http://drive.google.com/uc?export=view&id=1CpaRtwfM90TPlj36ZfCAeaDCq645Fm4O)

- Here, NVA has to be in routed path, where, it acts as network gateway for the layer 3 segment.
- From scale point of view, ESXi supports 10 network interfaces per VM. 
	- 1 interface can be used for uplink 
	- 1 for management
	- 1 for ha
	- 7 segments are then left to create security zones.
- Security zone in these options can either be 'a segment' or 'an isolated NSX-T T1 gateway'
- On the main NSX-T T1, configure a summary static route for all the south-bound segments with next hop set to NVA.
- On the isolated NSX-T T1s, configure default static route using 0.0.0.0/1, 128.0.0.0/1 with NVA as the next-hop.

---

