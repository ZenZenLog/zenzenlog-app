# Changelog

## v1.8.2 — 2026-09-08

Menu bar app and web app 1.8.2.

**The update notice is a button, all of it (bar)**
- The "a new version is available" row looked clickable but only the word
  "Update" at the far right actually was, so you had to hit a target the width
  of one word. The whole row responds now

**Showing times in UTC (web)**
- The switch has moved out of the account menu to sit beside the sessions it
  changes — next to Refresh for freelancers, beside the sessions heading for
  admins. It is a property of how you are reading this page, not of who you are
- It is a real on/off switch now rather than a checkbox, so its state is
  readable at a glance

## v1.8.1 — 2026-09-08

Menu bar app and web app 1.8.1.

**Both menus tell you the same thing (bar)**
- When the server needs a newer version, only the left-click panel said so. The
  right-click panel carried on as though nothing were wrong — and that is the
  one with "Check for Updates…" in it. A refusal visible in one menu and not
  the other reads as a glitch rather than a state
- It now appears in both, says your time is still being recorded on this Mac
  and will upload as soon as you update, and offers a button that installs the
  update there and then

## v1.8.0 — 2026-09-08

Menu bar app and web app 1.8.0.

**Your timezone, where it belongs (web)**
- Pick it from your own account menu — "Timezone: UTC+8 [Change]" — and change
  it whenever you like. Every time on every page follows it immediately
- Timezones are named the same way everywhere: **UTC+1 (CET)** where a
  well-known abbreviation exists, **UTC+8** where none does. The offset comes
  first because it is the part that is never ambiguous — CST is both US Central
  and China Standard, and most zones have no abbreviation at all
- Summer time is handled for you, per region and per date. Vienna reads
  UTC+1 (CET) in January and UTC+2 (CEST) in July; Manila is UTC+8 all year
- An admin can set a starting timezone when creating a freelancer, and the
  freelancer can change it afterwards. Whatever they choose is what the admin
  sees too, because these are that person's working hours

**Show times in UTC (web)**
- A switch in your account menu puts every time on every page into UTC, for
  both admins and freelancers. Useful when two people need to compare notes on
  the same session without arguing about whose clock is right
- It is per-browser, not per-account: switching it changes nothing for anyone
  else, and the page always says which clock you are reading

**Menu bar app**
- Stopped writing diagnostic traces to your Mac. They were left over from
  fixing a specific problem, recorded which apps you switched between, and
  never had an end date

## v1.7.11 — 2026-09-08

Menu bar app 1.7.11.

**"Update" installs the update (bar)**
- The update notice offered a link to the website, which meant downloading,
  unzipping and dragging — work the app has been able to do for itself since
  1.7.6. It now installs the update in place, and the "your app is too old"
  screen does the same, since being refused by the server never stopped the app
  updating itself. The website remains as a fallback if the update service
  cannot be reached
- Neither button draws a stray frame around itself any more. macOS outlines
  buttons it considers focused when Full Keyboard Access is on, tinted with
  that Mac's accent colour, which on a coloured control looked like a glitch

## v1.7.10 — 2026-09-08

Menu bar app and web app 1.7.10.

**The update notice appears when you look for it (bar)**
- The app asked the server about new versions every 30 minutes, so after a
  release you could sit on an old version for half an hour with no notice —
  which reads as the notice being broken rather than slow. It now asks every
  five minutes, and again the moment you open either panel, because that is
  when you are actually asking the question

**Website**
- The (i) beside the download version sits on the line properly now

## v1.7.9 — 2026-09-08

Menu bar app and web app 1.7.9.

**The update notice appears where you go to update (bar)**
- "A newer version is available" showed only in the left-click panel, while
  "Check for Updates…" lives in the right-click one — so the place you go to
  update never mentioned there was anything to update to. The right-click row
  now says "Update to 1.7.9" when there is one, and the whole row is clickable
  edge to edge instead of stopping short of each side

**Website**
- Downloads are a disk image now: open it, drag ZenZenLog to Applications,
  done. A .zip was expanding automatically in Safari and not in other browsers,
  so half of people got an app and half got an archive to hunt down
- The install steps say what to do with the disk image, name the app, and no
  longer explain the menu bar icon — the app introduces itself on first launch
