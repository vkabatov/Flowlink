# Flowlink
illumio Flowlink install, config, troubleshoot notes
 ```
 Author: Vlad Kabatov, illumio, inc.
 Version 2025.04.02
```
## Collection of Flowlink notes and install links
Deploy and configure Supported Linux OS for FlowLink
```
https://support.illumio.com/shared/software/os-support-package-dependencies/flowlink.html
```

Download the latest Flowlink RPM package
```
https://support.illumio.com/software/download.html#flowlink/download/
```
Install FlowLink
```
https://product-docs-repo.illumio.com/Tech-Docs/Core/24.4/Install-Upgrade/out/en/flowlink-configuration-and-usage/flowlink-configuration/configure-flowlink.html
```
copy flowlink to /tmp and install
```
cd /tmp
sudo su
rpm -ivh illumio-flowlink-x.x.x-yy.x86_64.rpm
```
Shutdown -r the server
```
reboot
```
## Configure Flowlink
```
https://product-docs-repo.illumio.com/Tech-Docs/Core/24.2/Install-Upgrade-Admin/out/en/flowlink-configuration-and-usage/flowlink-configuration/configure-yaml.html
```
Data directory (used in these configuration examples):
```
/usr/local/illumio/data/
```
### Configure api user
Users in this example have Global Org Owner permissions
On the PCE, navigate to:
Access >> Service Accounts >> Add
Create a service account and copy Authentication Auth Username/Secret

Alternatively, to create API Keys:
Top right-hand corner button with username >> My API Keys >> Add

File containing the api_key:
```
/usr/local/illumio/data/flowlink-api
```
Specify the api_key and secret on a single line:
```
api_116deb678d0bbfde1 e60ae20b32a5f1aa6a0469eff94c43a0b5dcbff6ad65c89ed083ccb283250965
```
### Configure Flowlink YAML
Detailed parameters available here
```
https://product-docs-repo.illumio.com/Tech-Docs/Core/24.2/Install-Upgrade-Admin/out/en/flowlink-configuration-and-usage/flowlink-configuration/configure-yaml.html
```

Schema file with all possible configuration options (and backup in cases of accidental deletion) available here:
```
/usr/local/illumio/flowlink_config_schema.json
```

Cleanup the yaml file and delete unnecessary consumers. 
`
/usr/local/illumio/data/config.yaml
`
Update values for:
    pce_addr
    api_key (location)
    data_directory
    org_id

In this example, only netflow and syslog consumers are configured with default values.
Output of config.yaml file:
```
---
pce_addr: pce-fqdn:8443
api_key: $cat /usr/local/illumio/data/flowlink-api
data_directory: /usr/local/illumio/data/
org_id: 3
aggregation_minutes: 5
consumers:
  - name: syslog
    connectors:
      - type: udp
        properties:
          ports: "6514"
    parser:
      type: text
      properties:
        src_ip: sip
        dst_ip: dip
        dst_port: dport
        protocol: prot
        timestamp: "date_time, 1"
        timestamp_format: "mmm dd yyyy HH:MM:SS"

  - name: netflow
    connectors:
      - type: udp
    parser:
      type: netflow
    connectors:
      - type: udp
        properties:
          ports: '2055'
```

Create an empty file to log Flowlink events
```
touch /usr/local/illumio/data/flowlink-log
```

Start Flowlink service and specify the log file
```
illumio-flowlink-ctl start --config /usr/local/illumio/data/config.yaml --log-file /usr/local/illumio/data/flowlink-log
```

## Flowlink troubleshooting
Check Flowlink status
```
illumio-flowlink-ctl status
```

Tail Flowlink logs
```
tail -f /usr/local/illumio/data/flowlink-log
```

Stop Flowlink service
```
illumio-flowlink-ctl stop
```

