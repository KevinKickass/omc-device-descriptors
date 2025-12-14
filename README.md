## Contribution Guidelines

1. Fork dieses Repository
2. Erstelle Device Profile nach Schema (siehe `schema/device-profile-v1.json`)
3. Validiere mit: `make validate`
4. Erstelle Pull Request

## Device Profile Format

Siehe [Schema Documentation](schema/device-profile-v1.json)

### Beispiel

{
"device_profile": {
"id": "vendor-model-version",
"vendor": "VendorName",
"model": "ModelNumber",
"version": "1.0"
},
"connection": {
"protocol": "modbus_tcp",
"port": 502,
"unit_id": 1,
"poll_interval_ms": 100,
"timeout_ms": 1000
},
"registers": [
{
"name": "example_register",
"address": 40001,
"type": "holding_register",
"data_type": "uint16",
"scale_factor": 1.0,
"unit": "rpm",
"access": "read_write",
"description": "Example register"
}
]
}

text

## Testing

Lokaler Modbus Simulator: [ModbusPal](http://modbuspal.sourceforge.net/)
