# What's New

## Release of 1.0.3:
 - Add ZTP Archives module for saving snapshots of ZTP records. 
 - Add ZTPF Teams and Roles for Users and Admins. 
 - Add Docs to help with [Setup](./docs/setup/README.md) of your System. 
 - Renamed Roles:
   `FortiManager-Playbook-Appliance` -> `ZTPF-Playbook-Appliance` 
   `FortiManager-Admin` -> `ZTPF-Admin`

## Release of 1.0.2: 
 - Add jinja vars support to ztp profile assignments and update docs to reflect this change.

## Release of 1.0.1: 
 - fixes the playbooks that references the connector fortinet-fortimanager-json-rpc. It was incorrectly referencing fortinet_fortimanager_json_rpc.

# Known Bugs

## Dashboard Dynamic Content ( 0932566 )

If you are updating an existing solution pack then the included Announcement might be auto-incremented. This impacts the Dashboard Quick Links. To fix this SSH into FortiSOAR and run the following, as root (`sudo su -`), command until this is fixed. 

```
env PGPASSWORD=$(cat /home/csadmin/device_uuid) \
psql -U cyberpgsql -d venom -c "update announcements set id=1 where uuid='83ca88a8-e02f-48a1-901f-39aede335b7d';"
```
See internal Bug ID `0932566` for the latest status of the bug. 