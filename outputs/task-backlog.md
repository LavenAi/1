# Laven AI - Small-Task Implementation Backlog

Prepared: October 9, 2026.
Status: Director planning. There are 82 tracked tasks. The requirements-mapping audit is prepared for review; no application implementation task has been dispatched or completed. No application code, service setup, paid tests, or deployment has been performed through this breakdown. Current task states are recorded in `progress_tracking.md`.

## How to Use This Backlog

Use this alongside `blueprint.md`, `avatar-plan.md`, `startup-launch-plan.md`, and `build-agent-prompt.md`. The blueprint remains the product specification; this file divides its delivery into reviewable assignments without changing selected behavior. Later confirmed decisions take precedence over earlier historical ones. Proposed defaults remain adjustable within the selected scope. `requirements-coverage.md` maps all 182 numbered discovery decisions and later project instructions to tasks; `progress_tracking.md` is the single authoritative task-status tracker.

Give an implementation agent one task ID at a time. Read dependencies before starting. A dependency means the required contract/evidence must exist, not that every future feature of that component must be finished. Passing a small task does not mean the product is ready to launch. The phases describe work groups; independent tasks can overlap.

Each task should produce one bounded, reviewable result. If inspection reveals that a row cannot fit one coherent change, split it into child IDs such as `T046a` and `T046b`, preserving its acceptance criteria and recording the revised dependencies. Do not substitute a large unfinished branch for several completed tasks. Do not promise a fixed duration before inspecting the work and the team's availability.

Keep a task report at `outputs/task-reports/Txxx.md`, containing source references, changes, evidence, remaining limitations, and the next task. Do not put private user content, audio, or credentials in these reports. Use a small branch/PR per implementation task where practical; review is not permission to merge or release without the team's agreed workflow.

Statuses: `planned`, `ready`, `in progress`, `in review`, `done`, `blocked`. A task is `done` only when its own acceptance evidence exists. Documentation verification, mocked checks, live-provider checks, real-device checks, and deployed checks must be identified separately.

## People and Review

| Label | Suggested responsibility | Assignment status |
| --- | --- | --- |
| D | Developer/technical lead: implementation, architecture, provider integration, technical review | The owner has identified themself as developer; no individual task has been dispatched |
| P | Product/user research: user interviews, priorities, acceptance wording, trial recruitment | Proposed responsibility for one friend; person not assigned |
| X | UX/UI and conversation design: flows, visual system, bilingual copy, gallery assets, interview script | Proposed responsibility for one friend; person not assigned |
| Q | QA/trial operations: reproducible bug reports, device checks, trial checklist, expense tracking | Proposed responsibility for one friend; person not assigned |
| Director | Task briefs, scope decisions, evidence review, and recommendations | This planning assistant; does not implement the application |

The Role column below is a recommendation, not an assignment. Choose one accountable human and one reviewer before dispatch. An AI build agent can assist that human; responsibility remains with the team. D reviews technical and security evidence, while P/X/Q review observable behavior in their areas. Nontechnical approval alone does not validate access policies or concurrent metering. Roles are work responsibilities, not equity allocations.

## External Dependencies

These are setup conditions, not tasks already authorized or completed:

- S1: Access to the chosen Supabase/Cloudflare projects and secure credential configuration, with the email/Google sign-in setup needed for the particular test.
- S2: An available verified/approved OpenRouter route and an explicitly funded, bounded live-test allowance. The USD 10/month application cap is not funded credit or permission to spend it.
- S3: Authorized staging/trial deployment, domain access, DNS/email setup, and target devices. `lavenai.space` is desired and unpurchased; staging is distinct from the selected trial domain.

Prepare setup instructions and continue independent work when a condition is missing. Mark the affected live/deployed acceptance check blocked. Do not mark a provider adapter live-tested merely because contract tests pass. Complete the concrete work package before asking for an external setup, purchase, or release decision.

## Phase 1 - Evidence and Design Inputs

