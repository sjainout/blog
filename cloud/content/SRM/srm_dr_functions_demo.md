---
title: "Application DR - Lab Demo"
date: 2023-03-20T18:56:03-04:00
weight: 40
TableOfContents: true
---

This document covers lab demo covering following sequence of steps:
1. Protect application for disaster 
2. Test recovery application in isolated network 
3. Migrate application to recovery site 
4. Recover application and network on disaster 

## Application Protection

![1 DR Protection Demo](http://drive.google.com/uc?export=view&id=1ZJnyt-fYayCK_oxUJ8af560tkhPFQLjD)

Demo video contains the following:
- Setup inventory parameters between protected and recovery sites.
- Setup Application Replication with RPO value.

<br>
</br>
{{< youtube 7yX_OOigqK4 >}}

## Application DR Test

![2 DR Test Demo](http://drive.google.com/uc?export=view&id=1rPJ_y44pxZTeAin_tKfKUdvYvy7VbEzj)
 
Demo video contains the following:
- Execute DR Test in isolated network environment at Recovery site.
- Verify application is still running in Protected site.

<br>
</br>
{{< youtube 1TN9fVynBVw >}}

## Application DR Migrate

![3 DR Migrate Demo](http://drive.google.com/uc?export=view&id=1Nud28d6Jr_oxc8p4cvP0xvIgoP-X1Voz)

Demo video contains the following:
- Execute application DR Migration to Recovery site.
- Verify application can reach all the other VMs in Protected and Recovery sites.
- Reprotect application back to original Protected site.

<br>
</br>
{{< youtube z1M_KENmsgQ >}}

## Application and Network Recocery on Disaster

![4 DR Event Demo](http://drive.google.com/uc?export=view&id=11KkQOVYzWSdkRhORfYgZ1D10lojTI5un)
 
Demo video contains the following:
- Assume Protected site is no longer reachable.
- Execute DR Event from SRM in Recovery site.
- Unextend the network from HCX in Recovery site.
- Verify application can reach all the other VMs in Recovery site. 

<br>
</br>
{{< youtube yrdSzGZHjm0 >}}


