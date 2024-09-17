| [Home](../../README.md) / [Usage](../usage.md) |
|------------------------------------------------|

# ZTP Profiles

The ZTP Profile describes what automation will be applied, and how, when associated with a device record. This ZTP Profile record is broken into the following setting areas:
 - Profile Settings
 - Provisioning Settings
 - Related Records:
   - Metafield Templates  
   - Script Templates
   - Devices

Below we will provide details for the above setting areas and settings. 

## Profile Settings

The profile settings generally focus on how the ZTP Profile will operate when assigned to a device. It ranges from how the profile will be assigned to what might happen to the device record when the profile is associated. 

| Setting | Description |
| -------------------------- | --------------- |
| Order Priority | If running in `Automatic` `Assignment Mode` the order from lowest to highlest that devices are automatically assigned to a profile. |
| Profile Mode | The mode `Disable`, `Manual`, `Onboard`, `Lifecycle`, and `Decommision` is used for an overall operation of this profile. See the **ZTP Profile Modes** below for details. |
| Assignment Mode | Can be set to `Manual` where you need to select devices to get this profile or `Automatic` which will run as a new device record is created.  |
| Assignment Search Type | In automatic mode you can search for devices using `simple` and `advanced` with regex, or `jinja` to build logical responses of `true`. |
| Assignment Search Fields | Only available for regex searches with `Simple` or `Advanced` and concatenates selected fields into a string.  |
| Assignment Search Metadata Sources | Only available for `Jinja` searches and can retrieve Jinja variables from FMG API calls or custom playbooks. See the [Jinja Rendering with Metadata Sources](./jinja_rendering_with_metafield_sources.md) page for details. |
| Assignment Search | Available for `Simple` or `Advanced` to store the regex or when `Jinja` is the `Search Type` will store Jinja Template language. |
| Clear Linked Scripts | Checkbox to enable/disable the unlinking of any Script Templates related to the device this profile is assigned. This is useful for cases where a device has already run through a profile and you do not want to re-run the same templates. |
| Clear Linked Metafield Templates  | Checkbox to enable/disable the unlinking of any Metafield Templates related to the device this profile is assigned. This is useful for cases where a device has already run through a profile and you do not want to re-run the same templates.  |
| Clear Device Metadata | Checkbox to enable/disable to clear any previously created metadata from the metafield templates. This can be useful in cases where the metadata was already used and no longer needed.  |
| Clear Device Reports | Checkbox to enable/disable to clear the `Report Markdown` field of the device in the case where you want to re-run Script Templates of type `Markdown Report` which will append that field on the device for reporting. |
| Export Metadata to FortiManager  | Checkbox to enable/disable the API call to update the FortiManager Variables per Device mapping.  |
| Retain Profile Assignment | Checkbox to enable/disable toggles if we should remove a ZTP Profile from a device when the ZTP Phases are complete. This is useful for cases where you might want to re-run a profile on a device or where you want to filter completed device based on the assigned profile regardless of the phase state. This is only available when `ZTP Profile Next` is empty.   |
| Skip Delete Device | Checkbox to enable/disable is only available when running the `Profile Mode` as `Decommission` which by default will remove the device from FortiManager but retain the device record in FortiSOAR. |

# ZTP Phases

The ZTP Phases are controlled from the `ZTP Step Map` field in the ZTP Profiles. The default setting is the following and can be changed to meet your needs. 
```
{
  "Authorize" : {
    "next_step" : "Device Metadata"
  },
  "Device Metadata": {
    "next_step" : "Device Groups"
  },
  "Device Groups": {
    "next_step" : "Run Linked Scripts"
  },
  "Run Linked Scripts": {
    "next_step" : "Install Device Config"
  },
  "Install Device Config": {
    "next_step" : "Install Policy Package"
  },
  "Install Policy Package": {
    "next_step" : "Complete"
  } 
}
```

## Phase Steps Defined

| Phase  | Description  |
| --------- | ----------------- |
| Authorize | Authorize device if needed. If the device is modeled we skip to the next step. If the ADOM is not set we assume `root`. | 
| Device Metadata | Handle device metadata. Can include notifying users  of required data. Can use metadata sources to retrieve data from API calls to FMG or custom playbooks.  |
| Device Groups | Add Device to Device Groups defined in the ZTP Profile and/or the Device Metadata. |
| Run Linked Scripts | Run all scripts linked to the device record. Scripts are not unlinked when done but ZTP Profiles can clear linked scripts to prevent running scripts multiple times that should only be run once. |
| Install Device Config | Install the Device Config from the FMG API. |
| Install Policy Package | Install the policy package from the FMG API. The package name can be set from the device metadata, the ZTP Profile, or will default to the Device Name from the Device Record. |
| Complete | Completion of the step maps for this ZTP PRofile. Final actions will depend on the ZTP Profile type and settings. |

-----------

# ZTP Profile Modes

| Mode  | Description  |
| -------- | ----------------- |
| Disable |  Not in use. |
| Manual | Designed to run one phase on entry or manually run any phase on demand from the profile itself. |
| Onboard | When assigned runs all the phases from inside the step map. |
| LifeCycle | Runs on change of device states when assigned to a device. |
| Decommision | At assignment runs all phases from the step map and finishes by deleting the device from FMG by default. |

-----------

# Device Metafield Overrides
| Field  | Order | Description | 
| -------- | ------- | ---------------- |
| adom | ZTP Profile -> Device Metadata | authorize device to the adom if it exists during the auth phase. |
| device_groups | ZTP Profile -> Device Metadata | Append device groups to list without duplicating. |
| policy_package | Device Metadata -> ZTP Profile -> Device Record -> Device Name | Chooses the name of the policy package to use in the ZTP Phases based on this order of being said.  |