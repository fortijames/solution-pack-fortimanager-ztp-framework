| [Home](../README.md) |
|----------------------|

# Contents

The solution pack ships the contents listed below. The framework building blocks — the modules — are documented in detail in the [Modules](./modules.md) reference, reached from [Usage](./usage.md).

## Modules

| Module | Description |
| ------ | ----------- |
| [Automation Profiles](./modules/automation_profiles.md) | An ordered set of steps that defines what runs on a device; assigning a profile to a device starts the automation. |
| [Automation Profile Steps](./modules/automation_profile_steps.md) | The steps of a profile: the referenced action, its arguments, and its input and configuration options. |
| [Automation Actions](./modules/automation_actions.md) | The reusable operations that steps run — FortiManager scripts and installs, API calls, validations — with payload, output, and status templates. |
| [Templates](./modules/templates.md) | Reusable Jinja payload scripts shared by actions and rendered as `{{template}}`. |
| [Data Sources](./modules/data_sources.md) | Define how a step's data is collected at run time: Static Data, FortiManager API, FortiManager Proxy API, Playbook, Step Output, or Spreadsheet Attachments. |
| [Managers](./modules/managers.md) | The FortiManager appliances: connection and status, discovered system information, and device synchronization. |
| [Devices](./modules/devices.md) | The FortiGates synchronized from each FortiManager, with status, source data, and their assigned automation. |
| [Device Metadata](./modules/device_metadata.md) | Persistent per-device values collected by Data Sources and consumed by templates and actions. |
| [Run Groups](./modules/run_groups.md) | One execution of a profile across one or more devices: status, timing, and reporting. |
| [Device Automation Steps](./modules/device_automation_steps.md) | The per-device, per-step records that actually run the automation: the final payload and the output produced. |
| [Manager Automation Profile Rules](./modules/manager_automation_profile_rules.md) | Rules that automatically assign Automation Profiles to devices as they appear on a Manager. |
| [Quick Links](./modules/quick_links.md) | Dashboard quick links for the framework. |

## Playbook Collections

| Collection | Description |
| ---------- | ----------- |
| `10 - SP - ZTPF - Buttons` | Handlers behind the buttons on the framework records. |
| `10 - SP - ZTPF - Triggers` | Playbooks that fire automatically on record events, such as a new device arriving or a status change. |
| `10 - SP - ZTPF - Functions` | The framework engine: reusable microservice playbooks that perform the actual work. |
| `10 - SP - ZTPF - FMG Microservices` | Focused FortiManager API wrappers used by the rest of the framework. |
| `10 - SP - ZTPF - Custom` | Space for your own playbooks; ships with examples such as `Generate Random Host IPs`. |

>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.

## Dashboards

| Dashboard | Description |
| --------- | ----------- |
| ZTPF Dashboard - Automation Run Group Reporting | Reports on automation Run Groups and their Device Automation Steps. |

## Widgets

| Widget | Description |
| ------ | ----------- |
| ZTP Run Report | Renders the report output of a run for a device or Run Group. |
| ZTP Group Timer | Shows the elapsed time of a Run Group stage. |
| ZTP Automation Step Graph | Draws the Device Automation Steps of a run as a graph. |
| Playbook Buttons | Renders the playbook buttons on the record details. |
| Playbook Execution Wizard | Wizard for examining playbook executions. |

## Roles

| Role | Description |
| ---- | ----------- |
| `ztpfAdmin` | Applied to the users who operate the framework; prevents direct edits to fields owned by FortiManager. See [Configuration](./configuration.md). |
| `ztpfPlaybookAppliance` | Applied to the Playbook Appliance user; allows playbooks to update the fields owned by the framework and FortiManager. See [Configuration](./configuration.md). |

## Connectors

| Connector | Description |
| --------- | ----------- |
| Code Snippet | Required. Used for data shaping, diffs, and YAML conversion; must have a configuration marked as default. |
| Fortinet FortiManager JSON RPC | API access to the FortiManagers; its configuration is created from each Manager record. |

## Picklists

| Picklist | Description |
| -------- | ----------- |
| `ztpfStatus` | Overall record status (Ok, Updating, Pending, Failed, Running, Ready, Reviewing, Disabled, Deleted). |
| `ztpfAdminStatus` | Enabled or Disabled state for framework records. |
| `ztpfRunGroupsStatus` | Run Group statuses (New, Running, Complete, Fail Detected, Reviewing, Abort Detected). |
| `ztpfDeviceStepStatus` | Device Automation Step statuses (Queued, Running, Preparing, Waiting, Complete, Fail, Cancel, Abort, and more). |
| `ztpfDeviceStepOutputStatus` | Step output statuses (OK, Exceptions Found, Incomplete). |
| `ztpfMetadataDeviceStatus` | Device Metadata statuses (Disable, New, Ok, Input Needed). |
| `ztpfActionCategory` | Which system an action targets (FortiManager, FortiSOAR, ZTPF, Universal). |
| `ztpfActionType` | The action types available to steps (scripts, installs, API calls, validations, and more). |
| `ztpfOutputType` | Output formats (Text, Markdown, HTML, JSON). |
| `ztpfMetadataType` | Data types for metadata values (Text, Secret, JSON). |
| `ztpfMetadataSourceType` | The Data Source types (Static Data, FortiManager API, FortiManager Proxy API, Playbook, Step Output, Spreadsheet Attachments). |
| `ztpfManagerGetNewDeviceType` | Which devices the Manager synchronization pulls (All, Unauthorized, Custom Filter). |
| `ztpfManagerRuleType` | Manager Automation Profile Rule purposes: onboard new devices, device lifecycle changes (MACD), or decommission devices. |
| `ztpfManagerRuleSearchType` | How a rule finds its devices (Simple, Jinja, All Devices). |

## Global Variables

| Global Variable | Description |
| --------------- | ----------- |
| `ztpf_running_triggerkey_idx` | Maps each action type to the playbook that runs it. |
| `ztpf_return_status_default` | The default return status object used by framework playbooks. |

## Playbook Blocks

| Playbook Block | Description |
| -------------- | ----------- |
| `ztpf: Pick a Manager then Device` | Reusable prompt that asks for a Manager and then a Device. |
| `ztpf: Pick a Manager then Device in one step` | The same selection in a single prompt. |

## Record Sets

| Record Set | Description |
| ---------- | ----------- |
| Quick Links | One seed record for the Quick Links module. |

| [<](./usage.md) |
|------------------|
