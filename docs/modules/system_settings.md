| [Home](../../README.md) / [Usage](../usage.md) / [Modules](../modules.md) |
|-----------------------------------------------------------------------------|


# System Settings

Record module: `ztpf_system_settings`

## Summary

The System Settings module holds framework-level settings as ordinary records. Each record has a name, a type tag that describes its purpose, a description, and a data payload in one of four formats — JSON, Text, Markdown, or HTML — selected by the record's Data Type and stored in the matching data field. The record's Details view shows the payload in its Text, JSON, HTML, and Markdown form.

The solution pack seeds one record: **QuickLinks** (type `ref`), whose HTML payload holds links for helping navigate the system. The record ends with an `[ edit links ]` link that opens the record itself, so the links can be edited in place.

Use the module wherever the framework needs a shared setting or a piece of content kept as data: create a setting record, give it a type tag, and store its value in the field that matches its Data Type.

## Fields

| Field | Type | Required | How it is used |
| ----- | ---- | -------- | -------------- |
| **Definition** | | | |
| Name | Text | Yes | Name of the setting, such as `QuickLinks`. |
| Type | Text | No | A tag for the setting's purpose, such as `ref` for navigation links. |
| Description | Text | No | What the setting is for. |
| **Data** | | | |
| Data Type | Picklist (`ztpfOutputType`) | No | The format of the payload: Text, Markdown, HTML, or JSON. |
| Data JSON | Object | No | The payload when the Data Type is JSON. |
| Data Text | Text Area | No | The payload when the Data Type is Text. |
| Data Markdown | Rich Text | No | The payload when the Data Type is Markdown. |
| Data HTML | HTML | No | The payload when the Data Type is HTML. |
| **Usage** | | | |
| id, createDate, createUser, modifyDate, modifyUser | System | — | System-managed record details shown on the record's Details tab. |

## Modules

**ZTPF Automation Templates**

 * [Automation Profiles](./automation_profiles.md)
 * [Automation Profile Steps](./automation_profile_steps.md)
 * [Automation Actions](./automation_actions.md)
 * [Templates](./templates.md)
 * [Data Sources](./data_sources.md)

**ZTPF Assets**

 * [Managers](./managers.md)
 * [Devices](./devices.md)
 * [Device Metadata](./device_metadata.md)

**ZTP Automations**

 * [Run Groups](./run_groups.md)
 * [Device Automation Steps](./device_automation_steps.md)
