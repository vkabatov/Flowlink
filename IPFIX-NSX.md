# VDS NetFlow configuration for Flowlink

This page provides references to IPFIX configuration in NSX. 
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.03
```
## About IPFIX and NSX
NSX can generate IPFIX flow records. NSX has different use cases and can be depoloyed in several ways:


    NSX manages vCenter vlan-backed networking without overlay.

    NSX manages vCenter networking with overlay.

    NSX Distributed Firewall (DFW/vDefend) with NSX managing vCenter VLAN-backed or overlay networking.


> Note: There is an additional option to deploy NSX Distributed Firewall (DFW/vDefend) without NSX managing the networking. This scenario is uncommon. In this scenario, configure the VDS through vCenter to generate NetFlow Records.

> Note: NSX-managed virtual switch is very similar to the traditional VDS, except it is managed through the NSX Manager, rather than vCenter. The NSX virtual switch and the NSX networks (distributed port groups) are visible in the vCenter, but denoted as "Managed by NSX"


NSX can generate IPFIX flow records at either (virtual) Switch or (Distributed) Firewall. In other words, flow records are generated at either the NSX switch (similar to the VDS) or after the Distributed Firewall processing filters at the VM vNIC level.




```
https://techdocs.broadcom.com/us/en/vmware-cis/nsx/vmware-nsx/4-2/administration-guide/network-monitoring/advanced-monitoring-tools/configure-ipfix/configure-switch-ipfix-collectors.html
```