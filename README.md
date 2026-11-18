# carplay_vc_maps_metadataON

Modifications of **CarPlay Maps VC 2.1.0-rc.7** by [omonob](https://github.com/omonob/VW-MHI2-Carplay-Maps)
for MQB MIB2 High (MHI2) head units with a Virtual Cockpit.

Maintained by [pali658](https://github.com/pali658).

> This repository contains documentation and version history only.
> No installer packages, binaries or firmware files are published here.

**Current version:** v1.3.5

## What it adds

| Feature | Status |
|---|---|
| CarPlay map in the Virtual Cockpit, centred between the gauges (Google Maps calibrated) | ✅ tested |
| Street labels kept above the bottom bar of the cluster | ✅ tested |
| Navigation metadata in the native cluster tile – maneuver arrow, distance, arrival time (Apple Maps and Google Maps) | ✅ tested |
| Now playing – title, artist and album artwork in the cluster | ✅ tested |
| Arrival time shown in local time (Europe/Zurich) instead of UTC | ✅ tested |
| Stuck lane-guidance arrows cleared after the junction | ✅ tested |
| Call info in the now-playing tile – caller name (large) and number (small) with a handset icon during a call | ✅ tested |
| HOME button opens CarPlay | ❌ not possible this way – see changelog v1.4.1 |
| Status page in the GEM menu shows build, metadata state and maintainer | ✅ tested |
| Android Auto | ⚠️ not tested |

## Key fixes against the original rc.7

- **No navigation metadata on MU1440** – the unit has no `printf`, so the mm-ipod wrapper never added the
  route-guidance messages (0x5200–0x5204) to `iap2.cfg` and the iPhone never sent maneuvers.
- **Installer ran out of space** on the 20 MB `/ramdisk` – staging moved to `/mnt/app`, leftovers cleaned.
- **Map position on AID 10.5** – separate safe areas for idle and active guidance, because Google Maps places
  the car at 50 % of the view area when idle and at ~77 % while guiding.
- **Arrival time one hour off** – computed in the unit's UTC default time zone.
- **Lane arrows stuck** – the original stale-lane check was an empty stub.
- **Call tile** – the original code blanked the tile during calls and stopped refreshing it.

## Tested hardware

| Unit (5F) | Cluster | Phone | Result |
|---|---|---|---|
| MU1440 (Škoda) | AID 10.5 (profile 790) | iPhone 14 Pro, Google Maps + Apple Maps | works |

**Android Auto has not been tested.** All changes were developed and verified with Apple CarPlay only;
behaviour with Android Auto is unknown.

Other profiles of the original package (MU1102, MU1367, MU1433, MU1447, AID 12.3) contain the same
changes where applicable but are **untested**. The exact firmware is identified by the size of `lsd.jxe`;
unknown firmware is rejected by the installer before anything is changed.

## Notes

- After installing a new version, reboot the head unit **and** the iPhone (the phone caches the old
  CarPlay identification).
- In the Virtual Cockpit settings page (under the MirrorLink / App-Connect settings) keep
  *Navigation Card* = **Off** – the centring is calibrated for this mode.
- The blue current-street label under the car is drawn by Google Maps itself and cannot be disabled.

See [CHANGELOG.md](CHANGELOG.md) for the full version history.

## Credits and license

- Original project: **CarPlay Maps VC** by omonob (QCDWJ) – MIT License, original notice kept in [LICENSE](LICENSE).
- Modifications: pali658, 2026.
- Handset glyph: Material Design "call" icon (Apache License 2.0).

Use at your own risk. Back up your unit before any modification.
