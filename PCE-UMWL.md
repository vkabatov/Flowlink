# VM traffic review
This page shows the VMs represented through unmanaged workloads and the associated traffic.
 
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.02
```
## Unmanaged workloads created to represent the VMs

Create unmanaged workloads to represent the VMs. Traffic will not populate until those objects are created.

> See Alex Goller UMWL-maker page for automation
```
https://github.com/alexgoller/illumio-flowlink-umwl-maker
```
![Alt text](/Images/pce-umwl.png?raw=true "Unmanaged Workloads")

## Generate traffic between VMs
The VMs in this example are L2 adjacent and on the same port group.

SSH into each machine and generate traffic between the VMs.
historian<>hmi traffic
#a-ot-historian:
```
netcat -l 14001
```
#a-ot-hmi: 
```
netcat -v a-ot-historian.wornbit.io 14001
```

hmi<>engr-pc traffic
#a-ot-hmi:
```
netcat -l 2010
```
#a-ot-engr-pc:
```
netcat -v a-ot-hmi.wornbit.io 2010
```

historian<>engr-pc
#a-ot-historian:
```
netcat -l 3389
```
#a-ot-engr-pc
```
netcat -v a-ot-historian.wornbit.io 3389
```
## Review traffic and the map

The traffic is displayed with source, destination, port/protocol and time but with 'Unknown Policy Decision', since it is not processed by a VEN
![Alt text](/Images/pce-traffic.png?raw=true "Unmanaged Workload Traffic")

The traffic between is shown on the map as.
![Alt text](/Images/pce-map.png?raw=true "Unmanaged Workload Map")
