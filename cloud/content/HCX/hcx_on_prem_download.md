---
title: "HCX On-Prem Connector OVA Download"
date: 2022-07-25T08:50:43-04:00
TableOfContents: true
weight: 20
---

[Documentation](https://docs.microsoft.com/en-us/azure/azure-vmware/install-vmware-hcx#download-and-deploy-the-vmware-hcx-connector-ova)

## login to cloud HCX manager

### get cloud HCX manager URL
- AVS > Add-ons > Migration using HCX > HCX Cloud Manager IP
![hcx_avs_url](http://drive.google.com/uc?export=view&id=1l8tf1U9KLzA43wY2zQckykMG5qBYj_Ns)

### get cloud HCX manager login credentials
- AVS > Identity > vCenter > Admin username 
- AVS > Identity > vCenter > Admin password  
![hcx_avs_login_credentials](http://drive.google.com/uc?export=view&id=1AdTM1GWWGoCJb59URw87mN30G3Czh5W3)

(do not select 'Generate a new password') 


### open browser to cloud HCX manager
- Use the IP, username and password gathered from earlier steps to go to https://<hcx-cloud-mgr-ip>


## download on-prem HCX Connector OVA

### request download link
 
- HCX > Administrator > System Updates  
![hcx_avs_request_download_1](http://drive.google.com/uc?export=view&id=1eXZe8PVov_DCCJ_-anpqgLAejlJL3nvF)

- wait for few minutes for link to show up
- Select 'Request Download Link'  
![hcx_avs_request_download_2](http://drive.google.com/uc?export=view&id=1RvOIgZzPWuSXYzq2akrV4F_6n99rG3Ld)  

### start download 
- Select 'VMware HCX' to start the download OR
- Select 'Copy Link' to save the download URL
![hcx_avs_connector_download_3](http://drive.google.com/uc?export=view&id=1RzXECjL3g0Ivc4kmOV76-mqxeWq-_1Z5)

