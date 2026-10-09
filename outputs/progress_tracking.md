# Laven AI - Progress Tracking

Last planning update: October 10, 2026.

This is the authoritative task-status and evidence tracker. Scope/dependencies/acceptance are in `task-backlog.md`; decision mapping is in `requirements-coverage.md`; product behavior is in `blueprint.md`. Task numbers are stable references, not strict execution order. Do not duplicate active status tables in another todo file.

## Current Snapshot

| Measure | Current value |
| --- | --- |
| Total tracked tasks | 82 |
| Planned | 70 |
| Ready to assign | 10 |
| In progress | 0 |
| In review | 1 |
| Done with acceptance evidence | 0 |
| Blocked | 1 |
| Numbered blueprint decisions mapped | 182 / 182 |
| Unmapped numbered decisions | 0 |
| Application implementation / live AI / trial deployment | Not started or verified by this planning work |
| External AI spending in this planning work | No paid inference performed |

These counts describe task states, not a weighted product-completion percentage. Mapping 182 decisions is planning coverage, not proof that the app implements them. T064 is post-trial work; T069 is repository alignment.

## Completed Planning Deliverables

- [x] English product blueprint and discovery decisions recorded.
- [x] Startup launch plan and production foundation checklist prepared.
- [x] Build-agent prompt prepared.
- [x] Initial project documents committed and pushed to `LavenAi/1`, branch `main` (initial commit `3d947d2`).
- [x] Small-task backlog and coverage audit prepared, including the audit additions.
- [x] This progress tracker prepared with honest initial states.
- [ ] Requirements coverage reviewed/accepted by the responsible team members (T001).
- [ ] Exact selected provider/runtime capabilities verified (Phase 1).
- [ ] A real protected voice turn observed (Gate B).
- [ ] Full online private trial accepted and rolled out (T063).

## Status Rules

- `planned`: scope exists, but dependencies/assignment are not ready.
- `ready`: documented prerequisites are available and the task can be assigned; execution has not started.
- `in progress`: a responsible person/Executor is actually doing the task.
- `in review`: deliverables/evidence are prepared and await reviewer acceptance.
- `done`: the designated reviewer accepted the task's stated checks; evidence is linked.
- `blocked`: a concrete missing decision/access/capability prevents the remaining acceptance work; identify the smallest required action.

Never mark implementation done from a sketch, generated code, successful build, mocked test, or planned account setup alone. Those can support a task only if they are the evidence that task actually requires. Live-provider and deployed checks must be recorded as such. The Director's planning audit in T001 is in review; no application Executor has been dispatched.

## Task Board

Suggested roles are D = developer, P = product/research, X = UX/conversation, Q = QA/operations. The owner has identified themself as developer. Other roles remain proposed; named task owners and reviewers are unassigned. The task title is a navigation summary; read its full backlog row before starting.

