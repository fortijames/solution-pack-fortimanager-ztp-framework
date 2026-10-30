| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# FortiManager Proxy API

| | |
| --- | --- |
| Type | FortiManager Proxy API |
| Handled By | `> run metadata source with data` |

## Summary

Sends a REST API request through the FortiManager to the device over the management tunnel and stores the response under the Data Key. Useful for FortiGate REST API data — such as monitor endpoints — without creating or running scripts.

## Script Template

YAML or JSON with a `data:` object describing the proxied request:

```yaml
data:
  action: <get, add, update, delete, or exec>
  target:
    - device/<device name>            # the device to proxy to
  resource: <rest api resource on the device>
  payload: <request body for the resource>
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script with the device's jinja_vars (`> render jinja template`), routes to the FortiManager branch, and detects `proxy` in the Type.
3. `> api proxy encapsulation to device` sends `action`, `target`, `resource`, and `payload` through the Manager to the device.
4. The proxy response results are stored under `data.<datakey>`. A non-zero proxy status marks the run as an error with the response message.

## Example

**Example script** (Data Key `routing_table`):

```yaml
data:
  action: get
  target:
    - device/{{record.device.name}}
  resource: /api/v2/monitor/router/ipv4
  payload: {}
```

**Example output** (`data.routing_table`):

```json
[
  { "dst": "10.255.0.0/16", "gateway": "0.0.0.0", "dev": "loopback1" },
  { "dst": "0.0.0.0/0", "gateway": "10.0.0.1", "dev": "port1" }
]
```

The proxied REST response is available in Jinja as `data.routing_table`.

| [Data Sources](../data_sources.md) | [Playbook](./playbook.md) |
|------------------------------------|----------------------------|
