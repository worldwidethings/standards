# Payloads

| Name | Source | Description |
|-|-|-|
| [Config](#config) | Thing | Contains the complete thing config. |
| [SetConfig](#setconfig) | App | Contains an arbitrary thing config subset composed of mutable config properties. |

## Config

This payload contains the complete config of a thing including every mutable and non-mutable configuration property as described in the [configuration standards document](Configuration.md).

### Config JSON payload

The JSON payload is a JSON object which represents the configuration properties of the [thing object](Configuration.md#thing-object).

### Config AWS payload

The AWS payload is a JSON object which has the following structure.

```json
{
    "state": {
        "reported": {
        }
    }
}
```

The property `reported` has a [thing object](Configuration.md#thing-object) as its value.

## SetConfig

This payload contains a subset of mutable [thing configuration](Configuration.md) properties which are to be used to modify the configuration of a thing. Only those configuration properties shall be contained that are to be modified.

### SetConfig JSON payload

The JSON payload is a JSON object which represents a subset of mutable configuration properties of the [thing object](Configuration.md#thing-object).

### SetConfig AWS payload

The AWS payload is a JSON object which has the following structure.

```json
{
    "state": {
        "desired": {
        }
    }
}
```

The property `desired` has a [thing object](Configuration.md#thing-object) as its value which is composed of a subset of mutable configuration properties.
