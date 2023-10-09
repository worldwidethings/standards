# MQTT message standard

| Name | Source | Topic | Payload | Description |
|-|-|-|-|-|
| [Config](#config) | Thing | `wwt/+id/config` | [Config JSON payload](Payload.md#config-json-payload) | Contains the complete configuration of a thing. |
| [Discover](#discover) | App | `wwt/discover` | None | Discover all contained things in a network. |
| [GetConfig](#getconfig) | App | `wwt/+id/getconfig` | None | Request the config from a thing. |
| [SetConfig](#setconfig) | App | `wwt/+id/setconfig` | [SetConfig JSON payload](Payload.md#setconfig-json-payload) | Set an arbitrary subset of mutable configuration properties on a thing. |

## General

## MQTT messages

### Config

The implementation of the [Config message](Message.md#config) for MQTT.

Topic: `wwt/+id/config`  
Payload: [Config JSON payload](Payload.md#config-json-payload)  

### Discover

The implementation of the [Discover message](Message.md#config) for MQTT.

Topic: `wwt/discover`  
Payload: None  

### GetConfig

The implementation of the [GetConfig message](Message.md#getconfig) for MQTT.

Topic: `wwt/discover`  
Payload: None  

### SetConfig

The implementation of the [SetConfig message](Message.md#setconfig) for MQTT.

Topic: `wwt/+id/setconfig`  
Payload: [SetConfig JSON payload](Payload.md#setconfig-json-payload)  
