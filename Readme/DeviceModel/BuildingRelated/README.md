# BuildingRelated: 
It is composed of the following categories of Device Model in related to Building and inheritating properties belong to [Device](https://git.rwth-aachen.de/EBC/Team_BA/projects/n5geh/n5geh.datamodel/-/tree/master/Device)
- [Sensor](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#sensor)
- [Actuator](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#actuator)
- [Controller](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#controller)
     - [PID](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#pid)
- [RVK](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#rvk)
### Sensor
A device that detects and responds to events or changes in the physical environment such as light, motion, or temperature changes. [SAREF](https://w3id.org/saref#Sensor)
-   `id` : Unique identifier.
-   `type` : Entity type. It must be equal to `Sensor`.
-  `loggingInterval`: 
     -  Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `loI`
     -  Attribute metadata:
        - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional
- `locatedIn`: Place of Sensor
     -  Attribute type: `Relationship`. 
     - Value: object of [Building](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), [Room](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), and [Zone](https://github.com/N5GEH/SARGON/tree/master/Readme/Building)
     -   Mandatory
- `readableName` : Human readable name of Device if it has
     - Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `nam`
- `writable`: if sensor is able to be written
     -  Attribute type: `Property`. 
     - Value: [Boolean](https://schema.org/Boolean)
     -   Optional
     -   Abbriviation: wri
 - `sampleRate`: Rate of sample values
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `sam`
     -  Attribute metadata:
        - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional
- `sampleInterval`:Interval to send sample values
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: saI
      -  Attribute metadata:
         - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional    
- `listening`: if sensor is able to listen to the commands
     -  Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)    
     -   Optional
     -   Abbriviation: `lis`    
- `subCategory`: to track device model categories
     -  Attribute type: `Relationships`. 
     -  Value: object of [SubCategory](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel)
     -   Optional
- `hasChannel`: 
     -  Attribute type: `Property`.  [Channel](https://sargon-n5geh.netlify.app)
     -  Value: [Text](https://schema.org/Text)
     -  Optional
     - ( Angle, Frequency, Maqnititute, Rocf, TimeStamp)
- `isMeasuredIn`: 
     -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     - (Currency, Energy, Pressure, Power, Template, ..)
- `address` : Location of this device represented by a GeoJSON geometry of
    type point.
     -   Attribute type: `GeoProperty`. `geo:json`.
    -   Attribute metadata:
        -   `Type`: [Text](https://schema.org/PostalAddress)
        -   `addressLocality`: locality [Text](https://schema.org/Text)
        -   `addressCountry`: Country [Text](https://schema.org/Text)
        -   `postalCode` :  Post code [Text](https://schema.org/Text)
        -   `streetAddress`: Street address [Text](https://schema.org/Text)
    -   Optional


### Example
```json
{
  "id": "urn:ngsi-ld:Sensor:01",
  "type": "Sensor",
  "readableName": {
    "type": "Property",
    "value": "KNX Gateway knxip://137.226.249.67:3671"
  },
  "controlProperty": {
    "type": "Relationship",
    "object": "urn:ngsi-ld:Property:Tempreture"
  },
  "soppurtedNetwork":{
    "type": "Property",
     "value": "KNX"
  },
  "loggingInterval":{
    "type": "Property",
    "value": "2s"
  },
   "locatedIn":{
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Building:01",
            "urn:ngsi-ld:Zone:02",
            "urn:ngsi-ld:Room:01"
        ]
    },
  "address": {
    "type": "Property",
    "value": {
      "type": "https://schema.org/PostalAddress",
      "addressLocality": "London",
      "addressCountry": "UK",
      "postalCode": "EC4N 8AF",
      "streetAddress": "25 Walbrook"
    }
  },
 "@context": [
        "https://raw.githubusercontent.com/Maliheh-Haghgoo/N5GEH/master/Core-Context.NGSILd.jsonld",  
        "https://raw.githubusercontent.com/Maliheh-Haghgoo/N5GEH/master/Device.jsonld" ]
 
}

```
### Actuator
 A device responsible for moving or controlling a mechanism or system. [Actuator](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#actuator).
-   `id` : Unique identifier.
-  `type` : Entity type. It must be equal to `Sensor`.
-  `hasSensor`: refer to connected Sensor
     -  Attribute type: `Relationship`.
     - Value: object of [Sensor](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel/BuildingRelated#sensor)
     -   Optional
- `locatedIn`: Place of Actuator
     -  Attribute type: `Relationship`. 
     - Value: object of [Building](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), [Room](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), and [Zone](https://github.com/N5GEH/SARGON/tree/master/Readme/Building)
     -   Mandatory
- `readableName` : Human readable name of Device if it has
     - Attribute type: `Property`.
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `nam`
- `writable`: if sensor is able to be written
     -  Attribute type: `Property`. 
     - Value: [Boolean](https://schema.org/Boolean)
     -   Optional
     -   Abbriviation: wri
 - `sampleRate`: Rate of sample values
     -  Attribute type: `Property`.
     - Value : [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `sam`
     -  Attribute metadata:
         - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional    
- `sampleInterval`:Interval to send sample values
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: saI
     -  Attribute metadata:
        - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional
- `listening`: if sensor is able to listen to the commands
     -  Attribute type: `Property`. 
     -  Value:[Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `lis`
- `subCategory`: to track device model categories
     -  Attribute type: `Relationships`.  object of [SubCategory](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel)
     -   Optional
- `hasChannel`: to define channel [Channel](https://w3id.org/saref#Channel) 
     -  Attribute type: `Property`.
     -  Value:[Text](https://schema.org/Text)
     -  (Angle, Frequency, Maqnititute, Rocf, TimeStamp)
     -   Optional
- `isMeasuredIn`: A relationship identifying the unit of measure used for a certain entity. [SAREF](https://w3id.org/saref#isMeasuredIn)
     -  Attribute type: `Property`.  
     -  Value: [Text](https://schema.org/Text)
     -  (Currency, Energy, Pressure, Power, Template, ..)
     -   Optional
-  `address` : Location of this device represented by a GeoJSON geometry of  type point.
     -   Attribute type: `GeoProperty`. `geo:json`.
    -   Attribute metadata:
          -   `Type`: [Text](https://schema.org/PostalAddress)
          -   `addressLocality`: locality [Text](https://schema.org/Text)
         -   `addressCountry`: Country [Text](https://schema.org/Text)
         -  `postalCode` :  Post code [Text](https://schema.org/Text)
         -   `streetAddress`: Street address [Text](https://schema.org/Text)
    -   Optional

### Example
```json
{
"id": "urn:ngsi-ld:Actuator:valve1",
"type": "Actuator",
"locatedIn":{
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Building:01",
            "urn:ngsi-ld:Zone:02"
        ]
    },
 "hasSensor": {
        "type": "Relationship",
        "object":"urn:ngsi-ld:Sensor:01"
    }
},
 "@context": [
        "https://raw.githubusercontent.com/Maliheh-Haghgoo/N5GEH/master/Core-Context.NGSILd.jsonld",  
        "https://raw.githubusercontent.com/Maliheh-Haghgoo/N5GEH/master/Device.jsonld" ]
 
}

```
### Controller
 A device responsible for controlling actuators and sensors 
-   `id` : Unique identifier.
-  `type` : Entity type. It must be equal to `Controller`.
-  `connectedSensor`: refer to te connected sensor
     -  Attribute type: `Relationship`. 
     -  Value: object of [Sensor](https://w3id.org/saref#Sensor)
     -   Mandatory
- `connectedActuator`: refer to te connected sensor
     -  Attribute type: `Relationship`.
     - Value: object of [Actuator](https://w3id.org/saref#Actuator)
     -   Mandatory
- `locatedIn`: Place of Controller
     -  Attribute type: `Relationship`.
     - Value: object of [Building](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), [Room](https://github.com/N5GEH/SARGON/tree/master/Readme/Building), and [Zone](https://github.com/N5GEH/SARGON/tree/master/Readme/Building)
     -   Mandatory
- `setValue` : set value to controller sensor 
     - Attribute type: `Property`.
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `seV`
     -  Attribute metadata:
        - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional     
- `ipAddress` : IP Address of controller 
     - Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `ipA`
- `controllAsset` : IP Address of controller 
     - Attribute type: `Property`.
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `coA`
- `supplierName` : Name of supplier
     - Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbrivia`tion: `suN
- `source` : source of data
     - Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `sou`
- `writable`: if sensor is able to be written
     -  Attribute type: `Property`. 
     - Value: [Boolean](https://schema.org/Boolean)
     -   Optional
     -   Abbriviation: wri
 - `sampleRate`: Rate of sample values
     -  Attribute type: `Property`.
     -  Value : [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `sam`
     -  Attribute metadata:
         - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional    
- `sampleInterval`:Interval to send sample values
     -  Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: saI
     -  Attribute metadata:
         - isMeasuredIn: 
            -  Attribute type: `Property`. [isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
            -  Value: [Text](https://schema.org/Text)
            -   Optional   
- `listening`: if sensor is able to listen to the commands
     -  Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `lis`
- `subCategory`: to track device model categories
     -  Attribute type: `Relationships`.  
     -  Value: object of [SubCategory](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel)
     -   Optional
- `hasChannel`: to define channel[Channel](https://w3id.org/saref#Channel) 
     -  Attribute type: `Property`.
     - Value: [Text](https://schema.org/Text)
     -  (Angle, Frequency, Maqnititute, Rocf, TimeStamp)
     -   Optional
- `isMeasuredIn`: to track device model categories
     -  Attribute type: `Property`.
     -  Value: [Text](https://schema.org/Text)
     -  (Currency, Energy, Pressure, Power, Template, ..)
     -   Optional
-  `address` : Location of this device represented by a GeoJSON geometry of  type point.
     -   Attribute type: `GeoProperty`. `geo:json`.
    -   Attribute metadata:
          -   `Type`: [Text](https://schema.org/PostalAddress)
          -   `addressLocality`: locality [Text](https://schema.org/Text)
         -   `addressCountry`: Country [Text](https://schema.org/Text)
         -  `postalCode` :  Post code [Text](https://schema.org/Text)
         -   `streetAddress`: Street address [Text](https://schema.org/Text)
    -   Optional

### Example
```json
{
 give it soon
}


```
### PID
 A controller device for buildiing related area. It uses properties of [Controller](https://github.com/N5GEH/SARGON/blob/master/Readme/DeviceModel/BuildingRelated/README.md#controller) and [Device](https://github.com/N5GEH/SARGON/tree/master/Readme/Device)
-   `id` : Unique identifier.
-  `type` : Entity type. It must be equal to `PID`.
-  `kp`: 
     -  Attribute type: `Property`.
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `kp`
-  `ti`: 
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `ti`
-  `td`: 
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `td`
-  `higherLimit`: 
     -  Attribute type: `Property`. 
     - Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `hl`
 -  `lowerLimit`: 
     -  Attribute type: `Property`. 
     -  Value: [Text](https://schema.org/Text)
     -   Optional
     -   Abbriviation: `ll`
 -  `reverseAction`: 
     -  Attribute type: `Property`. 
     -   Optional
     -   Abbriviation: `reA`
- `subCategory`: to track device model categories
     -  Attribute type: `Property`.  object of [SubCategory](https://github.com/N5GEH/SARGON/tree/master/Readme/DeviceModel)
     -   Optional
- `isMeasuredIn`: A relationship identifying the unit of measure used for a certain entity.[isMeasuredIn](https://w3id.org/saref#isMeasuredIn)
     -  Attribute type: `Property`.  
     - Value: [Text](https://schema.org/Text)
     -  (Currency, Energy, Pressure, Power, Template, ..)
     -   Optional
-  `address` : Location of this device represented by a GeoJSON geometry of  type point.
     -   Attribute type: `GeoProperty`. `geo:json`.
    -   Attribute metadata:
          -   `Type`: [Text](https://schema.org/PostalAddress)
          -   `addressLocality`: locality [Text](https://schema.org/Text)
         -   `addressCountry`: Country [Text](https://schema.org/Text)
         -  `postalCode` :  Post code [Text](https://schema.org/Text)
         -   `streetAddress`: Street address [Text](https://schema.org/Text)
    -   Optional

### Example
```json
{
 give it soon
}

```
### RVK