| Task | Work item | Suggested role | Responsible person | Reviewer | Status | Evidence / immediate note |
| --- | --- | --- | --- | --- | --- | --- |
| T001 | Build the effective-requirements index and release checklist; distinguish selected behavior, proposed defaults, superseded decisions, and feasibility gaps | D + P | Director: planning audit only | Unassigned | in review | [Coverage audit](requirements-coverage.md); team review pending |
| T002 | Verify the selected completed-audio STT identifier, request/response contract, formats, limits, errors, and prices | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T003 | Verify the regular LLM identifier, text streaming, usage reporting, cancellation behavior, context limits, and prices | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T004 | Verify the TTS identifier, voices, Thai/English documentation, expression, speed, audio output, timing metadata, cancellation, and prices | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T005 | Verify the selected OpenRouter Parallel Fast search contract, engine/mode, fees, source metadata, and language evidence | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T006 | Verify Next.js on Cloudflare: compatible versions/adapter, streaming, secrets, runtime limits, jobs, and scheduling | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T007 | Verify Supabase sign-in, verified-email handling, owner bootstrap options, and invited-user email delivery requirements | D | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T008 | Assemble funding/setup and cost sheet from verified prices; identify minimum test allowance and source of usage measurements | D + Q | Unassigned | Unassigned | planned | - |
| T009 | Interview three prospective companion users and summarize the strongest needs | P | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T010 | Produce responsive flows and a small lavender design system: Conversation, chat panels, Settings, History, and onboarding | X | Unassigned | Unassigned | ready | Ready for bounded assignment; not dispatched |
| T011 | Write the acceptance scenarios and bug-report template | Q + D | Unassigned | Unassigned | planned | - |
| T012 | Scaffold the application under `work/laven-ai/`, with the verified runtime path, scripts, environment example, and basic checks | D | Unassigned | Unassigned | planned | - |
| T013 | Create the versioned minimal data migrations and account access policies for the first slice, leaving documented extension points | D | Unassigned | Unassigned | planned | - |
| T014 | Implement email/password sign-in, verification, sign-out, and recovery using documented secure defaults | D | Unassigned | Unassigned | planned | - |
| T015 | Implement Google sign-in and consistent app-account identity across supported sign-in methods | D | Unassigned | Unassigned | planned | - |
| T016 | Implement safe owner bootstrap and server/database allowlist eligibility checks | D | Unassigned | Unassigned | planned | - |
| T017 | Persist account companion/settings defaults and validation with account-scoped read/write APIs | D | Unassigned | Unassigned | planned | - |
| T018 | Define session/turn/job identifiers, state transitions, cancellation tokens, and stale-result write guards | D | Unassigned | Unassigned | planned | - |
| T019 | Implement daily active-session usage ledger and admission check, including overlapping sessions and typed playback outside sessions | D | Unassigned | Unassigned | planned | - |
| T020 | Implement monthly AI-spend reservation/reconciliation and provider-usage records | D | Unassigned | Unassigned | planned | - |
| T021 | Build reusable protected provider-call admission and error handling around eligibility, daily rules, monthly budget, and turn identity | D | Unassigned | Unassigned | planned | - |
| T022 | Build the responsive app shell and Conversation screen with avatar container, collapsed menu, and desktop/mobile chat containers | D + X | Unassigned | Unassigned | planned | R001 ball/import container |
| T023 | Build readable user/AI messages and typed Send flow with source/speech metadata separation | D + X | Unassigned | Unassigned | planned | - |
| T024 | Implement transient microphone capture and hold/release input with permission, empty/cancelled recording, and 120-second limit handling | D | Unassigned | Unassigned | planned | - |
| T025 | Implement the verified STT adapter and account-scoped transcript acceptance | D | Unassigned | Unassigned | planned | - |
| T026 | Implement regular LLM reply streaming using current accepted conversation text and baseline saved settings | D | Unassigned | Unassigned | planned | - |
| T027 | Implement TTS, ordered transient playback, speech failures, and originating-surface delivery | D | Unassigned | Unassigned | planned | - |
| T028 | Connect one real held-spoken turn and one real typed reply through guarded STT/LLM/TTS and text persistence | D + Q | Unassigned | Unassigned | planned | - |
| T029 | Deploy the protected slice to authorized cloud staging with basic setup/rollback instructions | D + Q | Unassigned | Unassigned | planned | - |
| T030 | Add continuous VAD capture, the two-second utterance-end timer, resumed-speech extension, and shared recording-limit behavior | D | Unassigned | Unassigned | planned | - |
| T031 | Implement speech/send interruption and cancellation with echo/false-interruption checks | D + Q | Unassigned | Unassigned | planned | - |
| T032 | Implement the distinct mute and mode-switch rules at recording, submitted, thinking, and speaking boundaries | D + Q | Unassigned | Unassigned | planned | - |
| T033 | Implement automatic/manual session start, explicit Resume/Stop, persistent navigation controls, and browser lifecycle pause fallback | D + Q | Unassigned | Unassigned | planned | - |
| T034 | Implement disconnect/reconnect recovery and bounded STT/LLM retry plus current-failed-reply audio retry | D + Q | Unassigned | Unassigned | planned | - |
| T035 | Implement default-on proactive follow-ups with the selected timers, count, mute behavior, and auto-pause | D + Q | Unassigned | Unassigned | planned | - |
| T036 | Coordinate simultaneous sessions, one shared active thread, ordered messages, new-thread/resume/switch semantics, and origin-only audio | D + Q | Unassigned | Unassigned | planned | - |
| T037 | Synchronize saved settings and edits across surfaces with stale-write/conflict handling | D | Unassigned | Unassigned | planned | - |
| T038 | Implement light/dark/system theme, lavender/accent selection, Thai/English UI strings, and caption/startup/search preference controls | D + X | Unassigned | Unassigned | planned | - |
| T039 | Implement My Companion personality/name/custom-instruction controls with autosave and confirmed Reset personality | D + X | Unassigned | Unassigned | planned | - |
| T040 | Prepare a small licensed/original gallery and integrate synced gallery appearance selection | X + D | Unassigned | Unassigned | planned | Local rig import separately in T072/T075 |
| T041 | Implement verified voice catalog, preview, speed selection, and next-reply settings semantics | D + X | Unassigned | Unassigned | planned | - |
| T042 | Implement final reply prompt/style/language assembly and saved-settings precedence | D + X | Unassigned | Unassigned | planned | - |
| T043 | Implement History list/read/resume, activity ordering, topic/date titles, and protected manual renaming | D + X | Unassigned | Unassigned | planned | - |
| T044 | Implement Settings > Memory facts/summaries tabs and account-scoped Add/Edit/Save/Cancel/Delete operations | D + X | Unassigned | Unassigned | planned | - |
| T045 | Implement memory retrieval/learning eligibility: off, retained data, forward-only re-enable, and specific explicit-save exception | D + Q | Unassigned | Unassigned | planned | - |
| T046 | Implement deleted-fact exclusion identity/matching and summary filtering for automatic learning and retrieval | D + Q | Unassigned | Unassigned | planned | - |
| T047 | Implement durable end/inactivity job scheduling, idempotency, retries, budget-paused pending work, and source-state checks | D | Unassigned | Unassigned | planned | - |
| T048 | Implement regular-LLM summary updates and separate fact extraction/conflict replacement through the guarded job path | D + Q | Unassigned | Unassigned | planned | - |
| T049 | Implement seven-day history expiry and source invalidation while retaining eligible saved summaries/facts | D + Q | Unassigned | Unassigned | planned | - |
| T050 | Implement confirmed individual/multi-select history deletion with active-thread cancellation | D + Q | Unassigned | Unassigned | planned | - |
| T051 | Implement one new-thread greeting with eligible personalization and UI-language-before-first-input rules | D + X | Unassigned | Unassigned | planned | - |
| T052 | Finalize the selected friendly interview script and optional language-learning questions | P + X | Unassigned | Unassigned | planned | - |
| T053 | Implement optional AI interview, explicit capture start, saved setup stages, completion-only learning, and optional companion customization | D + X + Q | Unassigned | Unassigned | planned | - |
| T054 | Integrate verified Parallel Fast web search with server toggle, actual-call daily counter, and chat-only grounded citations | D + Q | Unassigned | Unassigned | planned | - |
| T055 | Build owner Trial Access UI and finish immediate cross-surface revocation/reinstatement propagation | D + Q | Unassigned | Unassigned | planned | - |
| T056 | Implement owner per-account current-UTC-day allowance overrides, reset display, and immediate lower-cap behavior | D + Q | Unassigned | Unassigned | planned | - |
| T057 | Implement owner monthly budget/spend view and current-UTC-month cap override | D + Q | Unassigned | Unassigned | planned | - |
| T058 | Implement account deletion confirmation, seven-day restricted pending state, cancellation, and guarded permanent cleanup | D + Q | Unassigned | Unassigned | planned | - |
| T059 | Implement and verify the final word-progress caption path and Show AI captions behavior | D + X + Q | Unassigned | Unassigned | planned | - |
| T060 | Audit end-to-end access, retention, daily/monthly exhaustion, and concurrency with targeted regression cases | D + Q | Unassigned | Unassigned | planned | - |
| T061 | Run the Android Chrome/desktop Chrome voice and visual acceptance matrix; measure actual latency, quality, speed, and authorized costs | Q + D + X | Unassigned | Unassigned | planned | - |
| T062 | Complete trial-domain/email/deployment/recovery operations and environment handoff | D + Q | Unassigned | Unassigned | planned | - |
| T063 | Review private-trial readiness, resolve release blockers, and perform the authorized owner/invitee rollout | P + Q + D | Unassigned | Unassigned | planned | - |
| T064 | Collect manual trial feedback and measured usage, then prepare the wider-launch recommendation | P + Q + D | Unassigned | Unassigned | planned | - |
| T065 | Implement answer-based post-interview preset/image/voice suggestions using real available catalogs and field-by-field acceptance | D + X | Unassigned | Unassigned | planned | - |
| T066 | Implement scoped developer memory-search diagnostics for the developer's own and designated test accounts | D | Unassigned | Unassigned | planned | - |
| T067 | Implement conversational explicit-remember requests and their item-specific persistence/confirmation flow | D + Q | Unassigned | Unassigned | planned | - |
| T068 | Implement contextual expressive TTS direction using the saved per-reply personality baseline | D + X + Q | Unassigned | Unassigned | planned | - |
| T069 | Resolve repository visibility against the earlier private-repository requirement and record the actual Git/GitHub state | D + P | Unassigned | Unassigned | blocked | Public repo vs Step 105 private plan; explicit owner direction pending |
| T070 | Verify the first 2D import format/runtime, local package contract, commercial rights, device support, and resource limits | D + X | Unassigned | Unassigned | ready | Read-only evaluation ready; not dispatched |
| T071 | Build the minimalist lavender ball and its conversation-state controller | D + X | Unassigned | Unassigned | planned | Eyes and shape-changing mouth confirmed Oct 10; styling/synchronization pending |
| T072 | Implement bounded client-local package import, validation, and account-partitioned storage | D | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T073 | Render an authorized compatible rigged 2D model through an isolated runtime adapter | D | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T074 | Connect ball and supported rig speaking motion to actual originating-surface playback | D + Q | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T075 | Add local model import/preview/use/replace/remove/default controls and identity/deletion cleanup | D + X | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T076 | Verify local import privacy, hostile-package limits, persistence, accessibility, and real-device performance | D + Q + X | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T077 | Review first-release ball and optional local rigged-2D import acceptance | D + Q + P | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T078 | Verify first-release Windows floating runtime, supported versions, packaging, costs, and release prerequisites | D + P | Unassigned | Unassigned | ready | Read-only evaluation ready; not dispatched |
| T079 | Define and implement the approved floating client/session bridge and local asset boundaries | D | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T080 | Build the first-release Windows floating companion using the verified runtime | D + X | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T081 | Build the future Android floating companion after a separate milestone is authorized | D | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |
| T082 | Review packaging, permissions, recovery, resource use, and release evidence for selected floating targets | D + Q + P | Unassigned | Unassigned | planned | R001; dependencies/decisions and implementation pending |

