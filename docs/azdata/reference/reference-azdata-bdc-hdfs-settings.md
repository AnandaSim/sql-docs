---
title: azdata bdc hdfs settings reference
titleSuffix: SQL Server big data clusters
description: Reference article for azdata bdc hdfs settings commands.
ms.prod: sql
ms.technology: big-data-cluster
---

# azdata bdc hdfs settings

Applies to [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

The following article provides reference for the **hdfs settings** commands in the **azdata** tool. For more information about other **azdata** commands, see [azdata reference](reference-azdata.md)

## Commands
|Command|Description|
| --- | --- |
[azdata bdc hdfs settings set](#azdata-bdc-hdfs-settings-set) | Set hdfs service-scope settings.
[azdata bdc hdfs settings show](#azdata-bdc-hdfs-settings-show) | Show hdfs service-scope settings and optionally hdfs settings for specified resources.

## azdata bdc hdfs settings set
Provides the ability to set a service-scoped or resource-scoped setting. Specify the full name of the setting and the value. Does not apply the setting to the running BDC. Run upgrade to do so.
```bash
azdata bdc hdfs settings set --settings -s 
                        
```
### Examples
Disable volume readthrough for the HDFS service 
```bash 
azdata bdc hdfs settings set --settings hdfs-site dfs.datanode.provided.volume.readthrough=false 
``` 
Set the replication factor for the Storage Pool resource
```bash 
azdata bdc hdfs settings set --settings hdfs-site.dfs.replication=3 –resources storage-0 
``` 

### Required Parameters
#### `--settings -s`
Sets the configured value for the provided settings. Multiple settings can be set using a comma separated list.
### Optional Parameters 
#### `--resources` 
Sets the given setting(s) for the provided resource(s). Resources can be listed as a comma separated list. 

### Global Arguments
#### `--debug`
Increase logging verbosity to show all debug logs.
#### `--help -h`
Show this help message and exit.
#### `--output -o`
Output format.  Allowed values: json, jsonc, table, tsv.  Default: json.
#### `--query -q`
JMESPath query string. See [http://jmespath.org/](http://jmespath.org/) for more information and examples.
#### `--verbose`
Increase logging verbosity. Use --debug for full debug logs.

## azdata bdc hdfs settings show
Shows the BDC's `hdfs` service-scope (optionally resource-scope) settings. By default, this command shows user-configured service-scope settings. Filters are available to show all settings (system-managed & configurable), configurable settings, or pending settings. To see a specific service-scope or resource-scope setting, you can provide the setting name. Use “recursive” to show settings for all resources as part of the service. 
```bash

azdata bdc hdfs settings show 
[--settings -s]
[--filter-option -f]  
[--recursive -rec]
[--include-details -i]  
[--description -d]
```
### Examples
Show the user configured HDFS service-scope settings 
```bash
azdata bdc hdfs settings show
```
Show the replication factor for HDFS in the Storage Pool.
```bash
azdata bdc hdfs settings show --settings hdfs-site.dfs.replication --resources storage-0 
```
Show the pending settings changes for the HDFS service-scope and resource-scope settings 
```bash
azdata bdc hdfs settings show --filter-options=pending --recursive --include-details
```
### Optional Parameters 
#### `--filter-options | -f` 
Options to filter which service-level or resource-scope settings are shown, rather than only user configured settings. Filters are available to show all settings (system-managed & user-configurable), all configurable settings, or pending settings. Options: `userConfigured`, `all`, `pending`, `configurable`.
#### `--settings | -s` 
Shows information for the specified setting name(s) 
#### `--include-details | -i` 
Includes additional details for the settings chosen to be shown 
#### `--description | -d` 
Include the description of the setting. Must be used with --include-details 
#### `--resources | -r` 
Shows the setting(s) information for the given resource(s). Resources can be listed as a comma separated list. 
#### `--recursive | -rec` 
Shows the setting information for the given scope (service or service-resource) as well as all lower-scoped components (resources). 

### Global Arguments
#### `--debug`
Increase logging verbosity to show all debug logs.
#### `--help -h`
Show this help message and exit.
#### `--output -o`
Output format.  Allowed values: json, jsonc, table, tsv.  Default: json.
#### `--query -q`
JMESPath query string. See [http://jmespath.org/](http://jmespath.org/) for more information and examples.
#### `--verbose`
Increase logging verbosity. Use --debug for full debug logs.

## Next steps

For more information about other **azdata** commands, see [azdata reference](reference-azdata.md). 

For more information about how to install the **azdata** tool, see [Install azdata to manage SQL Server 2019 big data clusters](../install/deploy-install-azdata.md).
