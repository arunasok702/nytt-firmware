# Nytt firmware releases

Signed firmware for Nytt hubs and nodes, read by the hubs (over-the-air updates), the Nytt
Flasher (USB flashing) and the Nytt app (firmware page). Everything here is signed with Nytt's
private keys (hub: RSA-3072 image signature, nodes: MCUboot ECDSA-P256, channel files:
ECDSA-P256), so these files are safe to publish.

| Path | What |
|---|---|
| `dev/channel.json`, `production/channel.json` | What hubs of that channel should run. Line 1 = signature (hex DER), then the JSON |
| `<channel>/hub/hub-<version>.bin` | Hub firmware (one image, every use case) |
| `<channel>/nodes/<kind>-<version>.bin` | Node firmware (`envnode`, `vibration`) |
| `<channel>/usb/<kind>-<version>/` | Extra files for USB flashing (bootloader, partition table, MCUboot) |
| branch `app` | The Nytt app (`app.json` + APKs) |

Written by `tools/release.py` (firmware) and `tools/app_release.py` (app) in the main (private)
repository. Older layouts (`factories/`, `builds.json`, `manifest.json`, `hub/`, `envnode/`, `usb/`)
were removed on 2026-10-20.
