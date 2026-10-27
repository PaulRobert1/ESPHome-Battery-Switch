# Publication validation

On 2026-10-27, `esphome config battery-switch.yaml` passed with ESPHome 2026.9.1 and temporary generated credentials. The local dependencies were present. Temporary secrets were removed after validation.

Public source was checked for known source credentials and private network identifiers. Firmware compilation, flashing and physical hardware tests were not performed for this publication. Existing calibration/behavior is retained except for the publication changes listed in README.md.

## Existing configuration warnings

- update_interval of 0ms is not supported - coercing to 1ms. A literal 0ms schedule would spin the main loop (the scheduled item would always be due, so the scheduler would never yield back) and trigger a watchdog reset. Set update_interval to a non-zero value such as 1ms or higher. (Custom C++ components that need true run-every-loop behaviour should override loop() with HighFrequencyLoopRequester instead.)
- 'ota' password wastes significant flash and RAM (about 3.5 KB and 60 bytes plus the password on the heap): the device already offers encryption with the 'api' encryption key, which authenticates any uploader that takes it, and a password only matters for uploaders without encryption support; remove 'password' and add 'encryption' under 'ota' so uploads use the key and encryption is required
- Captive portal is enabled but no WiFi AP is configured. The captive portal will not be accessible. Add 'ap:' to your WiFi configuration to enable the captive portal.
