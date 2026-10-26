# Handoff — Bus Follower page v6.19, channel PRESET (for the receiving Muse)

## What you're getting
One file: `bus-follower-index-v6.19-preset.html` — the complete, current Bus Follower
page (single-file HTML, Leaflet map over an ntfy channel), byte-identical to the
sender's live page. Save it as `index.html` in the bus-follower repo. Nothing to merge.

## The channel is already set — do not change it
The ntfy channel in use is preset in the file (the `HARDCODED_TOPIC` value, the channel
input, and the migration list are all in place). **Make no channel edits.** Anyone
opening this page connects to that channel automatically, and browsers that still hold
an older channel name from the list in the file migrate on their own.

## Ship it
Commit, push to GitHub Pages, wait ~1 minute, and confirm the live page header
reads **v6.19**.

## What's new (v6.18 + v6.19, over the v6.17 you may already have)
- **v6.18 — "School" label:** the PM route's start stop (data letter `S`) renders as
  "School" everywhere the follower prints a label — a wider map pill, "Stop School (13)"
  in status lines, popups, and log lines. Display-only helper; the data letter stays `S`.
- **v6.19 — waypoint dots:** PM stops `0`, `01`, `02` are progress waypoints, not pickup
  stops. They now render as small dots on the route line (green when passed, pulsing ring
  while next, grey if the ride ends first) with the popup "Waypoint — progress point,
  not a stop", instead of numbered badges.
- **v6.19 — label fix:** a stop's AM-number bracket now prints only when that number is
  positive, so labels read "Stop 0", "Stop 01", "Stop 02" instead of "Stop 01 (undefined)"
  or "Stop 0 (0)". Real stops keep theirs ("Stop B (8)", "Stop School (13)").

## Do NOT "clean up" the underlying data
- The letters (`S`, `0`, `01`, `02`, `A`–`L`) and the waypoint stops themselves are
  functional keys: message matching, stop lookups, and the Minutes Behind delay math
  (PM delays are measured at arrivals, including at 0 and 01) all depend on them.
  Only the rendering changed.
- Log lines that quote the driver's own messages stay verbatim on purpose.

## Sanity checks after it goes live (PM tab)
- School is a wide "School" pill; 0/01/02 are dots; A–L are lettered circles.
- Tapping a dot says "Waypoint — progress point, not a stop".
- Status/pill text shows "Stop 01" with no "(undefined)" anywhere.
- The channel field shows the preset channel and the page connects on its own.
- AM tab is completely unchanged (numbered pins 1–13).
