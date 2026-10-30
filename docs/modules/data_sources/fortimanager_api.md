| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# FortiManager API

| | |
| --- | --- |
| Type | FortiManager API |
| Handled By | `> run metadata source with data` |

## Summary

Queries the FortiManager through the device's Manager connector using the generic table fetch, and stores the returned table under the Data Key. Typical uses are reading device-side objects — interfaces, routes, policies — at run time so templates and actions can react to live configuration.

## Script Template

YAML or JSON with the table-fetch options. Only `url` is required; the rest are optional:

```yaml
url: <url to fmg api>      # the FortiManager API table URL; Jinja allowed
fields: <fields to return> # optional: list of fields to return
filter: <json-rpc filter>  # optional: filter for the query
loadsub: <0 or 1>          # optional: load sub-objects
options: <extra options>   # optional: extra fetch options
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script with the device's jinja_vars (`> render jinja template`), then routes to the FortiManager branch.
3. `> get fmg table` runs the query with `url`, `fields`, `filter`, `loadsub`, and `options` against the device's Manager connector configuration.
4. The returned table is stored under `data.<datakey>`. A non-zero FortiManager status marks the run as an error with the API message.

## Example

**Example script** (Data Key `ints_loopback`):

```yaml
url: /pm/config/device/{{record.device.name}}/global/system/interface
fields:
  - name
  - ip
filter:
  - - type
    - ==
    - loopback
loadsub: 0
```

**Example output** (`data.ints_loopback`):

```json
{
  "ints_loopback": [
    {
      "ip": [
        "10.255.255.1",
        "255.255.255.255"
      ],
      "oid": 170,
      "name": "SingleLo1",
      "vdom": [],
      "status": "up",
      "allowaccess": [
        "https",
        "ssh"
      ],
      "description": "Test Looopback SingleLo for FG1."
    },
    {
      "ip": [
        "10.255.255.2",
        "255.255.255.255"
      ],
      "oid": 173,
      "name": "SingleLo2",
      "vdom": [],
      "status": "up",
      "allowaccess": [
        "https",
        "ssh"
      ],
      "description": "Test Looopback SingleLo for FG1."
    }
  ]
}
```

The table returned by the query is available in Jinja as `data.ints_loopback` — for example `data.ints_loopback[0].name`.

| [Data Sources](../data_sources.md) | [FortiManager Proxy API](./fortimanager_proxy_api.md) |
|------------------------------------|--------------------------------------------------------|
