# ZTPF Automation Actions

## Categories 
 - ZTPF
 - FortiSOAR
 - FortiManager

### ZTPF

#### Collect Artifacts

In this example the script payload can be freeform. 
```
Device Data for `{{record.device.name}}` using the following data:
{% for k in data -%}
 - {{k}}
{% endfor -%}
```

The above produces the following script payload. 
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

The data is collected by leveraging the ZTPF Data Templates. 

The running action `output source` of this action will contain `output.script` and the `data` will all be in the standard `data` base of jinja_vars. 
```
{
  "script": "Device Data for `FG3` using the following data:\n- license\n- bgp_peers\n- fortiguard\n- routing_table\n- monitor_interfaces\n- available_interfaces\n- config_router_static\n"
}
```




#### Diff Step Output

In this action the script payload is instructions in YAML that define how to manage the DIFF action. 

Example script payload rendered to search for data from other steps run inside this rungroup. 

```
step_data:
  diffA:
    action_id: 44
    path: output.text
    revision_back: 1
  diffB:
    action_id: 44
    path: output.text
    revision_back: 2
exclude_regex:
  - Time
  - ^\d+$
```

The running action output of this type will 

#### Validate Data