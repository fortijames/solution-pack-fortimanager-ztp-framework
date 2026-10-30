| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# Static Data

| | |
| --- | --- |
| Type | Static Data |
| Handled By | `> run metadata source with data` |

## Summary

The simplest Data Source: the script renders to the data itself. Use it for static values, defaults, and site-specific constants. Jinja is still available, so values can also be computed from the device context at run time.

## Script Template

Freeform — any YAML or JSON structure. The rendered result is stored whole under the record's Data Key as `data.<datakey>`:

```yaml
# Any YAML or JSON structure. The rendered result is stored
# under the record's Data Key as data.<datakey>.
<key>:
  <subkey>: <value>
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script with the device's jinja_vars (`> render jinja template`).
3. The Static Data branch stores the rendered result directly as the source's data under `data.<datakey>`.

## Example

**Example script** (Data Key `networks`):

```yaml
site_a:
  network: 10.255.0.0/16
site_b:
  network: 10.255.1.0/24
```

**Example output** (`data.networks`):

```json
{
  "site_a": { "network": "10.255.0.0/16" },
  "site_b": { "network": "10.255.1.0/24" }
}
```

The values are available in Jinja as `data.networks.site_a.network` and so on.

| [Data Sources](../data_sources.md) | [FortiManager API](./fortimanager_api.md) |
|------------------------------------|--------------------------------------------|
