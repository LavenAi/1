# Laven AI - Executor Brief 01

Status: Superseded following the owner's clarification that the deliverable is an actual online startup product. Not dispatched; no Executor is assigned. Retained as a historical development-prototype brief, not the current release assignment. See `startup-launch-plan.md` and `executor-brief-02-production-foundation.md` for current milestones and the prepared replacement assignment. The platform is confirmed as an online mobile/desktop web app.

## Objective

Build a local, interactive prototype of Laven AI that lets the owner evaluate the companion experience before paying for inference or deployment. Deliver a working prototype with evidence of its behavior, not screenshots alone.

The Director owns product decisions, scope, priorities, budget review, and acceptance. The Executor owns implementation and technical verification within this brief. The owner decides material changes to the selected architecture, operating budget, or final product scope.

## Sources and Workspace

- Authoritative specification: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/outputs/blueprint.md`.
- Planned application root: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/work/laven-ai`.
- Report destination: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/outputs/executor-report-01.md`.
- Follow applicable AGENTS.md instructions before editing. Preserve existing files and planning artifacts.
- Use Next.js and TypeScript with the blueprint's planned source structure. Verify compatible package/runtime versions instead of assuming availability.

## Budget and Boundaries

This assignment has no paid-service allowance. Use deterministic mock responses and local demo data. Normal free development tools and project dependencies are acceptable; do not purchase subscriptions, domains, credits, or assets.

Do not connect OpenRouter, Supabase, Google authentication, or Cloudflare deployment in this assignment. Those remain planned integrations, not removed product requirements. Do not create external accounts, publish the site, send messages to other people, or request real API keys.

Use a visible, unobtrusive preview-mode indicator. Do not present mock responses, simulated voice states, fictional voice options, or local settings as verified AI, audio, authentication, or cross-device functionality. Microphone capture and real audio playback are not required for this first assignment.

## Required Prototype

### 1. Conversation

- Original minimalist lavender design, with a central circle and distinct idle/listening/thinking/speaking/paused visual states.
- Responsive mobile and desktop layouts; Thai and English interface choices.
- Collapsed Menu button leading to Conversation, History, and Settings. My Companion and Memory remain inside Settings.
- Openable chat panel: desktop side panel, mobile bottom panel. Show user/AI text, a composer, Send, and readable empty/loading/interrupted states.
- A typed message produces a deterministic mock reply. Sending a new message cancels unfinished mock output and prevents obsolete callbacks from appending later.
- Start, mute/unmute, pause/resume, and stop controls work in the simulated local session. Clearly identify simulation; do not request microphone permission just to animate a listening state.
- Sentence-level prototype captions may be used under Step 182. A hide/show setting must not remove chat text. Do not claim simulated timings are verified speech alignment.
- Keep local simulated session state across in-app navigation. No claim of real concurrent-account metering or cross-device synchronization.

### 2. My Companion

- Initial name Laven; Warm and gentle preset; playfulness 3/5, gentleness 4/5, short replies 2/5; Normal speed.
- Four selected presets, three five-level trait sliders, optional 1,000-character instructions with a counter, gallery selection, demo voice selection, and Slow/Normal/Fast speed choices.
- Autosave valid companion edits locally with visible save state. Keep existing traits when switching presets. Never overwrite unrelated settings in a field update.
- Changes affect subsequent mock replies, preserving the already-started reply's personality/voice-speed baseline.
- Reset personality requires confirmation, restores the initial preset/traits, and clears custom instructions. Preserve name, image, voice, speed, history, and memory.
- A voice-preview demonstration pauses the local session, cancels unfinished local mock processing, and requires explicit Resume afterward. If no actual audio exists, label it as a visual preview rather than offering a fictitious playable recording.
- Use original code-native graphics or already available appropriately licensed assets; document any third-party asset license. No paid image-generation service or proprietary Pingo artwork is required.

### 3. History

- Clearly identified sample conversations, ordered by latest accepted user activity. No search field or voice replay.
- Read retained messages, rename titles, preserve manual names, select multiple conversations, and confirm deletion.
- History deletion preserves separately saved demo memories and summaries.
- Deleting the active conversation stops its simulated session and unfinished work before deletion; no late output may recreate it. Do not automatically start another conversation.
- Viewing, renaming, or editing presentation does not change the history-retention timestamp. Apply the seven-day retention rule to local demo records where persistence is implemented.

### 4. Settings and Memory

- Light/dark/system theme, lavender accent with selectable alternatives, interface language, caption visibility, and the blueprint's selected conversation preference controls.
- Two Memory tabs: Facts/preferences and Conversation summaries. No user-facing memory search.
- Add, inspect, explicitly Save edits, Cancel drafts, and delete demo records. Memory off preserves stored records but excludes them from mock reply personalization.
- Developer diagnostics, if needed, use only the developer's own or synthetic test records. Do not add a private-user monitoring dashboard.
- No in-app feedback form for this release. No account or provider settings should imply a real backend connection.

An onboarding interview can follow after these core screens pass review. It remains part of the selected product, but is not required to demonstrate this first prototype's core controls.

## Acceptance Evidence

The Executor must return:

1. Source code in the planned project directory, a README, lockfile, and exact install/run commands. Document demo persistence and any browser limitations.
2. A working local preview URL and reproducible startup instructions.
3. Build/type-check results and any failures. Do not claim a check passed without its result.
4. Desktop and mobile screenshots with tested viewport sizes, plus a short interaction walkthrough.
5. Meaningful verification of interruption/stale-output rejection, deletion preserving memory, manual-title preservation, memory-off behavior, caption hiding preserving text, and personality reset boundaries. Use tests or reproducible interaction evidence appropriate to the implementation.
6. A report separating implemented prototype behavior, simulated behavior, deferred production integrations, unresolved defects, and any proposed deviations from the blueprint.

Accessibility review must cover keyboard access, visible focus, labelled controls, readable contrast, reduced-motion behavior, and layout without horizontal overflow. Prototype animations must not obscure essential controls.

## Director Review Gate

The Director will inspect the actual prototype and evidence, record defects against the blueprint, and issue focused correction work before moving to real voice integration. Do not substitute static mockups for working interactions or claim the production release is complete.

Before the next integration assignment, verify selected model identifiers and capabilities and prepare a bounded paid-test proposal if funding is needed. The USD 10 monthly ceiling in the blueprint is a planning control, not credit already purchased or permission to spend in this assignment.

## Executor Autonomy

Choose routine implementation details within this scope without asking the owner about each control or component. Record assumptions in the report. Escalate material model/provider changes, increased operating cost, broader private-data access, destructive workspace changes, or contradictions with confirmed requirements to the Director.
