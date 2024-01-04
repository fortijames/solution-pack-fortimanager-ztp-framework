| [Home](../README.md) |
|--------------------------------------------|

# Installation

Install the Solution Pack. This is an example screenshot and what you see in the content hub may defer in version and details. 

![](./res/setup/setup-001.png)

# Configuration
 
 * Modify the System `Settings > Appliances > Playbook` user to have the `ZTPF-Playbook-Appliance`, *or `FortiManager-Playbook-Appliance` if before 1.0.3*, Role.
 * Modify the System `Settings > Users`, that will be using this solution, to have the `ZTPF-Admin`, *or `FortiManager-Admin` if before 1.0.3*, Role.
 * Navigate to `Automation > Connectors` and look for `Code Snippet`. Make sure this is installed and has a configuration marked as `Mark as default configuration`.
 * Go to the [Setup Options Section](./setup/README.md) for customization options for your install. 

## Setup FortiManager ZTP Flow (ZTPF) Framework

Setting up the FortiSOAR/FortiManager ZTP Flow (ZTPF) integration depends a lot on how you want to use the solution pack. The general order of setup consists of the following tasks and will vary based on what objectives you are trying to accomplish:
  - Create an [API User](#fortimanager-api-user) on your FortiManager. 
  - [Add a Manager Record](#add-manager-to-fortisoar) for your FortiManager.
  - Synchronize your FortiManager Device Database in FortiSOAR.
  - Create Metafield Templates in FortiSOAR.
  - Create Scripts in FortiSOAR. 
  - Create a ZTP Profile and link the required Metafield Templates and Scripts.
  - Assign a ZTP Profile to a ForiManager Device using a manual assignment or an auto-assignment.

## FortiManager API User

Add a FortiSOAR API user to your FMG that has RPC read-write permissions. Below is an example user that includes a FortiSOAR avatar. Edit the avatar, username, password, and/or profile to meet your needs. The most important setting is `set rpc-permit read-write` for API access.

![](./res/setup/setup-002.png)

```
config system admin user
    edit "fortisoar"
        set password fortinet
        set profileid "Super_User"
        set avatar "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"
        set rpc-permit read-write
    next
end
```

## Add Manager to FortiSOAR

Navigate to the Manager Module under the **FortiManager** solution records.

![](./res/setup/setup-007.png)

**Add** a new **Manager** (FortiManager) record into FortiSOAR and input the required fields. 

![](./res/setup/setup-008.png) ![](./res/setup/setup-010.png)

If your Manager record worked you should see the FortiManager details auto-populate fields, such as `Platform`, `SN`, `Firmware`, `Time `Zone`, etc. The `Source Data` tab shows you all the available data from the System Info API call to FortiManager. 

![](./res/setup/setup-011.png)

You are now ready to start synchronizing the FortiManager Device DB and perform actions on those devices.

 # Next Steps

| [Configuration](./setup/README.md) | [Usage](./usage.md) | [Contents](./contents.md) |
|------------------------------------|---------------------|---------------------------|