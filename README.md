# Kubectl plugin for debugging AKS Windows nodes

TOC

## Objective

Kubectl plugin that will deploy a priviledged Windows pod with shared namespace as the hosting Node. It could provide a Powershell session directly on the Node for further 
debugging and also an hostPath shared folder in order to get the necessary files. 


## Prerequisites

This plugin will use already deployed Powershell scripts for generating Node level logs archive and optional the network capture. For getting the logs, it will deploy azcopy binary
used along with SAS Url to upload the results to Storage Account container. The SAS key needs to be exposed as an environment variable on he system where this script is running.
You can expose with the following command:
```
export SAS="Your SAS Key"
```

## Installation

You download this script from repository and make the file executable 

```
chmod +x ./kubectl-windebug
```

First parameter should be the Windows Node where this Pod should be scheduled. By default, it will only gather logs from the Node level and upload to Storage Account. 
You can choose to also get the network traces you neet to add the flag --netpcap
