| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# Step Output

| | |
| --- | --- |
| Type | Step Output |
| Handled By | `> run metadata source with data` |

## Summary

Reads data from the steps of a run and stores the gathered values under the Data Key, so later rendering can pull results from earlier steps. It uses the same step-data structure as [Diff Step Output](../automation_actions/ztpf/diff_step_output.md) and [Validate Data](../automation_actions/ztpf/validate_data.md).

## Script Template

YAML with a `step_data:` map. Each entry selects a step — by step number, step name, action ID, action name, or action UUID — and a `path` into that step's data:

```yaml
step_data:
  <entry name>:
    step_number: <step number>       # select the step by ONE of:
    step_name: <step name>           #   step_number, step_name, action_id,
    action_id: <action id>           #   action_name, or action_uuid
    action_name: <action name>
    action_uuid: <action uuid>
    rungroup_id: <run group id>      # optional: scope the search to a run group
    revision_back: <revisions back>  # optional: read a previous revision of the step
    path: <path into the step data>  # the step field to read
    use_data_key: <true or false>    # optional: true stores the value at the root of data.<datakey>
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script and routes to the Step Output branch, passing the rendered payload to `> parse step data yaml script and get data` — the same parser used by Diff Step Output and Validate Data. Each entry is resolved through `> find step data for device`.
3. The gathered values are stored under `data.<datakey>` — under each entry name, or at the root of the key for entries with `use_data_key: true`. An empty result raises a `Missing Step Data` error.

## Example

<pending example>

| [Data Sources](../data_sources.md) | [Spreadsheet Attachments](./spreadsheet_attachments.md) |
|------------------------------------|----------------------------------------------------------|
