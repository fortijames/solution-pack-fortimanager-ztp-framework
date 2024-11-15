# What's New

Release of 1.0.4:
 - Fix problems with running in FSR 7.5.x. 
 - Add support for FMG Workspace mode. 
 - Add a task monitor playbook for tasks that take a long time. 
 - Modify the ZTP Profile Record View to ease editing settings. 
 - Fix multiple issues outlined in the repo>issues.
 - Update random device model creation for testing to better supported models of the FMG by firmware. 

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