Read-only capability research starts first. P/X/Q can work on T009-T011 alongside it. No paid inference or external account creation is required to prepare these outputs.

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T001 | Build the effective-requirements index and release checklist; distinguish selected behavior, proposed defaults, superseded decisions, and feasibility gaps | Source documents available | D + P | Each substantive requirement maps to an implementation task and check; missed items become explicit child tasks, not hidden omissions | All sections; Decision Record |
| T002 | Verify the selected completed-audio STT identifier, request/response contract, formats, limits, errors, and prices | None | D | Current official URLs/date and an evidence table; explicitly record absent or undocumented capabilities; no inference requests | Sections 4-5; Steps 35, 179 |
| T003 | Verify the regular LLM identifier, text streaming, usage reporting, cancellation behavior, context limits, and prices | None | D | Current official evidence; standard inference distinguished from provider batch processing; gaps and alternatives recorded | Section 5; Steps 31-35 |
| T004 | Verify the TTS identifier, voices, Thai/English documentation, expression, speed, audio output, timing metadata, cancellation, and prices | None | D | Documented vs unverified vs later measured capabilities separated; proposed Thai fallback prepared for review if needed; no silent replacement | Section 4; Steps 161-162, 181-182 |
| T005 | Verify the selected OpenRouter Parallel Fast search contract, engine/mode, fees, source metadata, and language evidence | None | D | Exact route/configuration supported by official evidence or a precise incompatibility; no substitute engine selected automatically | First-Release Web Search; Steps 92-95 |
| T006 | Verify Next.js on Cloudflare: compatible versions/adapter, streaming, secrets, runtime limits, jobs, and scheduling | None | D | One evidenced deployment path plus durable-job options; unknowns listed; preserve Next.js/TypeScript | Sections 3, 5-6; Step 36 |
| T007 | Verify Supabase sign-in, verified-email handling, owner bootstrap options, and invited-user email delivery requirements | None | D | Setup dependency list; email verification/reset/Google callback needs documented; ordinary invitees do not need project-admin access | Account and Cross-Device Data; Steps 21, 47-48 |
| T008 | Assemble funding/setup and cost sheet from verified prices; identify minimum test allowance and source of usage measurements | T002-T007 | D + Q | STT/LLM/TTS/search/jobs/previews accounted for; estimates distinguished from charges; USD 10 cap distinct from provider credit and subscription price | Usage Controls; cost reference sections |
| T009 | Interview three prospective companion users and summarize the strongest needs | Confirmed companion-first scope | P | Anonymized findings and prioritized problems; do not upload private conversations; propose changes separately from confirmed scope | Project Goal; Initial Release Scope |
| T010 | Produce responsive flows and a small lavender design system: Conversation, chat panels, Settings, History, and onboarding | Confirmed UI scope | X | Mobile/desktop layouts, light/dark tokens, states, and Thai/English copy; lower-priority future features excluded | Pages and Main Features; Visual Theme |
| T011 | Write the acceptance scenarios and bug-report template | T001 + T010 | Q + D | Reproducible cases for voice actions, access, memory, quotas, concurrency, retention, and errors; privacy-sensitive evidence avoided | Startup release gates; Sections 4-6 |

Gate A: Compile T002-T008 findings into the foundation evidence report requested by Brief 02. Review any material incompatibility before changing selected models or architecture. Design/scaffolding can proceed on validated independent contracts; live inference waits for verified routes, guards, and S2.

## Phase 2 - Protected Foundation

These tasks establish the minimal account/data/usage boundaries needed before real AI calls. This is not a request to finish every admin screen before proving voice feasibility.

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T012 | Scaffold the application under `work/laven-ai/`, with the verified runtime path, scripts, environment example, and basic checks | T001 + T006 | D | Clean reproducible install/build/type checks; existing Git repository preserved; no credentials committed; placeholders clearly labeled | Folder Structure; Delivery Plan |
| T013 | Create the versioned minimal data migrations and account access policies for the first slice, leaving documented extension points | T001 + T007 + T012 | D | Migration applies in the authorized test environment; account A cannot read/write B's rows; source/turn/job and metering fields defined | Sections 3, 5; account isolation |
| T014 | Implement email/password sign-in, verification, sign-out, and recovery using documented secure defaults | T007 + T012 + T013; S1 for live checks | D | Actual verified/unverified and recovery flows; invalid/expired auth denied; assumptions about recovery recorded | Account and Cross-Device Data; Step 21 |
| T015 | Implement Google sign-in and consistent app-account identity across supported sign-in methods | T014 + T007; S1 | D | Actual callback/sign-out checks; account linking follows a documented validated path, without merging accounts based on untrusted client email | Account and Cross-Device Data |
| T016 | Implement safe owner bootstrap and server/database allowlist eligibility checks | T013 + T014 | D | Verified active allowlisted account admitted; revoked/unlisted/unverified users denied; owner mutations unavailable to ordinary users; no invitee-content admin access | Steps 47-49; Trial Access |
| T017 | Persist account companion/settings defaults and validation with account-scoped read/write APIs | T013 + T016 | D | New defaults match blueprint; a second sign-in/device sees saved values; invalid writes rejected; saved values distinguished from drafts | Companion, languages, settings; Steps 159-172 |
| T018 | Define session/turn/job identifiers, state transitions, cancellation tokens, and stale-result write guards | T001 + T013 | D | Contract/state diagram plus targeted checks: stale turn cannot append, restart audio, or write to a different thread/account | Voice and AI Behavior; Logical Workflow |
| T019 | Implement daily active-session usage ledger and admission check, including overlapping sessions and typed playback outside sessions | T016 + T018 | D | Deterministic checks for elapsed listening/thinking/silence, summed overlaps, no typed-audio double count, server UTC reset, and close/pause boundaries; show the remaining-time indicator without advance alert popups/sounds | Steps 51-56, 61, 139, 148 |
| T020 | Implement monthly AI-spend reservation/reconciliation and provider-usage records | T008 + T013 + T016 + T018 | D | Concurrent reservations and retries cannot freely bypass available allowance; actual charges reconciled; incurred costs not erased by cancellation; overshoot limits reported | Steps 54, 57-58, 149; Usage Controls |
| T021 | Build reusable protected provider-call admission and error handling around eligibility, daily rules, monthly budget, and turn identity | T016 + T018-T020 | D | Every interactive provider entry is guarded; preview/background exceptions apply only where specified; secrets/logging stay server-safe | Production Requirements; Logical Workflow |

