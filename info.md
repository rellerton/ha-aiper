# Aiper Pool Cleaner & Water Quality Monitor

Bring your Aiper pool cleaner and water quality monitor into Home Assistant. This integration automatically detects and connects to your Aiper cloud account to expose real-time telemetry and safe controls.

## Features
- **Pool Cleaners (Scuba S1, Scuba X1, Surfer S2, Shark):** Live state, battery, cleaning mode controls, clean path preferences, Surfer S2 start/stop, and supported consumable tracking.
- **Water Quality Monitors (HydroComm, W2 Series):** Live pH, ORP (mV), EC (µS/cm), TDS (ppm), Free Chlorine (mg/L), overall Water Quality Score, and bitmask-decoded alarm warnings.

## Configuration

To add the integration to Home Assistant, click the button below:

[![Open your Home Assistant instance and start setting up a new integration.](https://my.home-assistant.io/badges/config_flow_start.svg)](https://my.home-assistant.io/redirect/config_flow_start/?domain=aiper)

Alternatively, follow these manual steps:
1. Open **Settings -> Devices & Services**.
2. Select **Add Integration**.
3. Search for **Aiper Pool Cleaner**.
4. Sign in with the Aiper account used by your mobile app.

---
> This is the rellerton community build, based on the original
> [kmich/ha-aiper](https://github.com/kmich/ha-aiper) project. For advanced
> troubleshooting, security practices, and Lovelace dashboard examples, view
> the full [fork documentation](https://github.com/rellerton/ha-aiper).


## Recent Changes

### v1.3.3
- S1 charging now overrides both an omitted In Water field and an explicitly
  replayed stale wet value; other models remain payload-driven.

### v1.3.2
- Prevented redundant S1 MQTT topics from briefly replaying an older Cleaning
  lifecycle immediately after a current Parked or Charging report.
- S1 charging reports now clear stale In Water state even when the cloud omits
  that field. The inference is limited to the physically validated S1 profile.

### v1.3.1
- Added a capability-gated Estimated Cleaning Time duration sensor, enabled
  initially for the physically validated Scuba S1 profile. It anchors to raw
  cloud runtime, advances locally while cleaning, restores safely across Home
  Assistant restarts, and resets on stop or charging.
- Prevented path/mode capability refreshes from briefly republishing stale
  lifecycle state, and corrected runtime diagnostics lookup.

### v1.3.0
- Added field-tested Scuba S1 support, source-freshness state reconciliation,
  resilient MQTT credential and connection recovery, and persistent clean-path
  settings with independent capability refresh scheduling.

### v1.2.4
- Fixed Scuba S3 reporting charging as "Returning" and full charge as "Charging", which left the charging sensor inverted. Status codes are now interpreted per model; other models are unchanged.

### v1.2.3
- Fixed HACS release notes layout bug by combining custom release notes with GitHub format.

### v1.2.2
- Fixed HACS release notes display timing issue by ensuring the GitHub Release is fully built before clients poll the new tag.

### v1.2.1
- Fixed empty release notes in HACS UI by dynamically injecting CHANGELOG.md snippets into GitHub Release tags.

### v1.2.0
- Removed "Experimental" tags from documentation. All supported models (Surfer S2, Shark, etc.) are now marked as "Verified".
