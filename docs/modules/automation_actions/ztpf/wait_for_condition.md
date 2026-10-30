| [Home](../../../../README.md) / [Modules](../../../modules.md) / [Automation Actions](../../automation_actions.md) |
|-----------------------------------------------------------------------------------------------------------|

# Wait for Condition

| | |
| --- | --- |
| Category | ZTPF |
| Trigger Key | `ZTPF Wait for Condition` |
| Running Playbook | None yet — no trigger key index entry |

## Summary

Holds a step in a Waiting status while a condition is checked at a set interval, letting a run pause until a device or task reaches an expected state.

## Script Payload

<pending example>

## How It Runs

The framework's waiting machinery exists and is used by the firmware upgrade flow, but this Trigger Key does not have an entry in the running trigger key index or a wait-check playbook yet:

1. A step set to **Waiting** with `Step Waiting` true is re-checked on a cycle started by the `> device step (Waiting Timer)` trigger.
2. The `> device step (Waiting)` trigger looks up the step's Trigger Key in its wait-check index and runs the mapped check playbook. If no check is mapped for the key, the wait cannot complete.
3. A check that returns `Waiting` keeps the step waiting; otherwise the step proceeds, or fails.

A wait-check playbook for `ZTPF Wait for Condition` still needs to be built.

## Example

<pending example>

| [Automation Actions](../../automation_actions.md) | [Playbook](../fortisoar/playbook.md) |
|------------------------------------------------|---------------------------------------|
