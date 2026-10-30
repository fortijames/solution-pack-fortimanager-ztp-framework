| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Collect Artifacts

| | |
| --- | --- |
| Category | ZTPF |
| Trigger Key | `ZTPF Collect Artifacts` |
| Running Playbook | `> running step - ZTPF Collect Artifacts` |

## Summary

Runs a collection or report from the step's rendered script and stores the result on the step. The rendered script itself is kept as the step's Output Source Data under `output.script`, where later steps — such as diffs and reports — can consume it.

## Script Payload

Freeform Jinja-rendered text. There is no required format; the rendered script is stored verbatim as the artifact.

## How It Runs

1. When the step enters **Running**, the generic `> device step (Running)` trigger looks up the Trigger Key in the `ztpf_running_triggerkey_idx` trigger key index and runs `> running step - ZTPF Collect Artifacts`.
2. That playbook finds the device and the step, then stores the step's rendered script as the step's Output Source Data (`output.script`).
3. The step is marked `Complete`, and the shared post-run playbook renders the output templates, evaluates the Output Status Template, and chains the next step in the run group.

## Example

The payload can be freeform:

```
Device Data for `{{record.device.name}}` using the following data:
{% for k in data -%}
 - {{k}}
{% endfor -%}
```

The above renders to the following script payload, which is stored as the step output:

```
Device Data for `FG3` using the following data:
- license
- bgp_peers
- fortiguard
- routing_table
- monitor_interfaces
- available_interfaces
- config_router_static
```

| [Automation Actions](../../automation_actions.md) | [Diff Step Output](./diff_step_output.md) |
|------------------------------------------------|--------------------------------------------|
