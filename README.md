# Battery Switch

ESP8266 battery connection and inverter capacitor precharge controller with OLED status.

## What it does

Pulses connection/disconnection outputs, runs a 15-second inverter-capacitor precharge sequence, accepts physical override buttons, and displays remembered connection state. The status is commanded/remembered state, not contact feedback.

## Hardware and configuration

- ESPHome entry point: [`battery-switch.yaml`](battery-switch.yaml).
- Board/profile: `nodemcuv2`.
- GPIO assignments, calibration constants and exposed entities are defined in the YAML. Match them to your hardware before use.

## Setup

1. Keep the repository directory structure when copying it to ESPHome Device Builder.
2. Copy `secrets.example.yaml` to `secrets.yaml`; enter your Wi-Fi settings, unique OTA password and API encryption key. Generate an API key with `openssl rand -base64 32`. Set any BSSID/static-network/web-login placeholders for your own installation.
3. Review pins, sensor calibration, network settings and any Home Assistant entity references.
4. Validate with `esphome config battery-switch.yaml`, then build with `esphome compile battery-switch.yaml`. Choose an ESPHome version compatible with the source; the publication check uses ESPHome 2026.9.1.
5. Flash only the intended board after checking its wiring and configuration.

`secrets.yaml` and build outputs are ignored by Git. Fonts referenced with `gfonts://` require download access during preparation/build.

## Source and publication notes

Snapshot of the stored Home Assistant ESPHome source taken on **2026-10-27**. This is not proof of which firmware is currently flashed. Creating this repository does not upload firmware or change a live device.

- Credentials and network settings moved to `!secret` references.
- Installation-local font files replaced with Google Fonts Roboto; display typography may differ.

See [VALIDATION.md](VALIDATION.md) for the publication checks and their limits.