## Release Gates

| Gate | Required evidence | Current state |
| --- | --- | --- |
| A - Feasibility | T002-T008: current official model/runtime/auth/email evidence, cost/setup dependencies, material mismatch decisions | Not passed; research not executed |
| B - Real protected voice | T014-T021 and T028-T029: eligible real account, real Thai/English voice pipeline, measured usage/timing, protected staging | Not passed; setup/funding/live evidence missing |
| C - Personalization safety | Memory off/forward-only, explicit remember, deleted-fact exclusions, source expiry/delete guards, concurrent account/session checks | Not passed; implementation/tests pending |
| D - Online private trial | Full selected coverage including T077 avatars, T078 Windows feasibility evidence, and required T082 floating acceptance; final captions/device/voice evidence; auth/domain/jobs/runbook | Not ready; no deployed product or avatar implementation |
| E - Floating targets | T078-T082: confirmed first-release inclusion, selected Windows target, actual cross-app client, permissions, controls, local assets, session/quota guards, packaging/recovery | Not passed; Windows selected, runtime/version/client evidence pending |

Targets that fail measurement remain explicit issues. Sentence captions do not meet the final word-progress requirement, and the three-second target must include the two-second speech-end wait. A material scope/target change needs a recorded owner decision rather than a hidden exception.

