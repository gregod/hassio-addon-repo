# USB HID to MQTT Addon

This addon processes tokens from card or barcode readers that use a virtual USB keyboard to type number codes followed by an "Enter" key.

## Configuration
Protection mode **must be disabled** as the addon connects directly to the usb device to gain exclusive access.

When starting the addon all input devices with their manufacturer name are printed in the addon log. 
Find your device and set the `device` config entry to the full path (`/dev/input/event{NUMBER}`).

Use `mqtt://homeassistant` as `mqtt_connection_string` to use the homeassitant mqtt broker.
Supply a password with `mqtt://username:password@homeassistant`.

Make sure to set `max_token_length` to a reasonable length slightly exeeding the expected maximum length of tokens read from the device. 

## Supported Devices

The addon was tested with a Neuftech USB RFID Reader, but any USB keyboard device should work.