## Phase 3 - First Real Conversation Slice

Start with a held recording to isolate the real pipeline; continuous capture follows in Phase 4. This implementation order does not change continuous mode as the final default.

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T022 | Build the responsive app shell and Conversation screen with avatar container, collapsed menu, and desktop/mobile chat containers | T010 + T012 | D + X | Actual mobile/desktop rendered inspection; ball/import states follow R001; navigation/focus/accessibility work; visual animation is not represented as live AI | Main Screen; Page Map; R001 |
| T023 | Build readable user/AI messages and typed Send flow with source/speech metadata separation | T018 + T021 + T022 | D + X | Typed send creates one account-scoped turn; typing alone has no interrupt effect; corrections use a new typed message, without editing/regenerating old messages; citations excluded from speakable text; fake responses confined to tests | Steps 14, 24, 27, 65, 125 |
| T024 | Implement transient microphone capture and hold/release input with permission, empty/cancelled recording, and 120-second limit handling | T018 + T022 | D | Touch/pointer/keyboard held recording; release submission; cancelled/empty capture discarded; limit offers Send/Record again; no saved audio | Steps 64, 179; User Speech Storage |
| T025 | Implement the verified STT adapter and account-scoped transcript acceptance | T002 + T018 + T021 + T024 | D | Contract/error tests; live transcription marked pending until S2; cancelled/obsolete transcript cannot create a user message | Models; Steps 35, 143-145 |
| T026 | Implement regular LLM reply streaming using current accepted conversation text and baseline saved settings | T003 + T017 + T018 + T021 + T023 | D | Streaming/error/usage contract checks; interrupted replies are not treated as complete context; no batch processing; live checks gated by S2 | Logical Workflow; Steps 32, 122 |
| T027 | Implement TTS, ordered transient playback, speech failures, and originating-surface delivery | T004 + T018 + T021 + T022 | D | Actual audio decoding/playback when S2 is available; first completed sentence begins speech while later text generates; no audio persistence/replay; origin-only output; sentence ordering preserved | Steps 27, 63, 110, 121 |
| T028 | Connect one real held-spoken turn and one real typed reply through guarded STT/LLM/TTS and text persistence | T023-T027; S1 + S2 | D + Q | Observe actual Thai/English input and output; saved text visible after refresh; stage timing and provider usage recorded without audio artifacts | Startup Milestone 1; Logical Workflow |
| T029 | Deploy the protected slice to authorized cloud staging with basic setup/rollback instructions | T006 + T014-T016 + T028; S3 | D + Q | Real URL works independently of the developer's local server; protected access and secrets checked; staging is not declared full trial release | Startup Milestones 1-2 |

Gate B: A real account-isolated voice turn has been observed and measured. A local mock, recorded sample, build success, or staging placeholder does not pass this gate. If setup/funding is missing, keep the gate blocked and continue only independent tasks.

