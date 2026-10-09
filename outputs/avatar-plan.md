# Laven AI - Avatar and Floating Companion Plan

Revision R001 - updated October 9, 2026.
Status: Director planning. No renderer, importer, SDK, model purchase, native client, or device acceptance completed.

## Confirmed Scope

- First-release default: a simple minimalist lavender ball, alive during actual listening, thinking, and speaking.
- First-release alternative: users import their purchased, already rigged 2D anime model to replace the ball.
- Model files stay locally on the importing user's device. No cloud upload, model-file sync, provider submission, sharing, or repository copy.
- The same AI companion, account, personality, voice, history, and memory continue. Existing gallery choices remain available.
- The app remains online; local model assets do not make inference or account data offline.
- Buying/commissioning an official Laven anime model can be future work. It is not a prerequisite for the ball or user-import feature.
- The latest clarification is 2D. A 3D/GLB/VRM importer, automatic rigging, camera tracking, and arbitrary-format compatibility are not selected.

Decision sequence: the owner requested rigged anime and cross-app floating presence, then chose a minimal ball default, clarified purchased rigged 2D as the user alternative, selected import in the first release, and confirmed local storage. This supersedes the provisional assumption that every user starts with an official supplied anime rig or that all rig import is later.

## Pending Decisions and Proposed Defaults

| Topic | Confirmed | Remaining decision / proposal |
| --- | --- | --- |
| Format | Ready-rigged 2D; owner has not selected a format | Director proposes evaluating Live2D Cubism first; owner selection, version, runtime terms, and compatible package evidence pending |
| Packaging | User supplies existing files | Propose one self-contained package with required model/textures/optional motions; exact importer contract follows format selection |
| Persistence | Device-local files | Propose account-partitioned browser storage; native clients need a separate local store |
| Selection | Files do not sync | Propose device-local override and references; other devices retain their valid gallery/ball appearance until separately imported |
| Limits | One main AI companion | Propose one active imported model per account/device; bytes/file counts/textures/runtime limits need evidence |
| Motion | Live conversational behavior | Ball design and supported rig mappings pending; not every asset provides mouth/expressions/motions |
| Floating delivery | Above other applications is confirmed | First OS targets and web/floating rollout sequence pending T078 |

Proposals are not owner-confirmed details. No multi-runtime compatibility or free commercial SDK release is promised.

## Experience

Settings > My Companion includes the ball, existing gallery, and local model import. Proposed actions: Import, Preview, Use model, Replace, Remove local model, Use default ball. Show loading/error/local-only states; do not treat a failed or cancelled import as a saved selection. Existing personality/voice controls retain their save behavior.

Failed import preserves the previous working appearance. Removing a model deletes the app's local copy and releases its resources; it never deletes the user's original purchased files. Other devices/browser profiles/native clients require separate imports. Keep captions below the active companion and conversation controls usable.

The ball can be built with a lightweight code/SVG/canvas approach; a 3D engine or commercial mascot is not mandatory. Facial features and exact motions remain design proposals.

## Local Privacy, Validation, and Lifecycle

- Read only user-selected package files locally. Do not send contents, textures, manifests, filenames, source paths, thumbnails, or package-error payloads to Supabase, Cloudflare storage, OpenRouter, analytics, logs, or task reports.
- Model references must resolve within the imported package. Reject remote resources, executable/plugin content, unsafe schemes, traversal, missing assets, unsupported formats/versions, and excessive resource budgets.
- Bound compressed/uncompressed size, file count, texture dimensions, parser/GPU resources, and expansion after validation work. Never execute user JavaScript from an archive.
- Partition local model data/selection by authenticated account; switching accounts must dispose the current renderer and prevent another user on a shared browser from inheriting it.
- Proposed browser persistence: IndexedDB or another verified local mechanism. Test refresh/reopen, private browsing, quota failure, eviction, and interrupted import. Explain re-import after site-data loss; local storage is not guaranteed backup.
- Explicit Remove deletes the app-local copy. Account deletion should clear its copy on the active client. Offline devices cannot be guaranteed remotely wiped; clear inaccessible account-local copies when clients next process deletion/auth state. Never delete original OS files.
- Revocation, interruption, deletion, exhaustion, and Stop follow existing conversation cancellation rules. Asset loading/replacement never auto-starts capture or revives an obsolete turn.
- Keep the ball fallback working, but label a missing/incompatible model honestly. Fallback rendering does not prove custom import works.
- Local avatar persistence is separate from conversation retention: audio remains transient-only, with no history replay.

