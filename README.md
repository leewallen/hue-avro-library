# Hue Avro Lib

Example for creating Java library that generates Avro Java classes.


## Schemas

### Ct

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Ct",
  "fields": [
    {
      "name": "min",
      "type": "long"
    },
    {
      "name": "max",
      "type": "long"
    }
  ]
}
```

### Control

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Control",
  "fields": [
    {
      "name": "mindimlevel",
      "type": "long"
    },
    {
      "name": "maxlumen",
      "type": "long"
    },
    {
      "name": "colorgamuttype",
      "type": ["null", "string"]
    },
    {
      "name": "colorgamut",
      "type": {
        "type": "array",
        "items": {
          "type": "array",
          "items": "double"
        }
      }
    },
    {
      "name": "ct",
      "type": "my.example.hue.Ct"
    }
  ]
}
```

### Streaming

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Streaming",
  "fields": [
    {
      "name": "renderer",
      "type": "boolean"
    },
    {
      "name": "proxy",
      "type": "boolean"
    }
  ]
}
```

### Capabilities

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Capabilities",
  "fields": [
    {
      "name": "certified",
      "type": "boolean"
    },
    {
      "name": "control",
      "type": "my.example.hue.Control"
    },
    {
      "name": "streaming",
      "type": "my.example.hue.Streaming"
    }
  ]
}
```

### Startup

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Startup",
  "fields": [
    {
      "name": "mode",
      "type": "string"
    },
    {
      "name": "configured",
      "type": "boolean"
    }
  ]
}
```


### Config

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Config",
  "fields": [
    {
      "name": "archetype",
      "type": ["null", "string"]
    },
    {
      "name": "function",
      "type": ["null", "string"]
    },
    {
      "name": "direction",
      "type": ["null", "string"]
    },
    {
      "name": "startup",
      "type": "my.example.hue.Startup"
    }
  ]
}
```

### State

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "State",
  "fields": [
    {
      "name": "on",
      "type": "boolean"
    },
    {
      "name": "bri",
      "type": "long"
    },
    {
      "name": "hue",
      "type": "long"
    },
    {
      "name": "sat",
      "type": "long"
    },
    {
      "name": "effect",
      "type": ["null", "string"]
    },
    {
      "name": "xy",
      "type": {
        "type": "array",
        "items": "double"
      }
    },
    {
      "name": "ct",
      "type": ["null", "my.example.hue.Ct"]
    },
    {
      "name": "alert",
      "type": ["null", "string"]
    },
    {
      "name": "colormode",
      "type": ["null", "string"]
    },
    {
      "name": "mode",
      "type": ["null", "string"]
    },
    {
      "name": "reachable",
      "type": "boolean"
    }
  ]
}
```

### SoftwareUpdate

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "SoftwareUpdate",
  "fields": [
    {
      "name": "state",
      "type": "string"
    },
    {
      "name": "lastinstall",
      "type": "string"
    }
  ]
}
```

### Light

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Light",
  "fields": [
    {
      "name": "id",
      "type": "int"
    },
    {
      "name": "state",
      "type": "my.example.hue.State"
    },
    {
      "name": "swupdate",
      "type": "my.example.hue.SoftwareUpdate"
    },
    {
      "name": "type",
      "type": "string"
    },
    {
      "name": "name",
      "type": "string"
    },
    {
      "name": "modelid",
      "type": "string"
    },
    {
      "name": "manufacturername",
      "type": "string"
    },
    {
      "name": "productname",
      "type": "string"
    },
    {
      "name": "capabilities",
      "type": "my.example.hue.Capabilities"
    },
    {
      "name": "config",
      "type": "my.example.hue.Config"
    },
    {
      "name": "uniqueid",
      "type": "string"
    },
    {
      "name": "swversion",
      "type": "string"
    },
    {
      "name": "swconfigid",
      "type": "string"
    },
    {
      "name": "productid",
      "type": "string"
    }
  ]
}
```
### Lights

```json
{
  "namespace": "my.example.hue",
  "type": "record",
  "name": "Lights",
  "fields": [
    {
      "name": "lights",
      "type": {
        "type": "array",
        "items": {
          "type": "my.example.hue.Light",
          "name": "light"
        }
      }
    }
  ]
}
```

