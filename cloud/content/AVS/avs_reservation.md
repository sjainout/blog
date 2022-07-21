---
title: "AVS Reservation"
date: 2022-07-20T22:32:34-04:00
TableOfContents: true
---
# Azure VMware Solution (AVS) Host Reservation 

## Introduction
AVS host by default are created using on-demand billing rates but if Reserved Instance (RI) for AVS host is purchased then customer can reduce the overall billing commitment.

Azure AVS Reserved Instance [Documentation](https://docs.microsoft.com/en-us/azure/azure-vmware/reserved-instance) covers 2 routes:
1. Buy Reserved Instances for an Enterprise Agreement (EA) subscription
2. Buy Reserved Instances for a Cloud Solution Provider (CSP) subscription

## Requirements
1. AVS Subscription value
2. AVS Region
3. Reservation duration: 1 year or 3 years
4. Payment duration: upfront or monthly 
5. Number of hosts to reserve
6. User purchasing the reservation should have at least one of these roles: 
        1. Owner
        2. Reservation Purchase

## Sample execution steps
1. Deploy AVS with necessary hosts
2. Log in to Azure portal with Owner credentials
3. Go to 'Reservation' page on Azure Portal 
        1. One method is to go to search bar and type in ‘Reservation’
4. Select 'Purchase'
5. Select 'Azure VMware Solution'

![avs-ri-1.jpeg Select Azure VMware Solution](http://drive.google.com/uc?export=view&id=1hBjA-ID8B4us0nXyc-sPQP1-tPdoFsrV)

6. Leave scope to default value of 'shared'
7. Set 'Billing subscription' ID to same as AVS's subscription
8. Set 'Region'
9. Set 'Term'
10. Set 'Billing frequency'

![avs-ri-2.jpeg Set Filters](http://drive.google.com/uc?export=view&id=1_zOGCTa91BXeCl0uXQv0Oyohppiz3qg5)


11. Select 'Row' and 'Add to cart'

![avs-ri-3.jpeg Set Filters](http://drive.google.com/uc?export=view&id=1LLaVXf1zV6D4-E4_mXVBNWu25mVjpKNf)

12. Select 'Review + Buy'
13. Check final reservation state (Succeeded)


## FAQ
1. Can there be multiple reservations for a given subscription account?
   yes


## Open questions
1. Can reservation subcription be changed?
2. Can reservation region be changed?
3. Can reservation duration be changed?
4. Can reservation host type be changed?
5. Can reservation be canceled?

