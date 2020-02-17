# Zemismart Roller Shade Integration
This is a Python script to connect a Raspberry PI to a Zemismart Roller Shade. It listens to an MQTT topic and executes a close or open command based on that topic.

# Requirements

- Python 3+
- pip (to automatically install python dependencies)

# Dependencies
- paho-mqtt
- bluepy
- [Zemismart](https://github.com/GylleTanken/python-zemismart-roller-shade)
- libglib2.0-dev ```sudo apt-get install libglib2.0-dev```

# Install

1. Download or clone the repository:
2. In the directory run ```pip install -r requirements.txt```
3. Configure details in ```rollshade.py``` and then run with ```python rollshade.py```

# Home Assistant Config

Just add a MQTT cover:

```yaml
...
cover:
  - platform: mqtt
    name: "Blinds Bedroom"
    state_topic: "blinds/00:00:00:00:00:00/status"
    command_topic: "blinds/00:00:00:00:00:00"
    qos: 0
    state_open: "on"
    state_closed: "off"
    payload_open: "open"
    payload_close: "close"
    payload_stop: "stop"
    retain: false
    optimistic: false
```

# What Next?

- Get information from the Shade (battery, state, etc..), currently it's just sending command, for open and close.
- ESP32 version - Would prefer to run this in a ESP32 instead of a Raspberry PI
