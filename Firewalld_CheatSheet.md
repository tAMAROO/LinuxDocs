## Firewalld Cheat Sheet

### Start the firewall:

|Command|Description|
|----------- | -----------|
|systemctl enable --now firewalld| This will enable and start the firewall|

### Options:

|Command|Description|
|----------- | -----------|
|--permanent| When this is added to a command this will make the command action persistent|
|--reload| This will reload firewalld|

### Managing Zones:

|Command|Description|
|----------- | -----------|
|--get-zones| List all zones|
|--get-active-zones| list all active zones and all interfaces|
|--zone=test --list-all| List properties of zone test|
|--change-interface=eth0 --zone=test| Add interface eth0 to zone test|
|--get-default| Get default zone|
|--set-default-zone home| Set default zone to test|
|--new-zone=work| Create new zone work (requires rule reload)|


### Add Ports and Services:

|Command|Description|
|----------- | -----------|
|--add-port={port}/tcp --zone=test| Allow TCP traffic on port 123 in zone test|
|--add-service {service} --zone=test| Allow traffic on murmur ports in zone test|



### Remove Ports and Services:

|Command|Description|
|----------- | -----------|
|--remove-port {port}/tcp --zone=test| Deny traffic on port {port} in zone test|
|--remove-service {service} --zone=test| Deny traffic on {service} ports in zone test|