## Phase 4 - Conversation Lifecycle and Multiple Surfaces

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T030 | Add continuous VAD capture, the two-second utterance-end timer, resumed-speech extension, and shared recording-limit behavior | T024-T028 | D | Silence submits nothing; speech during the wait extends the same utterance; no press per turn; limit controls retained; continuous becomes default | Steps 5, 119-120, 179 |
| T031 | Implement speech/send interruption and cancellation with echo/false-interruption checks | T018 + T026-T028 + T030 | D + Q | Local speech and unfinished generation stop; saved text remains interrupted; late output ignored; new turn starts; independent surface unaffected | Steps 65, 122; Logical Workflow |
| T032 | Implement the distinct mute and mode-switch rules at recording, submitted, thinking, and speaking boundaries | T018 + T030-T031 | D + Q | Race checks prove unsubmitted mute/switch discard; accepted turns follow their selected rules; fresh capture uses the new mode; stale hold release ignored | Steps 114, 143-145 |
| T033 | Implement automatic/manual session start, explicit Resume/Stop, persistent navigation controls, and browser lifecycle pause fallback | T019 + T022 + T030-T032 | D + Q | Permission and admission precede capture; explicit Stop does not restart; History/Settings keep active controls; unsupported background continuation is reported honestly | Steps 22, 59-60, 78, 139 |
| T034 | Implement disconnect/reconnect recovery and bounded STT/LLM retry plus current-failed-reply audio retry | T018 + T021 + T025-T027 + T033 | D + Q | One eligible automatic transient retry then manual; disconnect pauses capture/audio/quota; reconnect requires Resume; Retry audio reruns TTS only, without history replay | Steps 66, 96-97, 110; Failure Recovery |
| T035 | Implement default-on proactive follow-ups with the selected timers, count, mute behavior, and auto-pause | T019 + T026-T027 + T033 | D + Q | Continuous only; 30 seconds after speech, maximum two unanswered follow-ups, then pause two minutes after the second; follow-ups continue while manually muted without unmuting input; guards checked before calls | Steps 73-77, 123-124; Proactive Conversation |
| T036 | Coordinate simultaneous sessions, one shared active thread, ordered messages, new-thread/resume/switch semantics, and origin-only audio | T018-T019 + T028 + T031 + T033 | D + Q | Two tabs/devices join/switch the shared thread without duplicate creation; independent session lifecycles remain; obsolete thread output rejected; durations summed | Steps 61-63, 88-89 |
| T037 | Synchronize saved settings and edits across surfaces with stale-write/conflict handling | T017 + T018 + T036 | D | Saved changes arrive on a second surface; failed drafts do not become effective; out-of-order writes do not silently overwrite newer accepted changes; mechanism documented | Cross-Device Data; Steps 156-158 |

## Phase 5 - Companion and Presentation

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T038 | Implement light/dark/system theme, lavender/accent selection, Thai/English UI strings, and caption/startup/search preference controls | T010 + T017 + T022 + T037 | D + X | Device-language fallback and saved preference tested; keyboard/focus/contrast/reduced-motion checked; unavailable integrations not claimed live | Steps 11, 23, 59, 92-93, 147, 167 |
| T039 | Implement My Companion personality/name/custom-instruction controls with autosave and confirmed Reset personality | T017 + T022 + T037-T038 | D + X | Four presets, 1-5 traits, 3/4/2 defaults, 1,000-character counter; preset changes retain traits; failed draft retained; reset preserves unrelated fields | Steps 69-71, 156-160, 172, 174 |
| T040 | Prepare a small licensed/original gallery and integrate synced gallery appearance selection | T010 + T017 + T022 + T037 | X + D | Both asset themes and default ball work; provenance and mobile/desktop fit checked; R001 local rig import is covered by T072/T075 without general image upload | Steps 12-13, 115; R001 |
| T041 | Implement verified voice catalog, preview, speed selection, and next-reply settings semantics | T004 + T017 + T027 + T031-T033 + T037-T039 | D + X | Sample uses saved personality/UI language; local work cancelled and quota paused before preview; explicit Resume; no daily deduction but monthly charge; current speech keeps old voice/speed | Steps 16-17, 150-152, 157, 161-162, 171 |
| T042 | Implement final reply prompt/style/language assembly and saved-settings precedence | T026 + T038-T039 | D + X | Thai/English/mixed and explicit language requests exercised; custom instructions override conflicting style but not server policy; contextual adaptation does not edit saved traits | Steps 6, 29, 112, 116-117, 154, 156-160 |