## Shared Controller and Actual Playback

Accepted local session/turn state feeds a controller with ball and selected-compatible-2D adapters. Proposed states: idle, listening, thinking, speaking, paused, error. Map supported blink/breath/motions/expressions explicitly; do not invent missing parameters.

Actual originating-surface TTS playback drives speaking motion. Receiving shared chat text must not make another device appear to speak. Use turn IDs/stale-result rejection so pause/end/cancel stops obsolete mouth motion. Audio-energy mouth opening is a possible baseline for a compatible rig, not phoneme-accurate lip-sync or word-caption alignment.

Release frame loops, GPU resources, object URLs, and audio-analysis connections on replacement/unmount/context loss. Keep transient playback only; no per-frame AI calls, generated-video provider, new inference model, or camera capture. Lower motion/physics under reduced-motion or device constraints and record actual limitations.

## Cross-App Floating Companion

Keep the owner's confirmed floating presence and hideable controls. Exact platforms and release sequence remain open. An in-page widget does not satisfy presence above other applications.

- Desktop: evaluate transparent/always-on-top clients and OS compatibility; no Tauri/Electron choice yet.
- Android: validate application-overlay permission, touch routing, foreground microphone/service restrictions, notifications, and explicit pause/exit. Overlay permission does not grant unrestricted background capture.
- Browser Document PiP is a potential desktop prototype; it does not establish a transparent, freely positioned pet on every OS/mobile browser.
- iOS/iPadOS: verify supported system alternatives and limits; do not promise an unrestricted interactive overlay. Label in-app fallbacks accurately.
- Web and floating gates require an explicit sequencing decision. A web-first trial can be approved separately without claiming full floating delivery complete.
- Reuse authorization, memory, origin-only audio, and quota rules. A second view controlling the same session must not duplicate capture/timers; genuine independent sessions retain existing summed usage.
- Local browser assets are not automatically available to a native client. No cloud transfer is implied.

## License, Cost, and Sources

User model purchase does not settle the app SDK's commercial release terms. Verify applicable end-user asset rights and SDK category separately, including user-import/expandable-app classification. Do not buy assets, install proprietary binaries, or commit licensed model packages through this planning work.

The ball avoids a mandatory purchased character; local import avoids cloud hosting of user packages. Runtime licensing, development/device resources, and cloud AI costs still require evidence. The USD 10/month AI cap is not funded credit or a total startup budget.

Primary sources reviewed October 9, 2026; candidate evidence, not Laven implementation tests:

- [Live2D Web SDK](https://docs.live2d.com/en/cubism-sdk-manual/cubism-sdk-for-web/), [model references](https://docs.live2d.com/en/cubism-sdk-manual/model/), [lip-sync](https://docs.live2d.com/en/cubism-sdk-manual/lipsync/), and [commercial release terms](https://www.live2d.com/en/sdk/license/).
- [Spine runtimes](https://esotericsoftware.com/spine-runtimes): format-specific alternative, not an interchangeable Live2D loader.
- [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) and [storage quotas/eviction](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria).
- [Android overlays](https://developer.android.com/reference/android/view/WindowManager.LayoutParams#TYPE_APPLICATION_OVERLAY) and [microphone foreground services](https://developer.android.com/develop/background-work/services/fgs/service-types#microphone).
- [Chrome Document PiP](https://developer.chrome.com/docs/web-platform/document-picture-in-picture) and [Apple video-call PiP](https://developer.apple.com/documentation/avkit/adopting-picture-in-picture-for-video-calls).

## Tasks and Acceptance

T070-T077 cover runtime/license evidence, ball, local importer, compatible rig renderer, playback motion, settings/cleanup, device/privacy tests, and avatar acceptance. T078-T082 cover floating feasibility/sequence, shared integration, selected desktop/Android clients, and floating acceptance.

First-release avatar acceptance requires an actual ball and an actual authorized compatible rig imported and rendered locally, with privacy, error, removal, account-isolation, playback, and target-device evidence. A placeholder upload control or static image does not complete rig import. Missing format/rights are explicit dependencies, not permission to silently defer this selected feature.
