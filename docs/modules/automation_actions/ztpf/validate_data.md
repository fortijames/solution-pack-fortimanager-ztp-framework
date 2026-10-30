| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Validate Data

| | |
| --- | --- |
| Category | ZTPF |
| Trigger Key | `ZTPF Validate Data` |
| Running Playbook | `> running step - ZTPF Validate Data` |

## Summary

Gathers data from the device record and/or the output of earlier steps in the run and stores it on the step for evaluation.

## Script Payload

YAML with a `step_data:` map — the same structure used by [Diff Step Output](./diff_step_output.md), but entries can be named anything: each gathered value is stored under its entry name. Each entry selects a source — the device record or an earlier step in the run group — and a `path` into its data.

The payload below shows every supported option with placeholder values, ready to copy into a record and adjust:

```yaml
step_data:
  system_status:
    step_number: 1        # select the step by ONE of:
    step_name: ""         #   step_number, step_name, action_id,
    action_id: ""         #   action_name, or action_uuid
    action_name: ""
    action_uuid: ""
    rungroup_id: ""       # optional: defaults to the current run group
    revision_back: 1      # optional: read the step's data from a previous revision
    path: output.text     # the step field to read
  routing_table:
    step_number: 2
    path: output.text
```

Only one selector per entry needs a value; the rest can be left empty or removed.

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - ZTPF Validate Data`.
2. That playbook parses the script payload with `> parse step data yaml script and get data` and gathers each entry through `> find step data for device`.
3. The gathered results are stored as the step's Output Source Data, and the shared post-run playbook renders the output templates, evaluates the Output Status Template, and chains the next step in the run group.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [Wait for Condition](./wait_for_condition.md) |
|------------------------------------------------|------------------------------------------------|