## Phase 6 - History and User-Controlled Memory

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T043 | Implement History list/read/resume, activity ordering, topic/date titles, and protected manual renaming | T028 + T036 + T038 | D + X | Only accepted user activity moves order/retention anchor; manual names survive auto-title jobs; no search or replay; resumption uses shared-thread rules | Steps 18, 83, 89, 110, 113, 163-165, 175 |
| T044 | Implement Settings > Memory facts/summaries tabs and account-scoped Add/Edit/Save/Cancel/Delete operations | T013 + T017 + T022 + T038 | D + X | Explicit Save for edits, preserved failed drafts, no user search, and disabled-memory explicit-add confirmation; owner cannot browse other accounts | Steps 40, 43, 118, 168-169, 173, 177 |
| T045 | Implement memory retrieval/learning eligibility: off, retained data, forward-only re-enable, and specific explicit-save exception | T018 + T026 + T042 + T044 | D + Q | Saved memory unused while off; current context remains; disabled-period content never backfilled; only confirmed specific item saved when enabling via the action | Steps 28, 41-45; Memory |
| T046 | Implement deleted-fact exclusion identity/matching and summary filtering for automatic learning and retrieval | T018 + T044-T045 | D + Q | Deleted fact does not return through paraphrase, retained summary, history, or new conversation; explicit remember can restore it; unrelated summary facts remain; uncertain matcher limits documented | Step 41; Hyper-Personalization |
| T047 | Implement durable end/inactivity job scheduling, idempotency, retries, budget-paused pending work, and source-state checks | T018 + T020-T021 + T033 + T036 + T045-T046 | D | End or 15-minute idle schedules eligible work once; resume updates same summary; jobs recheck access/memory/budget/source state; delayed results cannot recreate removed data | Steps 37-42, 149; Background Workflow |
| T048 | Implement regular-LLM summary updates and separate fact extraction/conflict replacement through the guarded job path | T003 + T026 + T044-T047 | D + Q | One current summary per thread; silent automatic fact updates, including manual-item conflict rules; no learning from ineligible sources; duplicate/conflict and usage evidence | Steps 39-45; Background Workflow |
| T049 | Implement seven-day history expiry and source invalidation while retaining eligible saved summaries/facts | T043 + T045-T048 | D + Q | Clock-controlled checks use last accepted user activity or greeting-only creation; viewing/AI output does not extend; cleanup prevents late learning but preserves saved memory | Steps 82-83; History Retention |
| T050 | Implement confirmed individual/multi-select history deletion with active-thread cancellation | T031 + T036 + T043 + T046-T049 | D + Q | Selected active thread stops across its sessions, history removed, existing eligible memory retained, obsolete writes rejected; inactive deletion does not stop unrelated sessions; no auto-new-thread | Steps 19, 176, 178 |

Gate C: Memory-off, deleted-fact, history deletion/expiry, and concurrent-session behavior pass meaningful tests before inviting real users to rely on personalization.

## Phase 7 - Onboarding, Search, and Administration

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T051 | Implement one new-thread greeting with eligible personalization and UI-language-before-first-input rules | T027 + T036 + T042 + T045 | D + X | One greeting per shared thread on its originating surface; generic when memory off/empty; join/Resume adds no greeting; no invented recent events | New Conversation Greeting; Steps 90-91, 155 |
| T052 | Finalize the selected friendly interview script and optional language-learning questions | T009-T010 | P + X | Three-to-five core questions include adaptive clarifications without repeating covered topics; optional target-language/familiarity/purpose branch makes roughly six-to-eight total when fully asked; skip/copy in Thai/English | Onboarding Interview Direction; Steps 127-140 |
| T053 | Implement optional AI interview, explicit capture start, saved setup stages, completion-only learning, and optional companion customization | T017 + T033 + T039-T041 + T045 + T047-T049 + T051-T052 + T065 + T067 | D + X + Q | Skip/typed fallback work; unfinished interview restarts after closure, preserving abandoned text but rejecting learning/late output; temporary disconnect still uses Resume; completion processed once; own text-only history; customization/greeting transition deduplicated; quota preserved | Steps 126-141; onboarding clauses |
| T054 | Integrate verified Parallel Fast web search with server toggle, actual-call daily counter, and chat-only grounded citations | T005 + T018-T021 + T023 + T038 + T042; S2 for live checks | D + Q | Default off; concurrent ten-execution cap enforced; exhausted search permits eligible ordinary chat; sources map to results and are not spoken; costs measured when authorized | First-Release Web Search; Steps 92-95 |
| T055 | Build owner Trial Access UI and finish immediate cross-surface revocation/reinstatement propagation | T016 + T018 + T031 + T036 + T038 | D + Q | Add/revoke/reinstate; revoke stops accepted generation/playback/jobs immediately, preserves saved data, rejects late output; reinstatement does not auto-resume; no private-content access | Steps 48-49, 142 |
| T056 | Implement owner per-account current-UTC-day allowance overrides, reset display, and immediate lower-cap behavior | T019 + T036 + T038 + T055 | D + Q | Owner can edit own/invitee allowance, preserving used time; next day 30-minute base returns; raising does not auto-resume; no global-default edit | Steps 137-138, 148 |
| T057 | Implement owner monthly budget/spend view and current-UTC-month cap override | T020 + T036 + T038 + T055 | D + Q | Preserves spend; next month USD 10 base returns; does not buy credits or bypass daily limits; restored allowance does not auto-start microphones | Steps 54, 57-58, 149 |
| T058 | Implement account deletion confirmation, seven-day restricted pending state, cancellation, and guarded permanent cleanup | T014-T018 + T036 + T045-T050 + T055-T057 | D + Q | Pending page/cancel/sign-out only; cancellation/deadline races tested; cleanup removes personal data/auth, prevents recreation, keeps aggregate incurred spend; fresh signup needs new authorization; last-owner/provider-backup handling explicitly resolved/documented | Steps 84-87; Account Deletion |

