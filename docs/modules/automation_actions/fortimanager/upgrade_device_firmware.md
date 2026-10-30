| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Upgrade Device Firmware

| | |
| --- | --- |
| Category | FortiManager |
| Trigger Key | `FortiManager Upgrade Device Firmware` |
| Running Playbook | `> running step - FortiManager Upgrade Device Firmware` |

## Summary

Upgrades the device firmware through the FortiManager. The upgrade runs as a FortiManager task, and the step waits — re-checking the task at a set interval — until the upgrade finishes before the run continues.

## Script Payload

YAML with a `firmware:` key. The value is the firmware version to upgrade to, typically supplied by the step's `input.firmware` and rendered by Jinja:

```yaml
firmware: 7.6.6
```

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - FortiManager Upgrade Device Firmware`.
2. That playbook renders the step's script payload as YAML and reads the `firmware` value.
3. It calls `> upgrade firmware image ext` to start the firmware upgrade task in the FortiManager, then sets the step to **Waiting** with the task output stored as Output Source Data.
4. The `> device step (Waiting)` trigger looks up the Trigger Key in its wait-check index and runs `> waiting check - FortiManager Upgrade Device Firmware`, which polls the task status. While the task is still running, the step stays in Waiting and the `> device step (Waiting Timer)` trigger restarts the check every `waitToCheckSeconds` (default 60 seconds).
5. When the upgrade task finishes, the step proceeds and the shared post-run playbook renders the output templates, evaluates the Output Status Template, and chains the next step in the run group.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [Collect Artifacts](../ztpf/collect_artifacts.md) |
|------------------------------------------------|----------------------------------------------------|
