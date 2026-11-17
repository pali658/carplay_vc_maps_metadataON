# Changelog

## v1.4.0 – 2026-11-17
- HOME button opens CarPlay / App-Connect; a second press within 2 s opens the stock home screen;
  on the home screen HOME still switches pages (MU1440 only).

## v1.3.4 – 2026-11-17
- Call info: caller name in the large (artist) line, number in the small (title) line.

## v1.3.3 – 2026-11-17
- Call icon in dark style (green handset on a dark rounded tile).

## v1.3.2 – 2026-11-17
- Call info: caller name and number are told apart by content, so the name is the large first line
  and the number the small second line.

## v1.3.1 – 2026-11-17
- Call info: refresh of the cluster tile only at call start (+1 retry), on caller change and at call end
  (idle cost: one call-state check per second, no extra cluster traffic outside calls).

## v1.3.0 – 2026-11-17
- Call info: tile is refreshed during calls (the original code suspended refreshes).
- Track cover returns right after the call instead of waiting for the next song.

## v1.2.0 – 2026-11-17
- Stuck lane-guidance arrows are cleared once the route advances to the next maneuver.

## v1.1.0 – 2026-11-17
- During a CarPlay call the now-playing tile shows the caller name (or number) and a handset icon.

## v1.0.0 – 2026-11-17
- First release based on CarPlay Maps VC 2.1.0-rc.7.
- Navigation metadata on MU1440 (`printf` → `echo` in the mm-ipod wrapper).
- Installer staging moved from `/ramdisk` to `/mnt/app`.
- AID 10.5 safe areas for Google Maps: idle `(202,48,606,268)`, guiding `(37,48,606,268)`; default Navigation Card = Off.
- Arrival time in time zone Europe/Zurich.
- Status page shows build, metadata state and maintainer.
