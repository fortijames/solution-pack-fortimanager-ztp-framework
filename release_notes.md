| [Home](./README.md) |
|--------------------------------------------|

# What's New

Release 2.0.60

This release adds the System Settings module, record cleanup playbooks, and slimmer role definitions. 

- New module: System Settings (`ztpf_system_settings`) — framework-level settings records with a data payload in JSON, Text, Markdown, or HTML, seeding a QuickLinks record that holds the framework's navigation links. 
- The ztpf Quick Links module is removed; its content now lives on the QuickLinks System Settings record. 
- New playbooks: a Delete Device Record button that finds the records related to a device, confirms with per-type counts, and deletes them; a delete orphan records function; a delete recursive records function; and a ztpf schedule trigger. 
- The Synch FMG Devices playbook resolves the `ztpfStatus` picklist by name instead of a hard-coded picklist id. 
- The role definitions now carry explicit permissions for the ZTPF modules only instead of an entry for every FortiSOAR module. 
- The Managers form places the admin status and status fields in their own column. 

Release 2.0.59

This release adds a ZTPF Templates navigation group and rounds out the documentation visuals. 

- Navigation: a new ZTPF Templates group in the navigation bar lists the automation-template modules: Automation Profiles, Profile Steps, Automation Actions, Templates, and Data Sources. 
- Cleanup: removed a leftover test widget tab from the Managers detail layout. 
- Documentation: every module framework diagram now carries its module title, the Device Automation Steps page adds a Device Automation Step Record field diagram, and the Create Single Loopback example adds a build-overview diagram showing each step's trigger key, args, and payload with the template's rendered CLI. 

Release 2.0.57

This release hardens the framework's playbooks and rounds out the documentation set. 

- Playbook reliability: record lookups no longer build a new JMESPath query per record (this fixes a jmespath cache-eviction failure when synchronizing source data for many devices on Python 3.11), rendered payloads are serialized to JSON before they are stored on a step, and a step keeps its existing status when it re-runs. 
- Clearer statuses: the failure status is now `Fail`, step updates write the `status` field (was `queueStatus`), return statuses start from the `ztpf_return_status_default` global variable, and FortiManager Proxy API steps separate proxy-call errors from device-call errors in the step message. 
- New playbooks: a bulk model-device generator button (`Randomly Create Model Devices - by Manager Record`), freeform device API execution (`api freeform exec DEV`), model device creation by PSK, and FortiManager ADOM and supported-platform lookups. The freeform proxy encapsulation microservice is deprecated. 
- The `Add Steps to Device from Profile` button now runs asynchronously with a 60-minute ready timeout (was 15). 
- Documentation: all module diagrams re-drawn as concise PNG summary visuals with family panels and data-flow arrows, an all-modules navigation list added to every module page, the Modules reference linked from Contents and Usage, and the 1.x usage pages replaced by the usage checklist and a worked example. 

Release 2.0.50

This release is a complete rebuild of the FortiManager ZTP Flow framework on a new set of ZTPF modules. Version 1.x kept the framework configuration in a small number of collections (ZTP Profiles, Metafield Templates, and Script Templates). ZTPF 2.0 replaces that model with twelve purpose-built modules that separate the building blocks of the framework: 

- **ZTPF Automation Templates** - the reusable definitions that drive automation: Automation Profiles, Automation Profile Steps, Automation Actions, Templates, and Data Sources. 
- **ZTPF Assets** - the managed estate and its data: Managers, Devices, and Device Metadata. 
- **ZTP Automations** - the executions: Run Groups and Device Automation Steps, plus Manager Automation Profile Rules and Quick Links to round out the set. 

What the new modules mean for you: 

   - Automation is composed from reusable parts. A profile is an ordered list of steps, and each step references an Automation Action, so the same action can be shared by every profile that needs it. 
   - Data is separated from logic. Device Metadata records hold per-device values, and Data Sources define how values are collected at run time (static data, FortiManager API, FortiManager Proxy API, playbooks, step output, and spreadsheet attachments). 
   - Runs are first-class records. Every execution creates Device Automation Steps under a Run Group, giving per-step status, timing, wait states, and reporting. 
   - This is a breaking change. The 1.x records and playbooks are replaced. Install this release fresh and rebuild your profiles in the new modules. 

Release highlights: 
   - New module set, roles (`ztpfAdmin` and `ztpfPlaybookAppliance`), and a new Automation Run Group Reporting dashboard. 
   - Wait states for automation steps, cancellation of queued/pending steps on fail, waiting timeouts, and consolidated status logic. 
   - New ZTPF Validate Data, Diff Step Output, and Collect Artifacts actions. 
   - New run group timer widget and per-step reporting flags. 
   - Global variables for playbook mapping (`ztpf_running_triggerkey_idx`) and a default return status (`ztpf_return_status_default`). 
   - New playbooks: export records by tag, CSV handler, FMG process list, and FMG process kill. 
   - New ZTPF2 documentation set under `docs/`. 

Release 1.0.2
   - Add 7.6.2 compatibility with playbook origin and editable flag support
   - Add new playbook to unlock all playbooks in the ZTP solution pack
   - Enhance Jinja templates for monitoring task execution time and policy script execution
   - Add logic to handle Jinja template rendering errors with device comments
   - Improve ZTP profile lookup performance using 7.6.2 loop breaking feature
   - Enhance missing metadata prompts with direct device record linking
   - Fix processing issue with running linked scripts on devices
   - Add task parameters for device authorization
   - Improve device name changing to use global device level
   - Add 7.6.2 dashboard defaults and MMD changes
   - Enhance format return for easier device IRI linking in dialogs
   - Enhance comment creation for script results


# Known Bugs

## Dashboard Dynamic Content ( 0932566 )

If you are updating an existing solution pack then the included Announcement might be auto-incremented. This impacts the Dashboard Quick Links. To fix this SSH into FortiSOAR and run the following command until this is fixed. 

```
sudo su -
env PGPASSWORD=$(cat /home/csadmin/device_uuid) psql -U cyberpgsql -d venom -c "update announcements set id=1 where uuid='83ca88a8-e02f-48a1-901f-39aede335b7d';"
```
See internal Bug ID `0932566` for the latest status of the bug.

| [Home](./README.md) |
|--------------------------------------------|