- The (i) beside the download version sits on the line properly

## v1.7.8 — 2026-09-08

Menu bar app and web app 1.7.8.

**The welcome card looks the same on every Mac (bar)**
- The "Got it" button picked up a rectangular frame around it — present on some
  Macs, absent on others, and a different colour again on a third. That was the
  system's focus ring, which macOS draws around the default button when Full
  Keyboard Access is switched on, tinted with whatever accent colour that Mac
  uses. On a card that paints its own colours it looked like a mistake. It is
  gone; Return still dismisses the card

**Checking what the server expects (web)**
- The version policy — the oldest menu bar app accepted, and the newest
  recommended — is now readable at /api/version. It was only ever handed to
  apps that were already signed in, which made "what is required right now?"
  impossible to answer without signing in or reading the source

## v1.7.7 — 2026-09-08

Menu bar app and web app 1.7.7.

**The app notices new versions while it is running (bar)**
- ZenZenLog asked the server which versions it supports only when you signed
  in. Since it launches at login and then sits in the menu bar for days, that
  meant asking once and never again: a newer version could be released and the
  running app would never mention it, unless you happened to sign in afterwards.
  It now re-checks every half hour
- This was only ever the *advisory* notice. Being refused outright has always
  been noticed straight away

## v1.7.6 — 2026-09-08

Menu bar app and web app 1.7.6.

**ZenZenLog updates itself now (bar)**
- Until this release, updating meant noticing there was an update, going to the
  website, downloading, unzipping, dragging to Applications and relaunching —
  for every release, on every Mac. ZenZenLog now checks for updates on its own
  and installs them with one click, like any other Mac app. There is also a
  "Check for Updates…" item in the right-click panel for when you want to ask
- This also fixes a problem that could not be fixed any other way: when the
  server required a newer version, older apps had no way to tell you, because
  the screen that says so only exists in versions that already have it. An app
  that can carry itself forward does not need the old version to cooperate
- Updates are cryptographically signed and verified before installation. An
  altered download is refused

**Smaller things (bar)**
- The privacy policy window opens next to the menu bar panel you opened it
  from, instead of in the middle of the screen

## v1.7.5 — 2026-09-08

Menu bar app and web app 1.7.5.

**Knowing which Mac you are at, accurately (web + bar)**
- 1.7.4 made the timer follow the Mac you are actually working on, but the
  signal behind it was a yes/no answer to "was there input in the last five
  seconds?", asked every fifteen seconds. A Mac only counted if you happened to
  move in the right five-second window — roughly one check in three, even while
  typing steadily. The menu bar app now reports how long it has been since you
  last touched that Mac, so the answer is measured rather than sampled

**The menu bar panel (bar)**
- The privacy entry added in 1.7.4 was wedged against the edge of the panel
  with no spacing. It now sits properly, with an icon and the same chevron the
  panel already uses for things that open, and Quit is aligned with it

## v1.7.4 — 2026-09-08

Menu bar app and web app 1.7.4.

**The Mac you are actually working on gets the timer (web + bar)**
- Starting from the web app could hand recording to a different Mac than the one
  you were sitting at. The screen said "the one you used most recently will log
  the activity", but the server picked whichever Mac had checked in most
  recently — and since every Mac checks in every 15 seconds, that was close to
  arbitrary. It now picks the Mac you have actually been typing on
- Quitting the menu bar app tells the server straight away. It used to keep
  looking available for up to 90 seconds, long enough to be offered as a place
  to record — or to be handed the timer

**The privacy policy is reachable again (bar)**
- The first-run screen has always said the full policy is in the menu bar
  icon's right-click panel. There was no such entry, and the window that would
  have shown it was never opened by anything. It is now there, under
  "Privacy & what's collected"

**Review & submit (web)**
- Nothing expands itself when the page opens. It used to expand a billing
  period for you, which quietly made a claim about which one mattered; opening
  one yourself is what makes it clear where you are
- The Refresh control is a proper button instead of a small line of text that
  was easy to miss entirely

## v1.7.3 — 2026-09-08

Menu bar app and web app 1.7.3. A pass over what happens when the server is
updated, or simply unreachable, while you are recording. The short version:
your recorded time was already safe, but several things around it were not.