## Phase 8 - Final Voice Evidence and Real Trial

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T059 | Implement and verify the final word-progress caption path and Show AI captions behavior | T004 + T027 + T031 + T038 + T041 | D + X + Q | Actual playback-aligned whole words, Thai segmentation, wrapping, sentence clearing, and interrupted final clearing; prototype fallback explicitly not release-ready; missing timing capability becomes a reported blocker | Steps 10, 67-68, 167, 182; Caption Review |
| T060 | Audit end-to-end access, retention, daily/monthly exhaustion, and concurrency with targeted regression cases | T034-T037 + T045-T050 + T053-T059 + T066-T068 | D + Q | Account isolation, revocation, deletion, stale jobs, overlapping time, and in-flight exhaustion tested across endpoints; preview/background exceptions respected; remaining failed checks visible | Release Acceptance; Steps 142-152 |
| T061 | Run the Android Chrome/desktop Chrome voice and visual acceptance matrix; measure actual latency, quality, speed, and authorized costs | T029 + T030-T042 + T051 + T053-T060 + T074-T075; S1-S3 | Q + D + X | Real-device observations, ball/import presentation, permissions/background/reconnect/echo, both themes/languages; first-audible metric includes two-second silence wait; no audio retained; unmet targets reported | Device Priorities; Steps 78, 99-100, 108-109, 119-120, 161; R001 |
| T062 | Complete trial-domain/email/deployment/recovery operations and environment handoff | T007-T008 + T029 + T060-T061; S1 + S3 | D + Q | Actual authorized domain/DNS/email configured; migrations/jobs/secrets and owner bootstrap reproducible; rollback/recovery exercised; provider-retention uncertainty disclosed | Startup Milestone 4; Steps 102-103 |
| T063 | Review private-trial readiness, resolve release blockers, and perform the authorized owner/invitee rollout | T001 + T059-T062 + T069 + T077-T078; T082 if floating in rollout; explicit rollout authorization | P + Q + D | Review full coverage/live evidence and R001 avatars/sequence; expected 1-5 is not a signup cap; real users reach the online product; web-first approval does not complete floating delivery | Startup Milestone 4; Release Acceptance; R001 |
| T064 | Collect manual trial feedback and measured usage, then prepare the wider-launch recommendation | T063 | P + Q + D | Reliability/retention/value findings, incurred cost vs estimates, remaining work, and pricing/public-launch questions documented; no automatic public registration or paid launch | Startup Milestone 5; Step 180 |

Gate D: A real online private trial is only accepted when the startup release criteria and all selected requirements pass, or the owner explicitly approves a documented scope/target change. The prototype caption allowance is not a blanket release exception. T064 is a post-trial decision task, not permission for a public paid launch.

## Coverage Audit Additions

These tasks make obligations found in the detailed source review explicit. IDs are appended to preserve the existing task references; execute them according to dependencies, not number order.

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T065 | Implement answer-based post-interview preset/image/voice suggestions using real available catalogs and field-by-field acceptance | T004 + T017 + T040-T042 + T052 | D + X | User accepts or changes each suggestion; only accepted settings saved; sliders/name/speed/custom instructions preserved unless explicitly edited; memory-off uses transient interview context without hidden saved profile; guarded cost documented | Step 141; Initial Personality Presets |
| T066 | Implement scoped developer memory-search diagnostics for the developer's own and designated test accounts | T016 + T044 | D | Search available through documented local development tooling only; no user search/admin dashboard; real invitee-content access denied; no privileged browser credentials or private-content logs | Step 173; Step 168 |
| T067 | Implement conversational explicit-remember requests and their item-specific persistence/confirmation flow | T021 + T026 + T044-T046 | D + Q | Spoken/typed explicit request saves only the intended fact while eligible; off shows Enable memory and save this and waits for confirmation; failed/pending saves not claimed successful; no unrelated backfill; explicit restore can remove the matched exclusion safely | Steps 4, 41-43, 118; Explicit Remember Workflow |
| T068 | Implement contextual expressive TTS direction using the saved per-reply personality baseline | T004 + T026-T027 + T031 + T039 + T041-T042 | D + X + Q | Observed playful/gentle/serious delivery follows actual verified route support and conversation context; ongoing reply retains its started settings through all sentences; saved profile unchanged; tone claims distinguished from real quality checks | Steps 17, 29, 156-157, 162 |
| T069 | Resolve repository visibility against the earlier private-repository requirement and record the actual Git/GitHub state | GitHub metadata available; owner decision for a visibility change | D + P | Current `LavenAi/1` is public, verified October 9; Step 105 planned private. Record the owner's explicit direction before changing visibility; working repo/remote/history preserved; no unsupported claim of private storage | Steps 105-106; later supplied repository/push instruction |

