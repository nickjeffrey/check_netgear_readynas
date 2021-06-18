# check_netgear_readynas
nagios check for Netgear ReadyNAS Duo 

# Requirements
perl,snmpget on nagios server
SNMP daemon enabled on Netgear ReadyNAS


# Configuration
Add a section similar to the following to commands.cfg on the nagios server:
```
# ---------------------------------------------------------------------------
# 'check_netgear_readynas' command definition
# parameters are -H hostname -C snmp_community
define command{
        command_name    check_readynas
        command_line    $USER1$/check_readynas -H $HOSTADDRESS$ -C $ARG1$
        }
```

Add a section similar to the following to services.cfg on the nagios server:
```
# ---------------------------------------------------------------------------
# Define a service to check the Netgear ReadyNAS
# Parameters are SNMP community name
define service {
        use                             generic-service
        hostgroup_name                  all_netgear_readynas
        service_description             Netgear ReadyNAS
        check_command                   check_netgear_readynas!public
        }

```


# Output
```
Netgear ReadyNAS OK - ReadyNAS version:6.1.4  Drive bays:4  Installed disks:2  Disk 1 temperature:37C  Disk 2 temperature:37C Temperature probe 1:41C Fan 1 speed:3450RPM Fan 2 speed:3450RPM Logical volume BackupVol:47% full (4.7TB/10TB)
```
