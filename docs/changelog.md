| [Home](../README.md) |
|--------------------------------------------|

# Change Log
 - 20240913-20241118 (1.0.5)
   - Update device synch to include hostname. 
   - Update special fields in the ZTP steps for authorization to include ADOM. 
   - Update `> monitor task complete` to continue if it errors out but return an `error:True` so that a stuck task can show `Failed`. 
   - Modify `> synch record metadata to fmg adom variables - by device` to default to the Global context if not running in vdom mode. 
   - Modify `> fmg install config - on devices` to use `> monitor task complete`. 
   - Modify `> change ztp phase on device records` to transition actions to toggle to the phase pending and then set to properly re-trigger records. 
   - Modify all buttons that deal with transitions to use the subroutine. 
   - Create `> fmg exec task - return standard output of results.json` to consolidate exec handling. 
   - Modify `> fmg install config - on devices.json` and `> fmg install policy package - on devices.json` playbooks to leverage the new playbook. Remove use of task monitor as the enhanced track_task functions are being added to pyFMG. 
   - Modify Dashboards to collapse Quick Links and show pie charts where useful. 
   - Modify playbook `On ZTP Profile Assignment in Device Record` to clear all ZTP fields when a new profile is assigned.
   - Modify playbook `> fmg exec task - return standard output of results` to handle latest `task_track()` return from `pyfmg`. 
   - Create playbook button `ZTP Phase Retry Failed on Device from Device Record` for devices that have failed a phase. 
   - Add new fields for storing ZTP Start/Stop times per device and update playbooks to update these in the ZTP Flow. 
   - Enhance ZTP Phase comments on a device. 
   - Modify `On ZTP Phase (Action Step) in Device Record` to better handle error conditions and set the device to fail instead of failing the playbook on problems.
   - Modify `Randomly Create Model Devices - by Manager Record` to have a better list of supported products by FMG firmware (7.2 - 7.6) to prevent errors during testing. 
   - Add new playbook `> get fmg supported platforms` to get supported platforms from FMG and update `Randomly Create Model Devices - by Manager Record` to use it. 

- 20240701 (1.0.4)
  - Update json-rpc Connector to 1.0.4. 
  - Modify ZTP Profile Views. 
  - Modify URLs to use ADOM on API calls to better support locking ADOMs. 
  - Add support for installing Policy Packages to a group within the playbook. 
  - Add get task and wait for task playbooks. 

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
  - Add logic to allow for chaining ZTP Profiles together. 
  - Tweak ZTP Auto Assignment and add Step Configuration. 
  - Added ZTP Trigger master playbook and implemented first assumed update path. 
  - Add new ZTP Phases and begin the ZTP Phase trigger system. 

- 20230428
  - Add ZTP Assignment and Mode pick lists.
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
  - Playbooks include synch, auth, and delete.