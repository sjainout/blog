---
title: "AVS Internet Access Architecture Options"
date: 2022-07-22T17:06:04-04:00
---

There are 3 broad exit points for Internet access for VMs sitting inside of AVS:
- Directly from AVS
- From Azure Region
- From On-Prem

![AVS Internet Access Architecture Choices](http://drive.google.com/uc?export=view&id=1IQ29_P01m7aCSUTux-d60UKpMj6Fa2Xm)

Further subdividing the categories:
- Directly from AVS
	- using SNAT
	- using Public IP
- From Azure Region
	- using Azure vWAN Hub with Global Reach
	- using Azure vNet with Global Reach
	- using Azure vWAN Hub without Global Reach
	- using Azure vNet without Global Reach
- From On-Prem
	- existing on-prem DMZ

---
