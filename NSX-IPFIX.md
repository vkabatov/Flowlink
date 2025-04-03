# VDS NetFlow configuration for Flowlink

This page provides references to IPFIX configuration in NSX. 
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.03
```
## About IPFIX and NSX
NSX can generate IPFIX flow records. NSX has different use cases and can be depoloyed in several ways:

-----------
> NSX manages vCenter vlan-backed networking without overlay.

> NSX manages vCenter networking with overlay.

> NSX Distributed Firewall (DFW/vDefend) with NSX managing vCenter VLAN-backed or overlay networking.
-----------

> Note: There is an additional option to deploy NSX Distributed Firewall (DFW/vDefend) without NSX managing the networking. This scenario is uncommon. In this scenario, configure the VDS through vCenter to generate NetFlow Records.

> Note: NSX-managed virtual switch is very similar to the traditional VDS, except it is managed through the NSX Manager, rather than vCenter. The NSX virtual switch and the NSX networks (distributed port groups) are visible in the vCenter, but denoted as "Managed by NSX"

NSX can generate IPFIX flow records at either NSX virtual switch (similar to VDS) or Distributed Firewall (after filters process connections at vNIC level). 

The difference between NSX Firewall IPFIX and NSX Switch IPFIX lies in their function and the level at which they operate in VMware NSX. Here's a breakdown:

NSX Firewall IPFIX
    Function: Collects flow data after firewall processing.
    Scope: Provides insight into network traffic that is allowed or denied based on firewall rules.
    Use Case: Helps with security monitoring, compliance, and identifying anomalies in traffic patterns.
    Placement: Works at the NSX Distributed Firewall (DFW) layer.
    Visibility: Shows data for permitted and denied flows, including firewall rule hits.

NSX Switch IPFIX
    Function: Collects flow data at the switching level before firewall processing.
    Scope: Focuses on raw traffic flows before any firewall rules are applied.
    Use Case: Useful for network traffic analysis, troubleshooting, and capacity planning.
    Placement: Works at the NSX Virtual Distributed Switch (VDS) layer.
    Visibility: Provides detailed east-west and north-sout traffic flows to and from VMs.

IPFIX flow records can be simultaneously generated at both switch and firewall. 

## Configure IPFIX in NSX

NSX Switch IPFIX configuration
```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-switch-ipfix-collectors.html
```
```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-switch-ipfix-profiles.html
```

NSX Firewall IPFIX configuration

```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-firewall-ipfix-collectors.html
```
```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-firewall-ipfix-profiles.html
```