| [Home](../../../README.md) / [Modules](../../modules.md) / [Data Sources](../data_sources.md) |
|-----------------------------------------------------------------------------------------------|

# Spreadsheet Attachments

| | |
| --- | --- |
| Type | Spreadsheet Attachments |
| Handled By | `> run metadata source with data` |

## Summary

Finds a CSV or Excel file attachment in FortiSOAR, extracts its rows, applies a search filter, and stores the matching data under the Data Key.

## Script Template

YAML or JSON with the attachment to read and the filter to apply:

```yaml
filename: <attachment file name>   # the CSV or Excel attachment to read
filter: <row filter>               # search applied to the extracted rows
filetags: <tags to find the file>  # accepted but currently not forwarded by the runner
```

## How It Runs

1. `> get jinja_vars from metadata sources for device_id` runs the linked sources in Order Priority and hands each source's script to `> run metadata source with data`.
2. The dispatcher renders the script with the device's jinja_vars (`> render jinja template`), then routes to the Spreadsheet Attachments branch.
3. `> find and return data from csv or excel file attachment` locates the attachment by name, extracts its data, and applies the `filter`.
4. The matching rows are stored under `data.<datakey>`.

## Example

<pending example>

| [Data Sources](../data_sources.md) |
|-------------------------------------|
