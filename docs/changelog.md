| [Home](../README.md) |
|--------------------------------------------|

# Change Log
- 20240308 (1.0.3)
 - Aggregate changelog into monthly changes instead of daily changes. 
 - Add support for Custom Script Types. 
 - Modified Device field `deviceName` to be writeable by playbooks for Custom Scripts to change. 
 - Update Docs to show Custom Script information. 
 - Alow system export rename of playbook files that had a `-` instead of `>`. 
 - Update playbooks associated with the **Create New Device** trigger and automatic assignment of ZTP Profiles for better performance. 

- 20231228 (1.0.2)
 - Add jinja vars support to ztp profile assignments and update docs to reflect this change.

- 20230822
  - Fixed playbooks that reference the connector fortinet-fortimanager-json-rpc. It was incorrectly referencing fortinet_fortimanager_json_rpc.

- 20230724
  - Migrate FortiManager microservices playbooks connector usage from the custom 3.0.0 version to the json_rpc 1.0.0 version. 
  - Add comment when assigning ZTP Profile. 
  - Update device record comments with status/details from retrieve device config.
  - Update device record comments with status/details from install config and policy package. 
  - Fix bug related to a null monitor regex field in ztp profiles.

- 20230630
  - Add custom playbook for reading spreadsheet files attached as metadata types.
  - Add Retrieve Device Config Phase and Tested.
  - Add monitor metadata support.
  - Add support for custom playbook metadata sources. 
  - Add metadata monitor regex fields and logic. Fixed device in device group bug. 
  - Add script error handling. ZTP Phases now go to "Fail" if a joining step has errors. 

- 20230531
  - Add error passing on script run to implement error handling. 
  - Add support for Report Script Templates. 
  - Create Packages if not defined and packages will be named by the device if not defined. 
  - First addition to prompting user for metafield on create.
  - Updated the auto assign profile. 
  - Add toggle for profile removals.
  - Add new playbooks for metafield handling and for auto assign options.
  - Add logic to allow for chainint ZTP Profiles together. 
  - Tweak ZTP Auto Assignment and add Step Configuration. 
  - Added ZTP Trigger master playbook and implemented first assumed update path. 
  - Add new ZTP Phases and begin the ZTP Phase trigger system. 

- 20230428
  - Add ZTP Assignment and Mode picklists.
  - Rename lots of buttons.
  - Added ZTP Phase data fields. 
  - Running Provisioning Templates now assigns devices to groups and uses the ZTP Profile Template Group Name if set...otherwise use the devname. 
  - Added lots of provision template playbooks. 
  - ZTP Profiles run a link and metadata merge on change. 
  - Metdata templates now also support rendering per device.
  - Add Metafield Templates and ZTP Profiles.
  - Add RPC Set to Connector.
  - Add playbooks for managing variables. 
  - Add record link from managers to devices. 
  - Synch Managers now...also now can communicated with FortiCloud. 
  - Can manage metadata keys using records.
  - Support import and export of metafields
  - Added metadata key add and delete functions. 
  - Add device fields for provisioning and pkg.
  - Add script to run on device option. 
  - Add script to do dynamic var lookups.
  - Tweak the create and execute script to function as desired. 
  - Export wizard always leaves off new fields.
  - Missing some script module fields now added.
  - Create new Script Module and Handle Create/Exec Script
  - Add run script button. 
  - Migrate install and run script to handle one or more devices.

- 20230331
  - Post upgrade 7.4.0.
  - Add spinner to install too.
  - Cleanup of some playbook views.
  - Add status spinner.
  - 2x ways to API to FOS.
  - Set devices to delete if no longer found. 
  - FOS Helper playbooks now use the util http instead of the http connector. 
  - Add config management dashboard. 
  - Add connection status as html.
  - Repair missing fields from Export wizard. 
  - Add new button to FMG devices that have been deleted.
  - Add new playbook, FOS Helpers, for bootstrapping the FMG config on the FG. 
  - Move status fields to an html and text version. 
  - Add source data field to devices. 
  - Change button logic to match status fields. 
  - Support comma separated configs on db synch.
  - Delete now also clears status fields. 
  - Add synch with status in the playbook.
  - Multitenant support. 
  - Device Records with comments.
  - Playbooks inclue synch, auth, and delete.