# Spy

|                |                                       |
| -------------- | ------------------------------------- |
| Name           | Spy                           |
| Version        | v1.0.1                                |
| DockerHub | [beetaone/spy](https://hub.docker.com/r/beetaone/spy) |
| Authors        | Jakub Grzelak                    |

- [Spy](#spy)
  - [Description](#description)
  - [Environment Variables](#environment-variables)
    - [Module Specific](#module-specific)
    - [Set by the beetaone Agent on the edge-node](#set-by-the-beetaone-agent-on-the-edge-node)
  - [Dependencies](#dependencies)
  - [Input](#input)
  - [Output](#output)

## Description

Debugging module displaying all data passing through it in the logs. This module shows only 3 logs:
* all data passing through it (with `info` severity level)
* confirmation that data was output to the next module `Data send.`
* any errors occurred during processing

## Environment Variables

### Module Specific

This module does not have any module specific configuration.


### Set by the beetaone Agent on the edge-node

Other features required for establishing the inter-container communication between modules in a data service are set by beetaone agent.

| Environment Variables | type   | Description                                    |
| --------------------- | ------ | ---------------------------------------------- |
| MODULE_NAME           | string | Name of the module                             |
| MODULE_TYPE           | string | Type of the module (Input, Processing, Output)  |
| EGRESS_URLS            | string | HTTP ReST endpoints for the next module         |
| INGRESS_HOST          | string | Host to which data will be received            |
| INGRESS_PORT          | string | Port to which data will be received            |

## Dependencies

```txt
bottle
requests
```

## Input

Input to this module is:

* JSON body single object, example:

```json
{
    "label-1": 12,
    "label-2": "speed"
}
```

* array of JSON body objects, example:

```json
[
    {
        "label-1": 12,
        "label-2": "speed"
    },
    {
        "label-1": 15,
        "label-2": "volume"
    }
]
```

## Output

Output of this module is exactly the same as the input:

* JSON body single object, example:

```json
{
    "label-1": 12,
    "label-2": "speed"
}
```

* array of JSON body objects, example:

```json
[
    {
        "label-1": 12,
        "label-2": "speed"
    },
    {
        "label-1": 15,
        "label-2": "volume"
    }
]
```