**Your saved password survived a bad moment (bar)**
- If the app started while the server was unreachable — mid-update, on a flaky
  connection, or waking somewhere without Wi-Fi — it treated that exactly like a
  wrong password: it signed you out and **deleted your saved credentials**. You
  had to type your password again, and nothing retried on its own. Only a real
  rejection forgets your credentials now; anything else keeps them and retries
  quietly in the background

**Quitting can no longer strand a running session (bar)**
- Quitting with the timer running was supposed to wait for the server to
  confirm the stop. It didn't — it quit regardless, and a stop lost to a network
  blip left your session running on the server, which then blocked submitting
  that whole billing period. The app now stays open and tells you, rather than
  leaving a session you can't see and can't submit

**Finished work keeps trying to upload (bar)**
- Your last few minutes were uploaded once when you pressed stop. If that single
  attempt failed, the work waited until the next launch — by which point the
  server no longer accepted it, and the session could bill nothing at all. It
  now keeps trying for a few minutes
- Work the server explicitly refused is no longer deleted from your Mac. It was,
  which meant the one copy of it disappeared

**An approved session keeps its evidence (web)**
- Approving compacts detailed activity into a summary. The raw rows were deleted
  first and the summary written afterwards, so an interruption in between
  destroyed the detail permanently and left nothing in its place. Both now happen
  together, or neither does

**Honest messages when the server is busy (web)**
- Errors during an update showed up as `Unexpected token '<'`. They now say what
  actually happened
- Pressing Submit and losing the reply reported a failure over something that
  had already succeeded. It now re-reads and shows you the truth
- "Menu-bar companion offline — activity is **not** being logged" was often
  simply wrong: the app records to your Mac whether or not it can reach the
  server. It now says we haven't heard from it recently, and what that does and
  does not mean
- An update notice can no longer miss a re-release of the same version

**Under the hood**
- The server refuses to start without its session key rather than falling back to
  a placeholder, which would have signed everyone out with no explanation
- Submitting a long billing period has more time to finish before giving up
- The app can now recommend a new version without requiring it

## v1.7.2 — 2026-09-08

Menu bar app and web app 1.7.2.

**A session that recorded nothing is no longer billed as if it recorded everything (web + bar)**
- If the menu bar app ran without Accessibility permission, the timer still
  counted and the session was billed for its entire span — lunch, coffee and
  lid-closed sleep at full rate — with no activity to show for it. That was the
  largest over-billing exposure in the product, and it was silent at both ends
- The web app now knows when a session was *supposed* to be recorded. One that
  produced no activity bills **zero** and says so in Review & submit, in plain
  words, with what to do about it
- The menu bar app now warns you the moment it happens: "Not recording — this
  time is not billable", instead of showing a running clock and nothing else

**You have ten minutes of thinking time, not one (bar)**
- Time stopped counting as billable after 60 seconds without keyboard or mouse.
  Reading, a phone call, or a whiteboard was enough to fall off the clock. The
  threshold is now 10 minutes
- Review & submit shows how much time was set aside this way, per session, so
  the gap between the clock you watched and the hours you bill is visible and
  explainable rather than mysterious

**A short welcome, once per version (bar)**
- A menu-bar app with no Dock icon is genuinely hard to find. On first launch of
  each new version, a small card appears beneath the icon — with an arrow
  pointing at where it actually sits in *your* menu bar — covering click,
  right-click, and what stays on your Mac. Once per version, per Mac

**Version checks that actually run (bar + web)**
- The version handshake had never been called in any released version, and the
  "your app is too old" screen could not be reached. When the server did refuse
  an upload, the app said nothing and kept a clock running
- The handshake now runs at sign-in, the refusal is surfaced, and that screen
  now carries a download link and tells you your recorded time is safe and will
  upload once you update
- The server can now advertise a recommended version separately from a required
  one, so a new release can be suggested without blocking anyone

**Smaller things**
- A session holding a single activity says "Remove This Session" rather than
  "Remove entire session (1 activity)", which promised a scope you could not see
- One ordering convention for the version floor: it was declared in two places
  and kept in step by a comment
- The app bundle reported version 1.2.2 to Finder in every release since 1.4.0

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