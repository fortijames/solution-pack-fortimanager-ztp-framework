# What's New

Release of 1.0.3:
 - Add support for an exciting new Script Type: `Custom`
 - Modify ZTP Profile auto-assign to be more efficient and stop rendering device searches once the profile is found. 

Release of 1.0.2:
 - Add jinja vars support to ztp profile assignments and update docs to reflect this change.

# Known Bugs

## Dashboard Dynamic Content ( 0932566 )

If you are updating an existing solution pack then the included Announcement might be auto-incremented. This impacts the Dashboard Quick Links. To fix this SSH into FortiSOAR and run the following command until this is fixed. 

```
sudo su -
env PGPASSWORD=$(cat /home/csadmin/device_uuid) psql -U cyberpgsql -d venom -c "update announcements set id=1 where uuid='83ca88a8-e02f-48a1-901f-39aede335b7d';"
```
See internal Bug ID `0932566` for the latest status of the bug. 