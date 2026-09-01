# Changelog

## v1.3.0 — 2026-09-01

- **Popover now mirrors the web 1:1**: same Active/Inactive columns, same rows, same ordering, same durations (down to the second) as the web activity breakdown — "your manager sees what you see" is now literal
- **Locked/Sleep**: `loginwindow` activity displays as `Locked/Sleep` everywhere
- **Session separators** in the popover timeline; `+N more in web app` opens the dashboard
- **Bar-offline transparency**: relaunching after a quit/crash records a visible "bar offline" gap row (counts as inactive, never billable); the web shows an amber "companion offline" banner ~90s after the bar stops heartbeating
- **Post-wake recording fix**: activity after unlock was sometimes stuck classified as sleep
- **Renamed**: user-facing "entries" → "sessions" (one timer run = one session)
- **Admin**: unpaid totals and per-entry value now compute from active time (FOCUS+GAP), not raw duration; Active column in entry tables
- Versions: bar 1.3.0, web 1.3.0; server handshake now requires bar ≥ 1.3.0

## v1.2.1 — 2026-08-30

- **Stop & Quit reliability**: app now waits for server to confirm timer stop before terminating (no more orphaned timers)
- **Bar-offline gap detection**: when relaunching and adopting a running timer, records a "bar offline" gap segment for the unlogged period
- **Activity reconciliation**: web dashboard shows logged vs total duration with "Xm had no activity data (bar offline)" warning
- **Today view timestamps**: each activity row shows start time, sorted most-recent first
- **"Earliest unsubmitted" fix**: was silently missing due to fractional-seconds date parsing bug
- **Quit warning dialog fix**: buttons and countdown were frozen (controller was deallocated, timer used wrong run-loop mode)

## v1.2.0 — 2026-08-30

- **Bar heartbeat**: app pings server every 30s while authenticated
- **Pre-start check**: web app warns freelancer if bar isn't running before starting timer
- **Title poll interval**: reduced from 60s to 15s for finer-grained tab tracking
- **Today view**: groups by app|title (each distinct title gets its own row)
- **"Recording" → "Logging your time"**: all user-facing strings updated
- **Popover anchoring**: always uses transparent anchor window (fixes intermittent unanchored popovers)
- **Notarized release**: Developer ID signed, notarized, stapled

## v1.1.0 — 2026-08-30

- **Rebrand to ZenZenLog**: all user-facing strings changed from ZenZenBar
- **Developer ID signing + notarization**: stable TCC grants
- **Popover anchor fix**: correct positioning with auto-hidden menu bar
- **Removed CGWindowList**: no more Screen Recording prompt
- **Stats panel redesign**: 30-day and 7-day breakdown with progress bars
- **Version handshake**: server publishes min/max bar version
- **Hover highlight**: system accent color on clickable panel rows

## v1.0.0 — 2026-08-28

- Initial release. Privacy-first timesheet with menu bar companion.