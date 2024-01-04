| [Home](../README.md) |
|--------------------------------------------|

# Usage

The `FortiManager ZTP Flow` Solution Pack has a variety of uses. First, refer to the [installation and setup guide](setup.md) guide to get started. Read the content below to help guide you through some solutions. 

You may also want to install the [FortiManager ZTP Flow - Feature Examples](https://fortisoar.contenthub.fortinet.com//list.html?contentType=all&searchContent=FortiManager%20ZTP%20Flow%20-%20Feature%20Examples) to get functional profiles and templates for various objectives. 


# Module Summary

## [Managers](./usage/managers.md)>
Manager records define the FortiManagers, and the current firmware and status, used in your solution. Creating a Manager record will automatically create the FortiManager JSON-RPC connector configuration for API access. 

## [Devices](./usage/devices.md)>
Devices are synchronized from the FortiManager and stored in FortiSOAR. Automation can then occur on one or more devices based on device properties and workflow needs. Once created, they are not removed from FortiSOAR to preserve the last known status of the Device record even if the device has been removed, or moved, from your FortiManager. 

## [Metafield Templates](./usage/metafield_templates.md)>
Managing metadata is crucial to the success of any network deployment and provisioning. Metafield Templates can be used to prompt required users to respond to unknown, but required, fields before deployment. Templates can be used to integrate external systems and retrieve key data requirements before deployment to create dynamic metadata based on a wide range of advanced and complex requirements through [Metafield Sources](./usage/jinja_rendering_with_metafield_sources.md). Metadata inside FortiSOAR can be exports to FortiManger to be used by already existing solutions with minimal effort.

## [Script Templates](./usage/script_templates.md)>
Scripts in FortiSOAR can be used for creating customized FortiManager CLI, Device DB, Policy DB, and/or TCL Scripts per device. Scripts in FortiSOAR can also maintain and create Provisioning CLI Templates in FortiManager such as when new ADOMs are created and need to be setup with Templates. Device reporting scripts can also be used to create a custom dashboard with user defined content. Scripts can also be enhanced by gathering external data using [Metafield Sources](./usage/jinja_rendering_with_metafield_sources.md).

## [ZTP Profiles](./usage/ztp_profiles.md)>
The ZTP Profiles module describes how to handle the provisioning of each device maintained by the respective FortiManager. As a device shows up in the FortiManager Device DB, unauthorized or modeled, when ZTP Profiles are assigned to those devices the defined device templates and provisioning steps are applied and reported per device. ZTP Profiles can be assigned on demand or automatically assigned when devices are created in FortiManger regardless of how the devices were created. Automatic assignment of ZTP Profiles can leverage [Metafield Sources](./usage/jinja_rendering_with_metafield_sources.md) to create complex auto assignment rules.

# Examples and Detailed Topics

 * [Multiple ZTP Profile Example](./usage/example1.md): Provision of 4x Unauthorized FortiGates VMs in FortiManager starting by simply assigning a ZTP Profile.
 * [Jinja Rendering with Metafield Sources](./usage/jinja_rendering_with_metafield_sources.md): Dynamic Metafield Source options for enhancing the provisioning experience. 

 # Next Steps

| [Contents](./contents.md) |
|--------------------------------|