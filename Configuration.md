# Configuration standards

IoT things have different configuration properties like an identifier, a MAC address or the MQTT broker address. Some of them are writable, others are read-only. This specification aims to standardize their names and possible values.

## General

### Type

The type of each property is defined in regard to the [JSON Schema](https://json-schema.org) standard and its seven [data types](https://json-schema.org/draft/2020-12/json-schema-validation.html#name-type) which are `array`, `boolean`, `integer`, `object`, `null`, `number` or `string`.

### Existence

Properties might be optional. If they are not set and thus not present in a configration object, it means that the thing does not support the corresponding feature. For example, the property `bluetooth` might be missing in a [thing object](#thing), which would mean, that this specific thing does not support bluetooth.

If the thing supports a features but its value is not set, the corresponding configuration property must be present and its value must be `null`. For example, a thing supports WiFi but its SSID is not set yet. The [thing configuration object](#thing) must contain the `wifi` property which must have a present [WiFi configuration object](#wifi) set as its value. The WiFi configuration object must contain an `ssid` configuration property which must have `null` as its value, as long as the SSID is not set. It must be present though, because the thing supports setting an SSID for its WiFi hardware interface.

## Configuration objects

### Thing

The configuration properties of a thing. The contained primitive typed properties serve the purpose of end user properties which can be used to further identify the thing.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [ais](#core-property-ais) | `array` of `object` [AI](#ai) | Optional | Read-only | A list of installed AI's. |
| [bluetooth](#core-property-bluetooth) | `object` [Bluetooth](#bluetooth) | Optional | Read-only | Bluetooth related configuration properties. |
| [ethernet](#core-property-ethernet) | `object` [Ethernet](#ethernet) | Optional | Read-only | Ethernet related configuration properties. |
| [id](#core-property-id) | `string` | Required | Read-only | The globally unique id of the thing. |
| [latitude](#core-property-latitude) | `number` \| `null` | Required | Writable | The latitude the thing is installed at. |
| [location](#core-property-location) | `string` \| `null` | Required | Writable | The name of the location the thing is installed at. |
| [locationType](#core-property-locationType) | `string` \| `null` | Required | Writable | The type of location the thing is installed at. |
| [longitude](#core-property-longitude) | `number` \| `null` | Required | Writable | The longitude the thing is installed at. |
| [monitored](#core-property-monitored) | `string` \| `null` | Required | Writable | The identifier of the monitored object. |
| [monitoredModel](#core-property-monitoredmodel) | `string` \| `null` | Required | Writable | The commercial model name of the monitored object. |
| [monitoredType](#core-property-monitoredtype) | `string` \| `null` | Required | Writable | The type of the monitored object. |
| [mqtt](#core-property-mqtt) | `object` [MQTT](#mqtt) | Optional | Read-only | MQTT related configuration properties. |
| [name](#core-property-name) | `string` \| `null` | Required | Writable | A name identifying the thing inside an organization. |
| [organization](#core-property-organization) | `string` \| `null` | Required | Writable | The name of the organization the thing is part of. |
| [project](#core-property-project) | `string` \| `null` | Required | Writable | The name of the project the thing is part of. |
| [sensors](#core-property-sensors) | `array` of `object` [Sensor](#sensor) | Optional | Read-only | A list of installed sensors. |
| [site](#core-property-site) | `string` \| `null` | Required | Writable | The name of the site the thing is installed at. |
| [system](#core-property-system) | `object` [System](#system) | Required | Read-only | Contains system wide settings. |
| [wifi](#core-property-wifi) | `object` [WiFi](#wifi) | Optional | Read-only | WiFi related configuration properties. |

#### Thing property `ais`

A list of installed AI's.  

Type: `array` of `object` [AI](#ai)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if empty
- Must not be null

#### Thing property `bluetooth`

Bluetooth related configuration properties.  

Type: `object` [Bluetooth](#bluetooth)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if the thing does not support Bluetooth
- Must be present if the thing supports Bluetooth

#### Thing property `ethernet`

Ethernet related configuration properties.  

Type: `object` [Ethernet](#ethernet)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if the thing does not support Ethernet
- Must be present if the thing supports Ethernet

#### Thing property `id`

The globally unique id of the thing.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 5 characters

#### Thing property `latitude`

The latitude the thing is installed at.  

Type: `number` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a value between -90 and 90

#### Thing property `location`

The name of the location the thing is installed at.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `locationType`

The type of location the thing is installed at.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `longitude`

The longitude the thing is installed at.  

Type: `number` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a value between -180 and 180

#### Thing property `monitored`

The identifier of the monitored object.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `monitoredModel`

The commercial model name of the monitored object.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `monitoredType`

The type of the monitored object.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `mqtt`

MQTT related configuration properties.  

Type: `object` [MQTT](#mqtt)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if the thing does not support MQTT
- Must be present if the thing supports MQTT

#### Thing property `name`

A name identifying the thing inside an organization.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `organization`

The name of the organization the thing is part of.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `project`

The name of the project the thing is part of.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `sensors`

A list of installed sensors.  

Type: `array` of `object` [Sensor](#sensor)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if empty
- Must not be null

#### Thing property `site`

The name of the site the thing is installed at.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Thing property `system`

Contains system wide settings.  

Type: `object` [System](#system)  
Existence: Required  
Mutability: Read-only  

#### Thing property `wifi`

WiFi related configuration properties.  

Type: `object` [WiFi](#wifi)  
Existence: Optional  
Mutability: Read-only  
Constraints:  

- Must not be present if the thing does not support WiFi
- Must be present if the thing supports WiFi

### AI

Configuration properties for an AI.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [model](#ai-property-model) | `string` | Required | Read-only | The commercial model name of the AI. |
| [slot](#ai-property-slot) | `integer` | Required | Read-only | The slot the AI is installed in. |
| [training](#ai-property-training) | `integer` | Required | Read-only | A number which denotes a series of cohesive AI trainings. |
| [version](#ai-property-version) | `integer` | Required | Read-only | An AI training version number which starts at 1 and is increased by 1 each time a new training of that AI was done. |

#### AI property `model`

The commercial model name of the AI.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### AI property `slot`

The slot the AI is installed in.  

Type: `integer`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must be an unsigned 8 bit integer

#### AI property `training`

A number which denotes a series of cohesive AI trainings. It needs to be unique regarding the system of numbers it resides in.  

Type: `number`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must be an unsigned 32 bit integer

#### AI property `version`

An AI training version number which starts at 1 and is increased by 1 each time a new training of that AI was done.  

Type: `integer`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must be an unsigned 32 bit integer

### Bluetooth

Configuration properties for Bluetooth.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [address](#bluetooth-property-address) | `string` | Required | Read-only | The identifier unique to every bluetooth thing. |

#### Bluetooth property `address`

The identifier unique to every bluetooth thing.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 17 characters

### Ethernet

Configuration properties for Ethernet.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [ip](#ethernet-property-ip) | `string` \| `null` | Required | Read-only | The IP address assigned to the thing. |
| [mac](#ethernet-property-mac) | `string` | Required | Read-only | The MAC address of the Ethernet interface. |

#### Ethernet property `ip`

The IP address assigned to the thing.  

Type: `string` | `null`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 15 characters

#### Ethernet property `mac`

The MAC address of the Ethernet interface.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 17 characters

### MQTT

Configuration properties for MQTT.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [host](#mqtt-property-host) | `string` \| `null` | Required | Writable | The IP address or DNS resolvable network name of an MQTT broker. |
| [messages](#mqtt-property-messages) | `array` of `object` [MQTT message](#mqtt-message) | Required | Read-only | A list of MQTT messages that the thing either sends or receives. |
| [password](#mqtt-property-password) | `string` \| `null` | Required | Writable | The MQTT broker password. |
| [port](#mqtt-property-port) | `integer` \| `null` | Required | Writable | The MQTT broker port. |
| [username](#mqtt-property-username) | `integer` \| `null` | Required | Writable | The MQTT broker username. |

#### MQTT property `host`

The IP address or DNS resolvable network name of an MQTT broker.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### MQTT property `password`

The MQTT broker password.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters
- Must be `null` if not set

#### MQTT property `port`

The MQTT broker port.  

Type: `integer` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must be an unsigned 16 bit integer

#### MQTT property `username`

The MQTT broker username.  

Type: `integer` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters
- Must be `null` if not set

### MQTT message object

Configuration properties for MQTT messages.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [hasPayload](#mqtt-message-property-haspayload) | `boolean` | Required | Read-only | If the MQTT message has a payload. |
| [name](#mqtt-message-property-name) | `string` | Required | Read-only | An identifying name of the MQTT message. |
| [topic](#mqtt-message-property-topic) | `string` | Required | Read-only | The topic of the message. |
| [toThing](#mqtt-message-property-tothing) | `boolean` | Required | Read-only | If the MQTT message is being sent to the thing. |

#### MQTT property `hasPayload`

If the MQTT message has a payload.  

Type: `boolean`  
Existence: Required  
Mutability: Read-only  

#### MQTT property `name`

An identifying name of the MQTT message.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 30 characters

#### MQTT property `topic`

The topic of the message.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### MQTT property `toThing`

If the MQTT message is being sent to the thing.  

Type: `boolean`  
Existence: Required  
Mutability: Read-only  

### Sensor

Configuration properties for a sensor.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
executed. |
| [model](#sensor-property-model) | `string` | Required | Read-only | The commercial model name of the sensor. |
| [port](#sensor-property-port) | `integer` | Required | Read-only | The number of the port the sensor is connected to. |
| [type](#sensor-property-type) | `string` | Required | Read-only | The type of the sensor. |

#### Sensor property `model`

The commercial model name of the sensor.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

#### Sensor property `port`

The number of the port the sensor is connected to.  

Type: `integer`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must be an unsigned 8 bit integer

#### Sensor property `type`

The type of the sensor.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 200 characters

### System

Contains system wide settings.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [country](#core-property-country) | `string` | Required | Writable | The ISO 3361-1 alpha-2 country code the thing is operated in. |
| [firmware](#core-property-firmware) | `string` | Required | Read-only | The commercial name of a firmware. |
| [firmwareVersion](#core-property-firmwareversion) | `string` | Required | Read-only | The installed version of the firmware. |

#### System property `country`

The ISO 3361-1 alpha-2 country code the thing is operated in.  

Type: `string`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must consist of two letters
- Must be one of the [ISO 3361-1 alpha-2 country code](https://www.iso.org/obp/ui)

#### System property `firmware`

The commercial name of a firmware.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of at least 1 character
- Must have a length of at most 200 characters

#### System property `firmwareVersion`

The installed version of the firmware.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must adhere to the [semantic versioning](https://semver.org)
- Must have a length of at least 5 characters
- Must have a length of at most 20 characters

### WiFi

Configuration properties for WiFi.

| Property | Type | Existence | Mutablity | Description |
|-|-|-|-|-|
| [ip](#wifi-property-ip) | `string` \| `null` | Required | Read-only | The IP address assigned to the thing. |
| [mac](#wifi-property-mac) | `string` | Required | Read-only | The MAC address of the WiFi interface. |
| [password](#wifi-property-password) | `string` \| `null` | Required | Writable | The password of the WiFi the thing will connect to. |
| [ssid](#wifi-property-ssid) | `string` \| `null` | Required | Writable | The SSID of the WiFi the thing will connect to. |

#### WiFi property `ip`

The IP address assigned to the thing.  

Type: `string` | `null`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 15 characters

#### WiFi property `mac`

The MAC address of the WiFi interface.  

Type: `string`  
Existence: Required  
Mutability: Read-only  
Constraints:  

- Must have a length of exactly 17 characters

#### WiFi property `password`

The password of the WiFi the thing will connect to.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 63 characters
- Must be `null` if not set

#### WiFi property `ssid`

The SSID of the WiFi the thing will connect to.  

Type: `string` | `null`  
Existence: Required  
Mutability: Writable  
Constraints:  

- Must have a length of at least 1 characters
- Must have a length of at most 32 characters
- Must be `null` if not set
