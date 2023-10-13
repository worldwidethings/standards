# Message standard

| Name | Source | Payload | Description |
|-|-|-|-|
| [Config](#config) | Thing | [Config](Payload.md#config) | Contains the complete configuration of a thing. |
| [Discover](#discover) | App | None | Discover all contained things in a network. |
| [GetConfig](#getconfig) | App | None | Request the config from a thing. |
| [SetConfig](#setconfig) | App | [SetConfig](Payload.md#setconfig) | Set an arbitrary subset of mutable configuration properties on a thing. |

## General 

## Messages

### Config

Contains the complete configuration of a thing.

Source: Thing  
Payload: [Config](Payload.md#config)  

- A thing must send a Config message after it booted up.
- A thing must send a Config message when recevice a [Discover message](#discover), a [GetConfig message](#getconfig) or a [SetConfig message](#setconfig).

### Discover

Discover all contained things in a network.

Source: App  
Payload: None  

- Every thing that receives the message will reply with a [Config message](#config).

### GetConfig

Request the config from a thing.

Source: App  
Payload: None  

- The thing will reply with a [Config message](#config).

### SetConfig

Set an arbitrary subset of mutable configuration properties on a thing.

Source: App  
Payload: [SetConfig](Payload.md#setconfig)  

- The thing will reply with a [Config message](#config).
