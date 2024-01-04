# What's New

Release of 1.0.3:
 - Add ZTP Archives module for saving snapshots of ZTP records. 
 - Add ZTPF Teams and Roles for Users and Admins. 
 - Renamed Roles:
   `FortiManager-Playbook-Appliance` -> `ZTPF-Playbook-Appliance` 
   `FortiManager-Admin` -> `ZTPF-Admin`

# Known Bugs

## Teams and Private Playbooks (0986751)



See internal Bug ID `0986751` for the latest status of the bug. 

## Dashboard Dynamic Content ( 0932566 )

If you are updating an existing solution pack then the included Announcement might be auto-incremented. This impacts the Dashboard Quick Links. To fix this SSH into FortiSOAR and run the following command until this is fixed. 

```
sudo env PGPASSWORD=$(cat /home/csadmin/device_uuid) psql -U cyberpgsql -d venom -c "update announcements set id=1 where uuid='83ca88a8-e02f-48a1-901f-39aede335b7d';"
```
See internal Bug ID `0932566` for the latest status of the bug. 