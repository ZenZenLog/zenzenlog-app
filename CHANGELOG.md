# Changelog

## v1.7.0 — 2026-09-07

Menu bar app 1.7.0. The web app moved continuously from 1.5.3 to 1.6.2 over the
same days; everything since v1.5.2 is collected here.

**Tab switches are sensed, not sampled (bar)**
- Window titles used to be checked every 15 seconds. A tab you visited between
  two checks was never recorded, and its time was filed under the *previous*
  tab — so a page you had already left could appear on your timesheet. Titles
  now register the moment they change, so each tab gets its own row no matter
  how quickly you move. The old 15-second check remains as a safety net for apps
  that announce nothing, and nothing changes on a Mac where Accessibility has
  not been granted

**Review & submit is built around three things, and now looks like it**
- A billing period, the sessions inside it, and the activity inside those, each
  with its own heading, indentation and background. Previously they carried
  almost the same visual weight, which made a billing period's status easy to
  read as a claim about the session inside it
- Sessions are numbered ("Session 2 of 3") under a heading that names how many
  the billing period holds
- Every billing period carries a coloured left bracket: green when you can
  submit it, teal while it is still running, grey while an earlier one comes
  first
- It is called a "billing period" everywhere now, never a bare "period", and
  weekly periods show weekdays — "Mon, Aug 24 – Sun, Aug 30, 2026" — so the
  Monday-to-Sunday shape is visible at a glance
- Opening the page expands the billing period holding your most recent work.
  It used to expand the oldest unsubmitted one, so old work sat open while
  today's stayed hidden

**Billable time and money, front and centre**
- Both now lead the billing period and session headers. Elapsed time is still
  shown, as a note rather than the headline
- Reconciliation uses h:mm:ss throughout, seconds in smaller type — precise
  enough to add up, quiet enough to skim
- The activity table has Active and Inactive columns again (it had briefly
  collapsed to a single "Length"), and a totals row, so the Active column
  visibly adds up to the session's billable figure
- A badge that said only "Waiting" now says "Earlier billing period first", and
  a running billing period says when it closes: "Open until Sep 13"
- The billing period card shows what Submit will actually send, rather than
  totals that included already-submitted work

**Fixes**
- The page could show a finished session as still running: it never re-read
  after loading. It now has a Refresh control, re-reads when you return to the
  tab, and follows a running session on its own
- "Remove" sat beside "Hide activity" and read as though it removed the activity
  view. The activity toggle moved, and the button says what it does: "Remove
  entire session (7 activities)"

## v1.5.2 — 2026-09-04

- **Your unsubmitted work is yours**: your client can no longer see a session's activity until you submit the billing period it belongs to. Until then you can review it, remove whole sessions or single activity rows, and undo — and anything still marked for removal is permanently deleted at submission, never shown to them. This is now enforced by the server, not just hidden in the interface
- **One privacy policy**: the policy lives in one place and the menu-bar app fetches it, so the app and the web can no longer say different things (they already had — one still used the old product name). The app keeps a clearly-labelled offline copy of the two sections that are absolute promises, for when it can't reach the server
- **Policy §5 rewritten** to say plainly when your client sees your work, and to be honest that whoever operates the service can technically reach stored data — no hosted service can claim otherwise. Nothing changed about *what* is collected, so no re-consent is needed; the policy revision date moves, the collection version does not
- **Consistent ordering** (v1.5.1): sessions and activity rows had disagreed about direction. Everything now reads newest-first, matching the menu-bar app
- **Approved sessions keep their full record** (v1.5.1): compacting a session at approval used to drop GAP time — which is billable and was part of the approved amount — and count activity from non-adopted machines, which never is. The evidence shown for a bill now matches the bill
- Versions: bar 1.5.2, web 1.5.2. Server still accepts bar ≥ 1.4.0

## v1.5.0 — 2026-09-02

- **Reconciliation**: you now review a finished billing period before it goes to your client. Remove a whole session, or a single activity row you'd rather not bill, and undo either freely — until you submit. Removed time stops counting toward your total immediately, so privacy costs exactly the minutes it covers
- **Billing periods**: work is grouped into whole periods (weekly by default, or monthly — your admin sets the cadence per freelancer). You submit one period at a time, oldest first, and only once it has finished on the wall clock. Submitting is final: it permanently deletes what you removed and cannot be taken back, and the confirmation spells out exactly what will be destroyed
- **Time zones**: pick your own (defaults to Pacific). Session times display in your clock; period boundaries stay UTC-anchored so everyone shares one billing calendar, and each period card shows its own start and end in your local time
- **Recording fixes (bar)**: stopping the timer from the web used to silently kill the companion's sync loop — the next session then recorded nothing and billed as wall clock. Also fixed: the last segment of every session was being discarded; activity was not followed onto the successor session after an idle/sleep auto-split; switching machines mid-session did not resume logging on the new Mac; and an idle Mac could win the recording token from the one actually in use
- **Billing integrity (server)**: duplicate activity uploads can no longer be counted twice (idempotent ingest with a uniqueness constraint); two near-simultaneous starts can no longer create two overlapping running sessions; merging an idle gap no longer discards the absorbed session's activity; and payouts now price the same active time every screen displays
- Versions: bar 1.5.0, web 1.5.0. The server now requires bar ≥ 1.4.0 (the first version that identifies its machine, which is what makes multi-Mac adoption enforceable). Bar and web share one version number from here on

## v1.4.0 — 2026-09-01

- **Multi-bar support**: the companion now identifies its machine (stable id + hostname). With several Macs online, exactly one records each session (adoption token, server-authoritative, switchable from the web while the timer runs); segments from non-adopted machines are flagged and never billable
- Web always names the machine doing the logging: "Activity is being logged on: <hostname>" while running, list of online companions at start, offline banner names the last-seen machine
- Zero companions online: start stays hard-blocked with the red notice
- Bar popover shows "Activity is being logged on: <hostname>" under the Today header

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