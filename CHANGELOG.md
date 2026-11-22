## 2.9.0 — 2026-11-21

### Changed
- Rebranded the application as **KERO PERFORMANCE** with the in-app tagline **STRENGTH · FITNESS · SCIENCE**.
- Set the installed home-screen app name to **Kero**.
- Replaced the original barbell icon with the K + performance-swoosh concept; sampled the exact background blue from the approved v2.8.0 icon (#1D4ED8). Existing workout functionality/data model preserved.
- Incremented the service-worker cache from `strength-log-v18` to `strength-log-v20` so installed apps can fetch the updated branding assets.

### Files
- `index.html` — browser title changed to KERO PERFORMANCE; footer updated to v2.9.0.
- `manifest.json` — application name, short name, and description updated.
- `app.js` — home-screen heading and tagline updated.
- `style.css` — minimal typography styling for the heading and tagline.
- `icon.svg`, `icon-192.png`, `icon-512.png` — updated K + swoosh app icon in original v2.8.0 blue (#1D4ED8).
- `sw.js` — cache identifier incremented to `strength-log-v20` for the updated branding and icon assets.
- `IDEAS.md` — recorded the completed branding decision.
- `CHANGELOG.md` — added this entry; all previous history retained.

### Test results
- `node --check app.js` — passed.
- Manifest JSON parse and branding assertions — passed.
- ZIP integrity, exact `my-strength-log/` root, 12-file inventory, version, cache, icon dimensions, and exact original blue (#1D4ED8) checks — passed.
- Browser rendering, installed-PWA update, and physical Android/iOS home-screen label behavior — not verified in this environment.

## 2.8.0 — 2026-11-18

### Changed
- Organized the existing seven per-set tags into three categories: Execution (Good / Form issue), Effort (Easy / Medium / Hard), and Velocity (Fast / Slow).
- Each category is optional and permits at most one newly selected tag. Selections across categories can be combined, such as Good + Hard + Slow.
- Kept RPE as whole numbers 6–10 and RIR as whole numbers 0–4, independently optional. No automatic conversion or validation relationship was added between them.
- Preserved the four-set grid, compact set summary, existing workout data model, and legacy performance compatibility.
- Standardized the ZIP structure to one top-level `my-strength-log/` folder and the release filename convention.

### Files
- `app.js` — grouped tag options and enforced one selection per category when a new choice is made; retained existing RPE/RIR validation and saved tag values.
- `style.css` — compact grouped tag layout in the set-effort modal.
- `index.html` — footer updated to v2.8.0.
- `sw.js` — cache identifier incremented from `strength-log-v17` to `strength-log-v18`.
- `IDEAS.md` — documented the finalized categorized-tag behavior and completion version.
- `CHANGELOG.md` — added this entry; previous history retained.

### Test results
- `node --check app.js` — passed.
- Targeted source assertions — passed for RPE 6–10, RIR 0–4, the three tag categories, category-exclusive selection handling, and retention of the four-set grid.
- Package checks — passed: ZIP integrity, exactly one top-level `my-strength-log/` folder, 12 expected project files, no nested or temporary directories, and matching footer/changelog/ZIP versions.
- Headless Chromium smoke test — attempted but timed out in this environment; modal rendering and interactive selection remain unverified in a browser and on physical devices.

## 2.7.3 — 2026-11-14

### Fixed
- Corrected the app footer to display v2.7.3, matching the delivered build and changelog. The previous v2.7.2 package incorrectly retained v2.7.1 in the footer.
- Incremented the service-worker cache identifier so installed PWAs fetch the corrected footer instead of reusing the prior cached HTML.

### Files
- `index.html` — footer version updated to v2.7.3.
- `sw.js` — cache identifier incremented from `strength-log-v16` to `strength-log-v17`.
- `IDEAS.md` — completion version for the RPE/RIR/tags and full-history-copy feature aligned with v2.7.2; latest update noted.
- `CHANGELOG.md` — documented this patch; all previous entries retained.

### Test results
- `node --check app.js` — passed.
- Targeted assertions for footer version, changelog version, and service-worker cache identifier — passed.
- ZIP integrity test — passed.
- Browser deployment and installed-PWA cache refresh — not verified in this environment; verify after uploading the ZIP.

## 2.7.2 — 2026-11-14

### Changed
- Generalized the successful copy confirmation on the History screen. It no longer names ChatGPT and instead tells the user the copied history can be pasted into any tool or app for review and analysis.

### Files
- `app.js` — replaced the ChatGPT-specific clipboard success message with platform-neutral wording.
- `IDEAS.md` — documented the completed wording refinement under #3.
- `CHANGELOG.md` — documented this patch; previous entries retained.

### Test results
- `node --check app.js` passed.
- Targeted assertion confirmed the old ChatGPT-specific message is absent and the general message is present.
- ZIP integrity check passed.
- Interactive clipboard behavior remains unverified on physical devices.

## 2.7.1 — 2026-11-14

### Changed
- Corrected the delivered RPE/RIR/tags and AI-history build version from v2.7.0 to v2.7.1, as requested. No workout-entry or history behavior was changed in this patch.
- Updated the service-worker cache identifier to `strength-log-v16` so browsers fetch the corrected build assets.

### Files
- `index.html` — footer now displays v2.7.1.
- `sw.js` — cache identifier incremented from `strength-log-v15` to `strength-log-v16`.
- `IDEAS.md` — #3 completion version aligned with the corrected delivered build.
- `CHANGELOG.md` — documented this patch; previous entries retained.

### Test results
- Pending validation for this patch build.

## 2.7.0 — 2026-11-14

### Added / updated
- Added per-set optional RPE (whole numbers 6–10), RIR (whole numbers 0–4), and independently selectable tags: Good, Easy, Medium, Hard, Fast, Slow, and Form issue. Either effort measure may be left blank; no automatic RPE/RIR conversion is performed.
- Kept the existing four-set workout grid and replaced long inline tag text with a compact per-set summary showing RPE, RIR, and tag count. Full details remain available in the per-set modal.
- Added **Copy Full Workout History for AI** to the History screen. It copies every workout, regardless of the active exercise filter, with dates, exercise names, each set's weight and reps/time, RPE, RIR, complete tag names, and workout comments.
- Preserved legacy `performance` values as readable tag details when older records do not contain the new `tags` array. JSON backup/import and CSV export retain the new fields.
- App footer remains v2.7.0; service-worker cache remains `strength-log-v15`.

### Files
- `app.js` — whole-number RPE validation, compact per-set summary, complete-history text generation and clipboard action, legacy compatibility.
- `style.css` — prevent long effort summaries from wrapping in the set grid.
- `IDEAS.md` — mark #3 complete and record the final design and accepted limitations.
- `CHANGELOG.md` — document this build.

### Test results
- `node --check app.js` passed.
- Targeted source assertions passed for whole-number RPE options and validation, RIR validation, compact tag-count summary, all-history export fields, legacy Performance fallback, and history-copy button wiring.
- ZIP integrity check passed.
- Interactive browser and physical Android/iPhone clipboard behavior remain unverified.

## How to use this file

- Add new ideas at the bottom of the matching section, with the next free ID.
- Status values: **Idea** → **Discussed** → **Approved** → **Done** (add the version, e.g. `Done in 1.2.0`).
- An idea is not implemented until its status is **Approved** and a release is requested.
- Every implemented change still follows the project rules (minimal change, `CHANGELOG.md` entry, SemVer, tests, completion report).
- Sections: Features, Fixes, Improvements. IDs are never reused.

## Features

### #1 Rest timer on the main screen
- **Status:** Idea
- **Suggested version type:** MINOR
- Move the timer to the main screen.
- Let the user enter the rest time.
- Play a sound and vibrate when the timer ends.
- **Notes for discussion:**
  - Sound needs a prior tap in browsers.
  - Vibration works on Android Chrome but not on iOS Safari (use sound plus a visual flash there).
  - Base the timer on an end timestamp so it stays accurate if the screen locks.
  - Open questions: remember the rest time between sessions? Auto-start after saving a set?

### #2 Custom exercises
- **Status:** Done in 2.0.0 (follow-up releases 2.1.0, 2.2.0, 2.2.1, 2.3.0)
- **Suggested version type:** MINOR (needs a data-safety plan first)
- Let the user add and enter their own exercises, not only Squat and Deadlift.
- **Notes for discussion:**
  - Keep Squat and Deadlift as built-in defaults and add a separate exercise list so existing records stay untouched.
  - If a database version upgrade is needed, plan a migration and a backup/export step first.
  - Open questions: per-exercise sets/reps (e.g. 4x8)? History kept per exercise?
- **Outcome (as built):**
  - Clean slate for every user: no built-in exercises. Squat and Deadlift are ordinary exercises; existing data was carried over automatically.
  - Add exercises by picking a suggestion or typing a name, with a movement type. The exercise list is stored in localStorage (not IndexedDB), and the suggestion list is in `exercise-presets.js`.
  - Hide keeps all history. Delete removes the exercise and its workouts after typing `DELETE`, with an optional backup download.
  - Bodyweight sets (weight 0) are shown as BW. The Progression table shows weight×reps.
- **Not built:** per-exercise sets and reps (every exercise starts at 4×8; sets can still be added or removed in the workout form). See #16.
- **Releases:** 2.0.0 (custom exercises), 2.1.0 (bodyweight fix, Delete), 2.2.0 (reps in Progression), 2.2.1 (Progression table fit), 2.3.0 (typed DELETE confirmation).

### #3 Per-set effort tracking (RIR and tags)
- **Status:** Idea
- **Suggested version type:** MINOR
- Track RIR (reps in reserve) for each set.
- Keep per-set feel tags: easy / medium / hard, fast / slow, form issues.
- **Notes for discussion:**
  - RIR and easy/medium/hard overlap. Keep both, or make RIR the main field with a label shortcut?
  - Add as new optional fields on each set. Old sets show them blank.
  - Use one-tap buttons so saving a set stays fast. All fields optional.

### #4 Cloud backup and sync
- **Status:** Idea
- **Suggested version type:** Split into steps (see below)
- Let users connect their preferred cloud service: Google Drive, Microsoft OneDrive, and possibly other storage providers.
- Requirements:
  - Secure authorization and permission management.
  - User-selected backup destination.
  - Upload, download, and restore.
  - Conflict handling when workout data changes on multiple devices.
  - Clear separation between backup and full two-way sync.
- **Suggested split:**
  - **#4a Manual export/import file (JSON).** No accounts or servers. MINOR.
  - **#4b Cloud backup/restore** to a user-chosen provider (upload, download, restore only). MINOR.
  - **#4c Full two-way sync** with conflict handling. Possibly MAJOR.
- **Notes for discussion:**
  - A PWA has no server of its own. Google Drive and OneDrive need OAuth sign-in and app registration with each provider, HTTPS hosting, and careful token storage.
  - Restore can overwrite workouts: require a confirmation step and an automatic local backup before any restore.
  - Conflicts (4c): "newest wins" vs. merging by set. Merging is safer but needs unique IDs and timestamps on every set.

### #5 Workout data analysis and graphs
- **Status:** Idea
- **Suggested version type:** MINOR (suggest splitting)
- Visualize weight, repetitions, sets, and training volume over time.
- Show progression and regression for each exercise.
- Track estimated one-repetition maximum (1RM).
- Compare workout sessions and identify trends.
- Summarize consistency, personal records, and training history.
- **Suggested split:** #5a per-exercise charts and PRs; #5b consistency summaries and session comparison.
- **Notes for discussion:**
  - Read-only on existing data, so low risk to records.
  - Works best after #2 and #3 (more exercises and effort data).
  - Estimated 1RM is a formula (e.g. Epley), most reliable for sets of about 10 reps or fewer. Label it "estimated".
  - Charts need a drawing method. A library adds a dependency, which conflicts with the no-new-dependencies rule, so decide explicitly or draw simple charts by hand.

### #6 AI coaching (CSCS and ACSM informed)
- **Status:** Idea
- **Suggested version type:** MINOR, possibly MAJOR for an AI-service version
- Develop an AI coaching capability informed by CSCS principles and American College of Sports Medicine (ACSM) exercise guidelines.
- Analyze workout history and training performance.
- Recommend progressive overload and appropriate weight increases.
- Suggest sets, repetitions, rest intervals, and training frequency.
- Identify plateaus, excessive fatigue, and potential under-recovery.
- Adapt recommendations to training goals, experience, and available equipment.
- Explain recommendations and their supporting rationale.
- **Important:** Recommendations should be evidence-informed, distinguish established guidelines from estimates, and account for safety and individual limitations.
- **Notes for discussion:**
  - **Rules-based coach (offline) first:** fixed, predictable, private, testable logic (e.g. progress weight when all reps are hit at a low RIR).
  - **True AI coach later:** needs an AI service, which means a server or API key, cost, privacy decisions, and sending workout data off the device. A PWA cannot safely hold an API key itself. Comes after cloud work (#4).
  - Tag each recommendation as "Guideline-based" or "Estimate".
  - Show a standing "not medical advice" note and a "stop and see a professional" prompt for pain or injury.
  - Fatigue and under-recovery flags need logged data (RIR, effort, possibly soreness), so #3 is a prerequisite.
  - With little history, say there is not enough data rather than guess.

### #7 Security and privacy
- **Status:** Idea
- **Suggested version type:** Review checklist plus small MINOR items (e.g. app PIN lock)
- Consider securing the app and protecting user privacy.
- **Notes for discussion:**
  - Current baseline is good: data stays on the device, with no accounts and no server.
  - Hosting: HTTPS only, plus security headers such as a Content Security Policy.
  - Code hygiene: no third-party scripts, and safe handling of anything the user types (exercise names, notes) so it cannot inject code.
  - Data protection: optionally encrypt exported files and cloud backups; optional app PIN or lock screen for shared phones (treat as a small separate feature).
  - Privacy: a short privacy policy stating what is stored and where. If selling to people in regions such as the EU, privacy law (e.g. GDPR) applies.
  - Cloud (#4) and AI coaching (#6) send data off the device, so they need consent screens and clear explanations.
  - Do this review before cloud features and before selling.

### #8 Locking the app for sale to individuals
- **Status:** Idea
- **Suggested version type:** MINOR or MAJOR depending on the approach
- Possibly lock the app so it can be sold to individuals (e.g. locked by phone number, a locking/license code, etc.).
- **Notes for discussion:**
  - A PWA runs on the user's own device, so any lock inside the app can eventually be bypassed. It deters casual sharing, not determined copying.
  - Phone-number locking is a poor fit: a PWA cannot read the phone number. It would need SMS verification (paid service, collects phone numbers, privacy burden). Email or a license code is simpler.
  - Options, simplest to strongest:
    1. License key sold through a platform (e.g. Gumroad, Lemon Squeezy) and entered once in the app. Easy, but keys can be shared.
    2. License key checked by a small server, limited to a number of devices. Stronger, but needs a server and upkeep.
    3. App store distribution (e.g. Google Play) wrapping the PWA. The store handles payment and licensing, but adds fees and a larger rewrite.
  - Open questions: one-time price or subscription? Free trial? Devices per buyer? How much copying is acceptable?
  - Depends on hosting and payment decisions, so place late in the build order. Needs #7 first.

### #11 Merge duplicate exercises
- **Status:** Idea
- **Suggested version type:** MINOR
- Let the user say that two exercises are the same (for example "BB press" and "Bench Press") so their history combines.
- **Notes for discussion:**
  - Safe way: record the merge as a link ("B counts as A") and show combined history, without rewriting any workout. It can be undone.
  - Most useful once graphs (#5) exist.

### #13 Recently deleted (undo for exercise deletion)
- **Status:** Idea
- **Suggested version type:** MINOR (needs a data-safety plan first)
- Keep a deleted exercise and its workouts in a holding area for a while so deletion can be undone.
- **Notes for discussion:**
  - Delete is currently permanent (typed `DELETE` confirmation plus an optional backup download). Undo would be the real safety net.
  - Changes how data is stored, so plan it before building. Related to backups (#4).

### #16 Per-exercise default sets and reps
- **Status:** Idea
- **Suggested version type:** MINOR
- Let each exercise have its own default number of sets and reps instead of 4×8 for all.
- **Notes for discussion:**
  - Relates to training type and periodization (strength vs hypertrophy). Fits with effort tracking (#3) and coaching (#6).
  - Open questions: a default per exercise only, or per workout? Show the plan in Progression?

### #17 Timed exercises (Reps or Time)
- **Status:** Done in 2.4.0
- **Suggested version type:** MINOR
- Exercises like planks and wall sits are measured in seconds. Each exercise is measured in Reps or Time, chosen when it is added (suggestions such as Plank come as Time). Timed sets store `seconds` (reps 0); weight 0 is bodyweight and a weight can still be added.
- **Not built:** a hold stopwatch, mm:ss input, a way to change the type of an exercise that already has workouts, and a progression suggestion for timed exercises.

### #18 Distance exercises
- **Status:** Idea
- **Suggested version type:** MINOR
- Farmer's walk, sled push, sprints: measure distance, often together with weight.
- **Notes for discussion:** next measurement type after Time, using its own optional field (e.g. meters) so existing workouts need no conversion. Needs a decision on the unit (metric or imperial) and whether it follows the lb/kg setting.

### #22 Jump or box height
- **Status:** Idea
- **Suggested version type:** MINOR
- Box jumps and other plyometrics. Relevant if power training matters. Lower priority.

### #23 Body measurements
- **Status:** Idea
- **Suggested version type:** MINOR
- Body weight, body fat, soreness or sleep. Not per set: a separate feature, useful for coaching (#6).

## Fixes

_None recorded yet._

## Improvements

### #9 Suggest-an-exercise link
- **Status:** Idea
- **Suggested version type:** MINOR
- Give users a way to ask for exercises missing from the suggestion list.
- **Notes for discussion:**
  - Google Form link preferred: no email address exposed, so less spam risk. A `mailto:` link to a dedicated address is the alternative. Needs your form URL or address.
  - Users can already type any exercise, so this only feeds the suggestion list. Editing the list in `exercise-presets.js` is a small PATCH release.

### #10 Similar-name warning when adding an exercise
- **Status:** Idea
- **Suggested version type:** MINOR
- Warn when a new name is close to an existing one ("Bench" vs "Bench Press"), with "Use existing" and "Add anyway".
- **Notes for discussion:** exact duplicates (ignoring capitals and spaces) are already blocked. This would catch near-misses and keep graphs (#5) accurate.

### #12 Permanent preset IDs and use of movement type
- **Status:** Idea
- **Suggested version type:** MINOR
- Exercises made from the suggestion list already have fixed IDs (for example `bench-press`) and every exercise has a movement type, but nothing uses them yet.
- **Notes for discussion:**
  - Needed for reliable graphs (#5) and coaching (#6). Typed custom exercises have generated IDs, so analysis would treat them as the user's own named exercise.
  - Preset IDs must never be changed or reused.

### #14 Hint that tapping a workout in History opens the edit form
- **Status:** Idea
- **Suggested version type:** PATCH or MINOR
- Editing and deleting a single workout already exist but are not obvious. Add a short hint on the History screen.

### #15 Progression suggestion for bodyweight and lighter exercises
- **Status:** Idea
- **Suggested version type:** MINOR
- The "+10 lb / +5 kg" suggestion is tuned for heavy lifts and is hidden when the top weight is BW.
- **Notes for discussion:** options are a per-exercise weight step, or a rep-based suggestion for bodyweight exercises. Fits with coaching (#6).

### #19 Per-side or per-hand flag
- **Status:** Idea
- **Suggested version type:** MINOR
- Mark a set as per side or per hand (lunges, single-arm rows, dumbbells) so volume is not misread.

### #20 Assisted weight label
- **Status:** Idea
- **Suggested version type:** MINOR
- Today a weight on a bodyweight exercise means added weight. Assisted exercises (assisted pull-up machine) need a way to show the weight is subtracted.

### #21 Tempo
- **Status:** Idea
- **Suggested version type:** MINOR
- Record tempo (for example 3-1-1) as a note or short text field on a set. Low priority.

## Suggested build order

Based on dependencies and risk (not yet approved):

1. #4a Manual export/import (safety net before data-affecting changes; basic JSON export/import already exists in the app, so this step is about extending it)
2. #1 Rest timer
3. #3 RIR and set tags
4. ~~#2 Custom exercises~~ (done in 2.0.0)
5. #7 Security and privacy review (before cloud and before selling)
6. #5 Analysis and graphs
7. #6 AI coaching (rules-based first)
8. #4b Cloud backup, then #4c two-way sync
9. #8 Licensing and locking for sale

## Workflow reminders

- One item per chat, started inside this Project, with the latest project ZIP attached.
- Ask for a plan first (files to touch, risk to workout data), then approve before any code.
- Complex items (#2, #4) get a plan-only chat before the build chat.


### #24 Cross-platform native applications (Android and iOS)
- **Status:** Discussed
- **Suggested version type:** MAJOR (larger migration; may be delivered in staged releases)
- Rebuild My Strength Log as a cross-platform mobile application so it can be distributed as native Android and iOS apps.
- **Recommended approach:** Evaluate Flutter or React Native and select one after a technical proof of concept. Maintain one shared codebase for workout rules and core application behavior, with native platform integrations where needed.
- **Scope to consider:**
  - Preserve existing exercise, workout, set, progression, and timer functionality.
  - Use native local storage and define a safe import/migration path for existing PWA workout records before changing or retiring the PWA.
  - Implement platform-appropriate notifications, sound, and vibration, while respecting Android and iOS background-execution restrictions.
  - Keep offline-first operation.
  - Treat cloud synchronization as a separate feature and design decision; a native rebuild does not automatically provide cloud sync.
  - Consider Apple Health and other platform integrations only as separately approved enhancements.
- **Risks and planning notes:**
  - Do not remove or replace the existing PWA until data migration and feature parity are verified.
  - Test Android and iOS independently; background behavior and store requirements differ.
  - Native distribution introduces app-store accounts, review requirements, signing, release management, and ongoing platform maintenance.
  - Choose the framework only after comparing required APIs, long-term maintenance, accessibility, and development effort.
- **Current decision:** Keep the PWA as the primary product for now. Revisit native cross-platform development when the feature set and user needs justify the migration.


### #25 Background timer alerts and audio coexistence
- **Status:** Idea
- **Suggested version type:** MINOR (PWA investigation first; native Android work may require a separate larger release)
- Improve rest-timer alerts when My Strength Log is minimized or another app is in the foreground, including when Spotify, YouTube, or a podcast is playing.
- **Observed behavior:** On Samsung Android using Chrome, when My Strength Log is minimized and another app is in use, neither sound nor vibration alert is delivered at timer completion. The alert becomes apparent only after reopening My Strength Log.
- **Goals:**
  - Keep the displayed countdown accurate after the browser suspends and resumes the app.
  - Investigate supported Android notification mechanisms as a background alert fallback.
  - Preserve other apps' music or podcast playback; avoid unnecessarily pausing or interrupting audio.
  - Evaluate whether reliable background alerts can be supported in the PWA, and identify any requirements that would instead need native Android background scheduling.
- **Test scenarios:** App foreground; minimized with another app open; screen locked; another audio app playing; return to the app after the timer deadline.
- **Technical note:** An absolute end timestamp helps the countdown recover after suspension but does not itself execute an alert while the page is suspended. Browser notification and background-execution capabilities must be verified on Android Chrome.
- **Current decision:** Investigate PWA-compatible options before committing to native implementation. Keep v2.6.1 behavior unchanged until a specific implementation is approved.

### #3 RPE, RIR, and multi-select set tags
- **Status:** Done in 2.7.0
- **Suggested version type:** MINOR
- Replaced the single-choice Performance input with per-set optional RPE, RIR, and independently selectable tags.
- RPE accepts 6–10 in 0.5 increments; RIR accepts 0–4 as whole numbers. Either measure may be left blank or entered independently. The app does not automatically derive one from the other.
- Tags: Good, Easy, Medium, Hard, Fast, Slow, and Form issue. Multiple tags may be selected for one set.
- The four-set grid remains in place; effort details open in a compact modal for the selected set.
- Existing workouts remain readable: legacy `performance` values are surfaced as tags when no tag array exists. New records retain a legacy performance field for compatibility, while JSON backup/import carries the new fields.
- Accepted limitations: RPE/RIR consistency is not automatically enforced; users may record both even if they do not numerically correspond. The current CSV export includes the new fields, but importing CSV is not supported.

