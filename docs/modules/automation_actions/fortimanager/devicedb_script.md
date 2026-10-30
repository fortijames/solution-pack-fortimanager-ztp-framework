| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# DeviceDB Script

| | |
| --- | --- |
| Category | FortiManager |
| Trigger Key | `FortiManager DeviceDB Script` |
| Running Playbook | `> running step - FortiManager Device Script` |

## Summary

Runs a CLI script against the device's Device DB through the FortiManager. The step's rendered script is created as a Device Manager script of type `DeviceDB` in the Manager, executed on the device, its log retrieved, and the script deleted again — leaving no script artifacts behind in the Manager.

## Script Payload

Jinja-rendered CLI commands. The script is rendered per device at run time and executed as a FortiManager Device Manager script of type `DeviceDB`.

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - FortiManager Device Script`.
2. That playbook finds the device and the step, takes the step's rendered script as the script contents, and derives the FortiManager script type from the Trigger Key — the Type without the ` Script` suffix (`DeviceDB` here).
3. It calls `> create exec delete device manager script on devices`, which creates the script in the FortiManager Device Manager, executes it on the device, retrieves the script log, and deletes the script.
4. The exec task output and the script log are stored as the step's Output Source Data. A task error marks the step `Fail`; otherwise the shared post-run playbook renders the output templates, evaluates the Output Status Template, and chains the next step in the run group.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [PolicyDB Script](./policydb_script.md) |
|------------------------------------------------|-----------------------------------------|
