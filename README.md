# OpenMachineCore Device Descriptors

Community-Repository für **wiederverwendbare Hardware-Module**.

## 📦 Struktur

vendors/
└── beckhoff/
├── index.yaml
└── modules/
├── bk9100.json # Coupler
├── kl1408.json # 8x Digital Input
└── kl2408.json # 8x Digital Output

text

## 🎯 Konzept

Dieses Repository enthält **nur Modul-Definitionen**.

Die **Composition** (Zusammenstellung) erfolgt:
- Im **Workflow-Editor** (UI)
- In der **Workflow-Definition** (JSON)
- Zur **Laufzeit** durch den Composer

## 🚀 Verwendung im Workflow

Der Workflow-Editor erlaubt dir, Module dynamisch zusammenzustellen:

{
"devices": [
{
"instance_id": "station-01",
"composition": {
"coupler": {
"module": "beckhoff/modules/bk9100",
"ip_address": "192.168.1.100",
"port": 502,
"unit_id": 1
},
"terminals": [
{
"position": 0,
"module": "beckhoff/modules/kl1408",
"prefix": "inputs"
},
{
"position": 1,
"module": "beckhoff/modules/kl2408",
"prefix": "outputs"
}
]
},
"io_mapping": {
"START_BUTTON": "inputs.input_0",
"LED_GREEN": "outputs.output_0"
}
}
]
}

text

## 📋 Verfügbare Module

### Beckhoff

#### Couplers
- **BK9100** - Modbus TCP Bus Coupler ✅

#### Digital I/O
- **KL1408** - 8x Digital Input 24V DC
- **KL2408** - 8x Digital Output 24V DC

#### Analog I/O
- **KL3064** - 4x Analog Input 0-10V _(coming soon)_
- **KL4004** - 4x Analog Output 0-10V _(coming soon)_

## 🤝 Neues Modul beitragen

1. Fork dieses Repository
2. Erstelle `vendors/{vendor}/modules/{model}.json`
3. Validiere gegen `schema/module-v1.json`
4. Update `vendors/{vendor}/index.yaml`
5. Pull Request erstellen

### Modul-Beispiel

{
"module": {
"id": "beckhoff-kl1408",
"vendor": "Beckhoff",
"model": "KL1408",
"type": "input",
"version": "1.0",
"description": "8-channel digital input"
},
"process_image": {
"input_bytes": 1,
"output_bytes": 0
},
"channels": [
{
"id": 0,
"name": "input_0",
"type": "digital_input",
"bit_offset": 0,
"description": "Digital input channel 0"
}
]
}

text

## 💡 Vorteile

✅ **Keine redundanten Definitionen** - Jedes Modul nur einmal  
✅ **Flexible Kombinationen** - Beliebige Reihenfolge im Workflow  
✅ **Community-driven** - Einfach neue Module hinzufügen  
✅ **Version Control** - Module sind versioniert  

## 📝 License

MIT License - Community contributions welcome!