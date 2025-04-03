# VDS NetFlow configuration for Flowlink

This page provides references to IPFIX configuration in NSX. 
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.03
```
## About IPFIX and NSX
NSX can generate IPFIX flow records. NSX has different use cases and can be depoloyed in several ways:


    NSX managing vCenter vlan-backed networking without overlay.

    NSX managing vCenter networking with overlay.

    NSX Distributed Firewall (DFW/vDefend) with VLAN-backed or overlay.

--------------
Note: There is also an option to deploy NSX Disgtributed Firewall (DFW/vDefend). In this scenario, NSX does not manage any of the networking. This scenario is uncommon. Leverage VDS to generate NetFlow Records.
--------------

IPFIX flow records can be generated at the NSX Firewall 



```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-switch-ipfix-collectors.html
```