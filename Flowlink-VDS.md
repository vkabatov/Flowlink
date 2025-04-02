# VDS NetFlow configuration for Flowlink

This guide provides instructions on how to set up vSphere VDS to send NetFlow records to Flowlink for agentless VM-to-VM and VM-to-external (outside of VDS) traffic visibility. 
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.02
```
## About NetFlow and VDS
The VMware vSphere Distributed Switch (VDS) is a central platform that allows for the management, configuration, and monitoring of virtual machines within the vSphere environment. It acts as a switch that enables networking access and facilitates easy switching between VMs.

vSphere VDS NetFlow is a feature of VMware vSphere Distributed Switch (VDS) that enables network traffic monitoring and analysis using the NetFlow protocol. It provides insights into virtual network traffic patterns, helping with security, troubleshooting, and performance optimization.

VDS supports export of unsampled flows to external collectors, including FlowLink.

### VDS references
```
https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vsphere-networking-8-0.html
```


## Setup
1. Right-click the VDS >> Settings >> Edit NetFlow

    ![Alt text](/Images/vds-edit-netflow.png?raw=true "Select VDS Netflow Settings")


2.  Specify Collector IP (Flowlink) address

    Set sampling rate to 0

    ![Alt text](/Images/vds-config.png?raw=true "VDS Configuration")

3.  Right-click the dvPG >> Edit Settings

    ![Alt text](/Images/dvpg-settings.png?raw=true "Select dvPG Settings")

4.  Under Monitoring, set NetfFlow to Enabled

    ![Alt text](/Images/dvpg-config.png?raw=true "dvPG Configuration")

5.  Enable Netflow (Step 4) on uplink port group (DVUplinks)


---------------
Important!!

To enable NetFlow on a vSphere Distributed Switch (VDS) port group for bidirectional traffic monitoring, enable NetFlow on both the port group and the uplink port groups to capture traffic entering and exiting the virtual network. 
---------------
