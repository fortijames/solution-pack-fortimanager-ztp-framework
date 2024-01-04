| [Home](../README.md) |
|----------------------|

# Change Log
- 20240105 (1.0.3)
  - Add ZTP Archive Module and Playbooks to create archive records. 
  - Rename Roles and Teams to be `ZTPF` to simplify finding objects. 
  - Update Docs

- 20231228 (1.0.2)
 - Add jinja vars support to ztp profile assignments and update docs to reflect this change.

- 20230822
  - Fixed playbooks that reference the connector fortinet-fortimanager-json-rpc. It was incorrectly referencing fortinet_fortimanager_json_rpc.

- 20230724
  - Migrate FortiManager microservices playbooks connector usage from the custom 3.0.0 version to the json_rpc 1.0.0 version. 

- 20230713
  - Add comment when assigning ZTP Profile. 
  
- 20230712
  - Update device record comments with status/details from retrieve device config.

- 20230706
  - Update device record comments with status/details from install config and policy package. 
  - Fix bug related to a null monitor regex field in ztp profiles.

- 20230630
  - Add custom playbook for reading spreadsheet files attached as metadata types.

- 20230629
  - Add Retrieve Device Config Phase and Tested.

- 20230614
  - Add monitor metadata support.

- 20230613
  - Add support for custom playbook metadata sources. 

- 20230607
  - Add metadata monitor regex fields and logic. Fixed device in device group bug. 

- 20230601
  - Add script error handling. ZTP Phases now go to "Fail" if a joining step has errors. 

- 20230531
  - Add error passing on script run to implement error handling. 

- 20230530
  - Add support for Report Script Templates. 

- 20230519
  - Create Packages if not defined and packages will be named by the device if not defined. 

- 20230515
  - First addition to prompting user for metafield on create.
  - Updated the auto assign profile. 

- 20230512
  - Add toggle for profile removals.
  - Add new playbooks for metafield handling and for auto assign options.

- 20230511
  - Add logic to allow for chaining ZTP Profiles together. 

- 20230509
  - Tweak ZTP Auto Assignment and add Step Configuration. 

- 20230508
  - Added ZTP Trigger master playbook and implemented first assumed update path. 

- 20230504
  - Add new ZTP Phases and begin the ZTP Phase trigger system. 

- 20230428
  - Add ZTP Assignment and Mode picklists.

- 20230427
  - Rename lots of buttons.
  - Added ZTP Phase data fields. 

- 20230425
  - Running Provisioning Templates now assigns devices to groups and uses the ZTP Profile Template Group Name if set...otherwise use the devname. 

- 20230424
  - Added lots of provision template playbooks. 

- 20230419
  - ZTP Profiles run a link and metadata merge on change. 

- 20230417
  - Metadata templates now also support rendering per device.

- 20230414
  - Add Metafield Templates and ZTP Profiles.
  - Add RPC Set to Connector.
  - Add playbooks for managing variables. 

- 20230413
  - Add record link from managers to devices. 

- 20230412
  - Synch Managers now...also now can communicated with FortiCloud. 
  - Can manage metadata keys using records.
  - Support import and export of metafields

- 20230411
  - Added metadata key add and delete functions. 

- 20230410
  - Add device fields for provisioning and pkg.

- 20230407
  - Add script to run on device option. 
  - Add script to do dynamic var lookups.

- 20230406
  - Tweak the create and execute script to function as desired. 

- 20230405
  - Export wizard always leaves off new fields.
  - Missing some script module fields now added.

- 20230405
  - Create new Script Module and Handle Create/Exec Script
  - Add run script button. 
  - Migrate install and run script to handle one or more devices.

- 20230331
  - Post upgrade 7.4.0.
  - Add spinner to install too.
  - Cleanup of some playbook views.

- 20230329
  - Add status spinner.
  - 2x ways to API to FOS.
  - Set devices to delete if no longer found. 

- 20230328
  - FOS Helper playbooks now use the util http instead of the http connector. 

- 20230327
  - Add config management dashboard. 
 
- 20230324
  - Add connection status as html.

- 20230323
  - Repair missing fields from Export wizard. 
  - Add new button to FMG devices that have been deleted.
  - Add new playbook, FOS Helpers, for bootstrapping the FMG config on the FG. 

- 20230322
  - Move status fields to an html and text version. 
  - Add source data field to devices. 
  - Change button logic to match status fields. 

- 20230320
  - Support comma separated configs on db synch.
  - Delete now also clears status fields. 

- 20230317
  - Add synch with status in the playbook.
  - Multitenant support. 
  - Device Records with comments.
  - Playbooks include synch, auth, and delete.