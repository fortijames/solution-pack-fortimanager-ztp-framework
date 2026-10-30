| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Diff Step Output

| | |
| --- | --- |
| Category | ZTPF |
| Trigger Key | `ZTPF Diff Step Output` |
| Running Playbook | `> running step - ZTPF Diff Step Output` |

## Summary

Compares the output of two or more earlier steps in the run and stores the diff as this step's result. Commonly used for pre/post checks around an operation such as a firmware upgrade.

## Script Payload

YAML with a `step_data:` map plus optional line filters. Each entry in `step_data` selects an earlier step in the run group — by step number, step name, action ID, action name, or action UUID — and a `path` into that step's data. For a diff, the entries must be named `diffA` (the original) and `diffB` (the new).

The payload below shows every supported option with placeholder values, ready to copy into a record and adjust:

```yaml
step_data:
  diffA:
    # Find step data using one of the action details.
    action_id: <action id>              # The action id can change on import of records. 
    action_uuid: <action uuid>          # The action uuid will not change on import of records. 
    action_name: <action name>
    revision_back: <revision back>      # If multiple steps of the same search exist 1 is the latest and default. 
    # Find step data using one of the action details.
    step_number: <step number>          # Step number of the current rungroup for this device.
    step_name: <step name>              # Step name of the current rungroup for this device.
    # Select data from the step record. If not provided all data available will be returned. 
    path: output.text     # the step field to compare
  diffB:
    # Find step data using one of the action details.
    action_id: <action id>              # The action id can change on import of records. 
    action_uuid: <action uuid>          # The action uuid will not change on import of records. 
    action_name: <action name>
    revision_back: <revision back>      # If multiple steps of the same search exist 1 is the latest and default. 
    # Find step data using one of the action details.
    step_number: <step number>          # Step number of the current rungroup for this device.
    step_name: <step name>              # Step name of the current rungroup for this device.
    # Select data from the step record. If not provided all data available will be returned. 
    path: output.text     # the step field to compare
# Optional regex filters of the output before diff. 
include_regex: 
  - [Vv]ersion
  - [Ll]icense
exclude_regex: 
  - 'Time'
  - '^\d+$'
```

Only one selector per entry needs a value; the rest can be left empty or removed. `include_regex` and `exclude_regex` accept a list of regular expressions applied line by line before the diff runs.

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - ZTPF Diff Step Output`.
2. That playbook parses the script payload with `> parse step data yaml script and get data`; for each entry, `> find step data for device` locates the referenced step in the run group, applies `revision_back`, and extracts the value at `data_path`.
3. `> diff text return json` diffs the collected text blocks and returns the results as JSON.
4. The diff results are stored on the step, and the shared post-run playbook renders the output templates — for example a color-coded diff table — evaluates the Output Status Template, and chains the next step in the run group.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [Validate Data](./validate_data.md) |
|------------------------------------------------|--------------------------------------|
