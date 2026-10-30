| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# Playbook

| | |
| --- | --- |
| Type | Playbook |
| Handled By | `> run metadata source with data` |

## Summary

Runs a FortiSOAR playbook and stores its output under the Data Key — letting custom playbook logic produce data for rendering. Use it to integrate external systems or compute values with playbook-level steps.

## Script Template

YAML or JSON with the playbook to run and its arguments:

```yaml
id: <playbook uuid>    # the playbook to run
args:                  # arguments passed to the playbook
  <arg name>: <value>
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script with the device's jinja_vars (`> render jinja template`), then routes to the Playbook branch.
3. `> run playbook for metadata` runs the referenced playbook with the rendered `id` and `args`, keyed by the source's Data Key.
4. The playbook's output is stored under `data.<datakey>`.

## Example

<pending example>

| [Data Sources](../data_sources.md) | [Step Output](./step_output.md) |
|------------------------------------|----------------------------------|
