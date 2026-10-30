| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Install Device Config

| | |
| --- | --- |
| Category | FortiManager |
| Trigger Key | `FortiManager Install Device Config` |
| Running Playbook | `> running step - FortiManager Install Device Config` |

## Summary

Installs the device's configuration from the FortiManager onto the device. No script payload is required — the playbook acts on the device directly.

## Script Payload

Not used. The playbook installs the device configuration from the Manager without needing a rendered payload.

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - FortiManager Install Device Config`.
2. That playbook finds the device and the step, then calls `> install config on devices` to start the install config task in the FortiManager for the device.
3. The task results are stored as the step's Output Source Data. A task error marks the step `Fail`; otherwise the shared post-run playbook renders the output templates, evaluates the Output Status Template, and chains the next step in the run group.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [Install Policy Package](./install_policy_package.md) |
|------------------------------------------------|--------------------------------------------------------|
