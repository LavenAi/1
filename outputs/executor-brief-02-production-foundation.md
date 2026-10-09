# Laven AI - Executor Brief 02: Online MVP Foundation

Status: Prepared by the Director. Not dispatched; Executor and reviewer are unassigned.

## Outcome

Establish a verified implementation path for a real online Laven AI MVP. The owner has confirmed a responsive production web app for mobile/desktop browsers, not a local-only demo. R001 additionally records first-release ball/local 2D import and cross-app floating presence; native targets and rollout sequence remain pending.

Keep Next.js/TypeScript, Supabase, Cloudflare, and the cascaded OpenRouter pipeline. Real user authentication, cloud persistence, protected AI integration, and actual voice are release requirements. Mocked tests may assist development; they cannot satisfy production acceptance.

R001 is in avatar-plan.md. Treat format/license/platform checks as separate bounded T070/T078 assignments; this foundation brief does not authorize SDK purchases, native client implementation, or cloud upload of user model files.

## Inputs

- `blueprint.md`: authoritative product requirements and selected controls.
- `startup-launch-plan.md`: Director milestones and online release gates.
- Planned source root: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/work/laven-ai`.
- Requested evidence report: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/outputs/executor-report-02.md`.

The owner reports a four-person inexperienced project team; no named role assignments or Executor identities have been approved. The Director coordinates work and review rather than implementing the app.

## Assignment A: Free Preflight and Architecture Evidence

Perform this bounded preflight before assuming the selected routes or deployment path work. It is read-only research/planning and does not authorize external setup, paid inference, purchases, or deployment.

### Model and Voice Verification

Check current official OpenRouter/provider documentation and available model metadata for these owner-selected identifiers:

- STT: `google/gemini-3.5-transcribe`.
- Interactive LLM: regular `google/gemini-3.8-flash`, not batch.
- TTS: `google/gemini-3.8-flash-lite-tts`.

Return an evidence table covering identifier availability, modality, supported audio formats, completed-audio transcription, text streaming, Thai/English support, expressive delivery, speed controls, response/audio timing metadata, cancellation, published pricing, and any account/funding requirement.

Separate documented capability, inference, and unverified behavior. If a model identifier is absent or a capability is undocumented, state that precisely; do not invent routes or claim success. Prepare alternatives for Director review without silently selecting replacements or sending paid requests. Word-level caption alignment and the three-second response target require measured tests later.

### Deployment and Account Verification

- Verify a supported Next.js/TypeScript deployment path on Cloudflare, compatible versions, runtime limits, streaming behavior, secret storage, and background-job support using current official sources.
- Identify Supabase account/authentication, verified-email, allowlist, database-access, and email-delivery setup requirements. Include the previously identified need to validate SMTP suitability for invited users.
- Distinguish development/staging URLs from the selected `lavenai.space` trial domain. Record domain/account/provider setup dependencies without purchasing or creating anything.
- Identify the smallest production vertical slice and its actual setup/funding blockers. The existing USD 10 monthly AI ceiling is not credit already available.

### Production Architecture Handoff

Prepare a concise component diagram and responsibility map for browser client, protected backend, Supabase Auth/database, OpenRouter adapters, and durable personalization jobs.

Specify contracts and safeguards for account identity, conversation/turn IDs, admission checks, cancellation, stale-result rejection, text persistence, transient-only audio, and metering. Keep credentials server-side. Preserve selected memory-off, deleted-fact, history-expiry, and cross-account isolation rules.

Do not write application code, create schemas, or connect services as part of Assignment A. Return the report and a proposed implementation work package for Director review.

## Assignment A Acceptance

The report must contain:

1. Exact verified identifiers/capabilities with official URLs and verification dates, including unresolved gaps.
2. A viable deployment proposal, or a clearly stated incompatibility and evidence.
3. Production component/data-flow diagrams and a small first integration slice.
4. Required accounts, access, domain, email, and funded-test dependencies; no secrets or account credentials in the report.
5. Cost assumptions separated from published prices, and a proposed bounded test allowance rather than an assumed free voice service.
6. Suggested team tasks with one responsible person and one reviewer per task, explicitly unassigned until the humans agree.

## Assignment B: Real Integration - Not Yet Activated

After Assignment A is reviewed and actual Executor/account access/test funding are established, a separate implementation assignment can activate:

- Real Supabase authentication and account-scoped persistence.
- Server-enforced allowlist/access and daily/monthly admission checks.
- Actual STT to LLM to TTS flow, with measured latency, cost, interruption, and failure recovery.
- A cloud staging deployment with a reproducible setup/runbook and Director review before real-user rollout.

Do not treat this future work list as current permission to create accounts, run paid calls, publish, or bypass the Director review gate.

## Completion Reporting

Report what was verified, what remains unknown, proposed deviations, and required decisions. Do not label the application launched or production-ready based on a diagram, a local mock, or a successful build alone.