Coverage review found all 182 discovery decisions mappable to this backlog, historical context, or explicitly later work. Mapping coverage is not implementation completion. Repository visibility is a recorded unresolved alignment issue; exact model/runtime capabilities and live quality remain unverified. `requirements-coverage.md` records the classifications and specific task links.

## Revision R001 - Ball, Local 2D Import, and Floating Delivery

First-release avatars now require a default minimalist ball and optional device-local imported user-owned rigged 2D model. No official purchased mascot or 3D importer is required. Format is pending; Live2D Cubism is the Director's first evaluation candidate. See avatar-plan.md for local/privacy/runtime contracts.

Apply these acceptance amendments to existing tasks without deleting their original scope:

- T010/T022: design/build the ball-or-imported-model container and local import/error/fallback flows; no fake working-model claims.
- T017/T037: preserve cloud settings/history/memory sync while keeping imported assets and proposed custom-model selection device-local/account-partitioned.
- T040: keep the licensed static gallery. R001 adds local rigged-2D import through T072/T075; no general image/3D upload scope.
- T058/T060: include reachable app-local model cleanup, account-switch isolation, and no false promise to erase original files or offline devices immediately.
- T061: include T074/T075 integration in the device evidence; T076 supplies import-specific privacy/performance checks.
- T063: additionally requires T077 and an explicit T078 platform/sequence decision. If the owner selects a web-first trial, document that boundary and keep floating acceptance open. If floating clients are included in that rollout, require T082 for those targets.
- T065: recommend actual existing gallery/preset/voice choices only; never invent available local models or silently import assets.

### Added Tasks

| ID | Task and output | Depends on | Role | Acceptance evidence | Blueprint source |
| --- | --- | --- | --- | --- | --- |
| T070 | Verify the first 2D import format/runtime, local package contract, commercial rights, device support, and resource limits | None | D + X | Official evidence/date; Live2D is a proposal, not selected; owner format decision and SDK/asset terms explicit; no purchase or installation | R001; avatar-plan.md |
| T071 | Build the minimalist lavender ball and its conversation-state controller | T010 + T012 + T018 + T022 | D + X | Actual local listening/thinking/playback states; paused/error/reduced-motion behavior; no mock AI claim; default usable without a purchased rig | R001; avatar-plan.md |
| T072 | Implement bounded client-local package import, validation, and account-partitioned storage | T070 + T012 + T016 | D | Chosen format only; package-local references; unsafe/remote/executable/oversized assets rejected; no cloud/network content transfer; quota/eviction/import-cancel handling | R001; local model privacy |
| T073 | Render an authorized compatible rigged 2D model through an isolated runtime adapter | T070 + T072 + T018 + T022 | D | Real model/textures/mapped motions observed; load/error/context-loss/cleanup; missing rig features reported; SDK rights established; no static substitute | R001; runtime evidence |
| T074 | Connect ball and supported rig speaking motion to actual originating-surface playback | T027 + T031 + T071 + T073 | D + Q | Pause/end/cancel/late-result guards; remote text does not animate speech; supported mouth mapping and bounded expressions; no per-frame inference or stored audio | R001; original voice/caption contract |
| T075 | Add local model import/preview/use/replace/remove/default controls and identity/deletion cleanup | T017 + T022 + T037 + T040 + T072 + T073 | D + X | Failed import preserves appearance; local override isolated by account/device; other devices use valid fallback; deletion removes app-local copy when reachable, not original OS files; no cloud sync | R001; My Companion |
| T076 | Verify local import privacy, hostile-package limits, persistence, accessibility, and real-device performance | T029 + T058 + T060 + T074 + T075; target devices | D + Q + X | Network inspection proves assets stay local; real authorized packages; account switch/removal/eviction; GPU/memory/reduced-motion and mobile/desktop matrix; no fabricated universal support | R001; device/privacy acceptance |
| T077 | Review first-release ball and optional local rigged-2D import acceptance | T061 + T071-T076 | D + Q + P | Actual ball and local rig working with live conversation on approved devices; format/SDK rights and unresolved limits recorded; owner acceptance required for scope changes | R001; first-release avatar gate |
| T078 | Evaluate cross-app floating platforms, supported OS matrix, costs, and web/floating release sequence | None | D + P | Official desktop/Android/iOS/PiP evidence; owner chooses first OS targets and sequence; in-page fallback not called cross-app; no framework/purchase silently selected | R001; confirmed floating presence |
| T079 | Define and implement the approved floating client/session bridge and local asset boundaries | T018 + T021 + T036 + T037 + T078 | D | Reuse account guards/memory/budgets/origin-only audio; same-session view has one capture/timer; independent sessions still sum; local assets not auto-transferred; revoke/stop propagation | R001; cross-client contract |
| T080 | Build the floating desktop companion for the explicitly selected desktop OS and runtime | T070-T075 + T078 + T079; approved desktop target | D + X | Real always-on-top/transparent placement where supported; drag/hide/reveal/pause/exit; ball/imported rig; OS permission/lifecycle tests; no unselected platform claim | R001; desktop floating delivery |
| T081 | Build the floating Android companion if Android is selected for the first floating milestone | T070-T075 + T078 + T079; approved Android target | D | Actual overlay permission and touch behavior; microphone/service/notification lifecycle; pause/exit/revoke and local asset import; real OS/device evidence; no unrestricted-background promise | R001; Android floating delivery |
| T082 | Review packaging, permissions, recovery, resource use, and release evidence for selected floating targets | T079 + owner-selected T080/T081; authorized release environment | D + Q + P | Selected OS matrix passes; captions/controls/local imports/account guards and quota cancellation verified; sequence explicit; unselected platforms not declared complete; rollout separately authorized | R001; floating acceptance |

