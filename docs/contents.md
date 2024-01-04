| [Home](../README.md) |
|----------------------|

# Contents

The **FortiManager ZTP Flow** solution pack contains the following resources.

## Connectors

|**Name**|**Description**|
| :- | :- |
| Fortinet FortiManager JSON-RPC  |  _Pending_ Connector used to do generic API calls to FortiManager using API calls documented in [FNDN FortiAPI for FortiManager](https://fndn.fortinet.net/index.php?/fortiapi/5-fortimanager/). |

## Module Schema

|**Name**|**Description**|
| :- | :- |
| Managers | Stores FortiManager information for one or more FortiManagers |
| Devices | Synchronized from the FortiManager's Device DB table. |
| Metafield Templates | Template files to populate Device Metadata on Device records. |
| Scripts | Records designed to do a variety of scripts. Markdown Reports per device, DeviceDB, Remote CLI, PolicyDB, and/or TCL Scripts on devices via the FortiManager API. |
| ZTP Profiles | Defined solutions to apply templates and scripts to devices on demand or when discovered. |
   
## Roles

|**Name**|**Description**|
| :- | :- |
| FortiManager-Playbook-Appliance | The playbook appliance needs to have full access to records to update fields that are owned by FortiManager.  |
| FortiManager-Admin | Users should not directly edit fields that are owned by FortiManager. |

## Record Set

|**Name**|**Description**|
| :- | :- |
|  Announcements  |  Used in Dashboards for Quick Links.  |

## Playbook Collection

|**Playbook Collection Name**|**Description**|
| :- | :- |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-Microservices | Focuses on FortiManager API calls. |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-Buttons | Buttons that users can use to invoke sections of the framework on carious records. |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-RecordHandlers | Automation around records within the framework. |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-Synchronizing | Synchronize data from FortiSOAR and FortiManager. |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-Triggers | Actions triggered by record changes within the system and used heavily in the ZTP Flow process. |
| 10 - SP - FortiManager ZTP Flow - FortiManager(FMG)-CustomPlaybooks | Playbooks that can be created by users as metadata sources and used in Template files to build custom solutions within the integration. |

>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.