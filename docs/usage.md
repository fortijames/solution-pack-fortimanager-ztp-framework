| [Home](../README.md) |
|--------------------------------------------|

# Usage

The FortiManager ZTP Flow framework turns automation objectives into building blocks: Data Sources feed data, Templates build payloads, Automation Actions do the work, and Automation Profiles order the work into steps that run on devices. Work through the checklist below in order — each section is one step of the process. Before starting, complete the [installation](./setup.md) and [configuration](./configuration.md).

## Checklist

- [ ] 1. [Connect a Manager and find devices](#1-connect-a-manager-and-find-devices)
- [ ] 2. [Plan your automation objectives into steps](#2-plan-your-automation-objectives-into-steps)
- [ ] 3. [Create Data Sources for the data your steps need](#3-create-data-sources-for-the-data-your-steps-need)
- [ ] 4. [Create Templates for shared payloads](#4-create-templates-for-shared-payloads)
- [ ] 5. [Create Automation Actions](#5-create-automation-actions)
- [ ] 6. [Build the Automation Profile and add steps](#6-build-the-automation-profile-and-add-steps)
- [ ] 7. [Run the automation and monitor the Device Automation Steps](#7-run-the-automation-and-monitor-the-device-automation-steps)

## 1. Connect a Manager and Find Devices

- Add a Manager record and make sure it works as described in the [installation](./setup.md#add-a-manager) area: the status moves to `Ok` and the Source Data tab is populated from the FortiManager API.
- Run `Synch Devices (New)` from the Manager record to pull the FortiManager Device DB into FortiSOAR, and confirm the devices appear in the [Devices](./modules/devices.md) module.
- If your FortiManager does not have any devices, you can use Device Models instead of real FortiGate devices: add model devices in the FortiManager Device DB and synchronize those — model devices stand in for real FortiGates while you build and test the framework.

## 2. Plan Your Automation Objectives into Steps

Before building anything, decide what you need for your automation objectives and put them into an ordered list of steps. For each step ask:

- What should this step do — collect or gather data, execute something on the network, install, or validate?
- What data does the step need to do it?
- What should happen when the step finishes?

The answers decide which building blocks you need in the sections below.

## 3. Create Data Sources for the Data Your Steps Need

If your steps need data, start by creating [Data Sources](./modules/data_sources.md) records. The Type of a Data Source decides where the data comes from: Static Data, FortiManager API, FortiManager Proxy API, Playbook, Step Output, or Spreadsheet Attachments.

Use the test wizard on the Data Source record — `Get Metadata Source Data on Device` — to confirm that the Data Source record gets the data you expect for a selected device. It prompts for a device, renders the source script in that device's context, and shows the data that would be collected.

## 4. Create Templates for Shared Payloads

If an action needs to leverage a common script, or payload, that can be used by multiple actions, create a [Template](./modules/templates.md) instead of copying the payload into each action. Templates are reusable Jinja scripts that can also link to data records, and they build standard script payloads for actions to use by referencing `{{template}}` in the payload.

## 5. Create Automation Actions

[Automation Actions](./modules/automation_actions.md) are what your steps run. Actions can focus on collecting and gathering data, or on executing something on the network.

For each action, decide what data is needed to perform the action and link it to the action:

- Link the [Data Sources](./modules/data_sources.md) that supply the action's data — the data is available in the action script as `data.<datakey>`.
- If the action leverages a common script or payload, link a [Template](./modules/templates.md) and reference it as `{{template}}` in the payload.
- Output templates control what the output of the action will be in various formats — Text, Markdown, HTML, and JSON.
- The Output Status Template is used to indicate if the action on the step worked as expected. If issues are found from the output, the status template raises an exception and decides what happens next: continue with an exception flag and then continue, or cancel or abort the rest of the steps being run on the device in the run group.

## 6. Build the Automation Profile and Add Steps

Once you have built the required building blocks — Data Sources if needed, Templates if needed, and Automation Actions — create an [Automation Profile](./modules/automation_profiles.md) and add [steps](./modules/automation_profile_steps.md) to it in the order the automation should run.

Steps hold arguments which can have input options and configurations to be used for the referenced action. The steps under the Automation Profile are used to build the Device Automation Steps when the profile runs.

## 7. Run the Automation and Monitor the Device Automation Steps

When an Automation Profile runs on a device, the framework creates a [Run Group](./modules/run_groups.md) containing the [Device Automation Steps](./modules/device_automation_steps.md) built from the profile steps.

Device Automation Steps are the records responsible for actually running the automation. They contain the final payload script that is used in the automation as well as the output produced by running the automation. Monitor progress per device and per step from the Run Group.

## Next Steps

| [<](./configuration.md) | [Contents](./contents.md) |
|-------------------------|----------------------------|
