# USB HID to MQTT Addon

This addon processes tokens from card or barcode readers that use a virtual USB keyboard to type the codes followed by an "Enter" key.

Maintenance Status: Unmaintained / Experimental Software. I am not using this myself anymore but will leave the current state online. If i do push dependency updates they are untested on real hardware.

## Installation
This addon is available through the repository https://github.com/gregod/hassio-addon-repo. See the [Homeassistant Documentation](https://www.home-assistant.io/hassio/installing_third_party_addons/) for installation instructions.

## Configuration
Protection mode **must be disabled** as the addon connects directly to the usb device to gain exclusive access.

When starting the addon all input devices with their manufacturer name are printed in the addon log. 
Find your device and set the `device` config entry to the full path (`/dev/input/event{NUMBER}`).

Use `mqtt://homeassistant` as `mqtt_connection_string` to use the homeassitant mqtt broker.
Supply a password with `mqtt://username:password@homeassistant`.

### All Options

| Option | Description |
| --- | --- |
| `device` | Full path to usb hid device |
| `mqtt_connection_string` | See [hbmqtt documentation](https://github.com/mqtt/mqtt.org/wiki/URI-Scheme) for valid formats |
| `max_token_length` | We will wait for an enter key marking the end of a token. This options marks an upper bound for the token length to prevent overflow within the token if no enter signals are received. |
| `debug` | Set addon log level to debug |
|  `raw_scancodes` | Disable the character translation and post the usb hid scancodes received instead. |
| `grab_device` | Grab exclusive access to the usb device |


## Supported Devices

The addon was tested with a Neuftech USB RFID Reader, but any USB keyboard device should work.

