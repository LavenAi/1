# Laven AI

A voice-first, personalized AI companion delivered as an online web app for mobile and desktop browsers.

## Current status

This repository contains product planning and an implementation handoff. Application development and deployment have not started. The initial release is a private trial for the owner and email-allowlisted invitees.

## Project documents

- [Project blueprint](outputs/blueprint.md): English product specification, behavior, folder structure, and decision history.
- [Startup launch plan](outputs/startup-launch-plan.md): delivery milestones and real online release criteria.
- [Avatar and floating plan](outputs/avatar-plan.md): default ball, first-release local rigged-2D import, pending format, and floating-platform gates.
- [Build agent prompt](outputs/build-agent-prompt.md): instructions to give an AI implementation agent alongside the project documents.
- [Small-task backlog](outputs/task-backlog.md): 82 bounded tasks with dependencies, suggested roles, and acceptance evidence.
- [Progress tracker](outputs/progress_tracking.md): authoritative task states, evidence, release gates, and blockers.
- [Requirements coverage](outputs/requirements-coverage.md): mapping of all 182 discovery decisions and later instructions to work assignments.
- [Production foundation brief](outputs/executor-brief-02-production-foundation.md): model/runtime feasibility and integration checklist.
- [Earlier prototype brief](outputs/executor-brief-01.md): superseded historical planning; do not use as the current build assignment.

Start with the blueprint, launch plan, and progress tracker. Assign one backlog task using the copyable single-task prompt, with the build prompt as supporting guidance. Planning files include paths from the original Windows workspace; map them to your checkout before implementation. The planned application directory is `work/laven-ai/`.

## Selected direction

- Next.js and TypeScript for the responsive web application.
- Supabase for authentication and account-scoped persistence.
- Cloudflare for hosting and the verified deployment/runtime path.
- OpenRouter for the cascaded transcription, conversation, and speech pipeline.
- Thai/English conversation, a minimal lavender ball, optional first-release local rigged-2D import, and user-controlled personalization memory.
- Cross-app floating companion retained; first operating systems and web/floating rollout sequence still require selection. User model files remain device-local.

Exact model availability, deployment compatibility, voice quality, latency, and operating costs still require verification. Historical estimates and selected model identifiers are not proof that live integrations work.

Keep credentials, private user data, audio recordings, and local environment files out of the repository. The USD 10 monthly AI cap is a planning control, not funded provider credit or subscription pricing.