Gate E: selected floating targets require real cross-app client evidence from T082. A web trial alone does not complete floating delivery. First-release avatars require T077 even when the owner approves a web-first sequence. These additions are planning, not assignments, purchases, installations, or accepted implementation.


## First Work Queue

Start with these assignments rather than sending the entire build to one agent at once:

1. D/technical agent: T002, then T003, then T004. Independent metadata checks may be batched within an assignment, but report each task separately. T006/T007 are the next infrastructure checks. No paid calls.
2. P: T009, using the selected companion-first audience and anonymized notes.
3. X: T010; T052 can follow the research/flow inputs before onboarding code begins.
4. Q: prepare T011 after the effective-requirements index and flow inputs; begin drafting the bug-report template while those inputs are being prepared.
5. D + P: T001 completes the mapping audit so the board has coverage, without reopening the 182 discovery decisions as another questionnaire.

The proposed P/X/Q roles can start before application code. Do not wait for every research/design task to finish before scaffolding the validated technical path. Conversely, do not issue paid live calls before the guarded foundation and actual test funding exist.

## Copyable Single-Task Agent Prompt

Replace the task ID and role/reviewer fields before sending. If using a separate machine, supply the real documents; a local path does not attach them.

```text
You are the Executor for one bounded Laven AI task: [Txxx - task title].

Read outputs/task-backlog.md, outputs/blueprint.md, outputs/startup-launch-plan.md,
outputs/progress_tracking.md, outputs/requirements-coverage.md, outputs/avatar-plan.md, and the relevant
guidance in outputs/build-agent-prompt.md. Read the source
sections and latest decision outcomes referenced by this task. Preserve selected
behavior, existing code, repository instructions, and budget/access boundaries.

Responsible human: [name / developer]
Reviewer: [name]
Application root: work/laven-ai/ within this repository.

Implement or research this task only. Check its prerequisites first. If a
prerequisite is missing, explain precisely what is missing and complete the
independent preparation this task permits. Do not claim a prerequisite is done
from an untested assumption or silently implement unrelated future tasks.

Make routine reversible choices and carry out the scoped work. Use current
official sources for unstable provider/runtime facts. Test the behavior with
evidence appropriate to the task. Clearly label contract tests, mocks, live
provider observations, real-device checks, and deployed checks. Do not create
accounts, spend money, change selected models, or publish without the applicable
owner authorization. Ask only for material missing information or dependencies.

Write outputs/task-reports/[Txxx].md with:
- Goal and exact blueprint/decision references.
- Deliverables and changed files.
- Checks performed and observed results.
- Costs incurred if authorized; otherwise distinguish estimates and no paid tests.
- Unverified behavior, blockers, and any proposed deviations.
- Status: in review, or blocked with the remaining acceptance items.
- The smallest next task.

Update outputs/progress_tracking.md with actual status/evidence and accurate
counts. Do not mark done before reviewer acceptance. Stop at this task's review
boundary. Do not mark the whole application complete
or automatically start the next task. Report in Thai; write artifacts in English.
Begin with a short plan, then do the scoped work in the same turn.
```

## Later Work - Outside This Trial Backlog

Full language-tutor flows, Chinese/Japanese, public signup, paid subscriptions, an official commissioned/purchased Laven character, 3D import, and scaling decisions remain later work. R001 selects first-release local rigged-2D import and separately retains floating delivery; its first OS targets and rollout sequence need T078. Do not classify every native/floating task as later by default. Optional interview questions about language interests do not activate the tutor release. No new analytics/embedding/feedback service is selected by this breakdown.