## Known Decisions and External Dependencies

| ID | Issue / condition | Affected tasks | Smallest next action |
| --- | --- | --- | --- |
| B01 | Selected OpenRouter identifiers/capabilities and current prices unverified | T002-T005, T025-T028, T041, T054, T059, T068 | Read-only official documentation/model metadata checks, then bounded authorized live tests |
| B02 | Cloudflare runtime/job scheduling and Supabase email/auth setup unverified | T006-T008, T012-T016, T029, T047, T062 | Establish evidenced configuration and actual project/setup access; no provisioning assumed |
| B03 | Actual provider funding/test allowance not established; USD 10 cap is not credit | T008, T028-T029, T041, T054, T061 | Prepare a concrete test allowance from verified prices and obtain actual funding/access before paid calls |
| B04 | Desired domain unpurchased; trial deployment/email/device access still needed | T029, T061-T063 | Prepare real setup/deployment instructions, then the authorized domain/email/device configuration |
| B05 | GitHub repo `LavenAi/1` is public; Step 105 planned private storage | T069, T063 | Record owner's explicit public/private direction; do not change visibility automatically |
| B06 | Accurate Thai word/audio alignment, expressive quality, speed controls, and latency need actual evidence | T004, T028, T041, T059, T061, T068 | Verify capabilities, implement playback-aligned path, measure on target devices; prepare an approved alternative if necessary |
| B07 | Local rigged-2D format/version, SDK commercial terms, package limits, and model-device evidence pending | T070-T077, T063 | Evaluate Live2D first as a proposal; owner selection and rights/device checks before integration |
| B08 | Windows floating is selected for the first release; runtime/version/packaging evidence pending | T078-T082, T063 | Verify Windows runtime/version/cost matrix; propose the framework from evidence |

