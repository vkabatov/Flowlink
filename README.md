# Flowlink
illumio Flowlink install notes
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
restart the server
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
POST 
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