B01-B04/B06 are known validation/setup conditions, not claims that a provider is unavailable or a task has failed. T069 is blocked by the specific unresolved visibility alignment. User messages and stored records must not be exposed through troubleshooting evidence.

## Next Assignments

1. Review T001's coverage index; correct omissions before implementation.
2. Assign T002 to the developer/technical agent for completed-audio STT evidence. Follow with T003/T004. No paid inference in these research tasks.
3. Assign T009 to the proposed product person and T010 to the proposed UX person once names are agreed.
4. Prepare T011 with the proposed QA person after the coverage/flow inputs are ready.
5. Resolve T069's actual visibility direction; separate this from model/setup work.

Only dispatch the selected task. Use the single-task prompt in `task-backlog.md`; do not launch the full backlog or assume every proposed role is accepted.

## Updating This File

For each assignment:

1. Fill the actual responsible person and reviewer. Check prerequisites and access/funding conditions.
2. Set `in progress` only when work begins. Record a concrete blocker immediately if one occurs.
3. Link `outputs/task-reports/Txxx.md` only after the report exists; include source references, changed files, verification type/results, costs when applicable, and remaining acceptance items.
4. Move to `in review` with evidence. Mark `done` only after reviewer acceptance; keep unperformed live/device/deployed checks visible.
5. Recompute the snapshot counts and identify newly ready dependent tasks. Update relevant gate state from actual evidence.
6. Append the date/task/outcome to the change log. Do not erase old blockers silently or turn proposed defaults into confirmed product decisions.

## Change Log

| Date | Change | Evidence / limits |
| --- | --- | --- |
| October 9, 2026 | Director created the 69-task breakdown, corrected source references, added five explicit coverage tasks, and mapped all 182 discovery decisions | task-backlog.md; requirements-coverage.md; mapping is not implementation verification |
| October 9, 2026 | Initial tracker established; T001 in review, eight research/design tasks ready, T069 blocked, all other tasks planned | No application task dispatched; no live API/device/deployment evidence |
| October 9, 2026 | R001 adds 13 avatar/floating tasks: total 82; T070/T078 ready for read-only evaluation, 11 additions planned | Default ball + first-release local rigged-2D import confirmed; format/OS/sequence pending; no code or purchase |
| October 9, 2026 | Owner confirmed floating companion in the first release alongside web, default ball, and local rigged-2D import | T082 now required before T063 rollout; first OS targets pending; no implementation |
| October 9, 2026 | Owner selected Windows as the first-release floating platform | T080/T082 required for Windows; T081 Android floating is future work; web mobile/desktop scope unchanged; runtime/version evidence pending |
| October 10, 2026 | Owner confirmed eyes and a shape-changing mouth for the default ball | T071 appearance refined; mouth shape inventory and audio-energy versus phoneme/viseme alignment still pending; no animation implemented |
