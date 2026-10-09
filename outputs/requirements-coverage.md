# Laven AI - Requirements Coverage Audit

Prepared: October 9, 2026.
Status: Planning coverage prepared for review. Every numbered blueprint decision is classified and mapped. No implementation, live-provider validation, or deployed acceptance is implied.

## Audit Result

- Numbered discovery decisions indexed: **182 / 182**.
- Backlog tasks: **82**, including T070-T077 avatars and T078-T082 floating delivery under R001.
- Unmapped numbered decisions: **0**.
- Full behavior remains in `blueprint.md`; the summaries below are navigation aids, not replacements for detailed acceptance conditions.
- Current task status and evidence are recorded in `progress_tracking.md`. A mapped requirement can still be unimplemented, unverified, or blocked.

The audit added explicit tasks for post-interview recommendations (T065), scoped developer diagnostics (T066), conversational remember commands (T067), contextual expressive speech (T068), and repository visibility alignment (T069). It also clarified unfinished-interview restart, muted proactive follow-ups, correction by a new typed message, streaming first-sentence speech, and remaining-time-only presentation, and corrected mistaken decision-number references in the first task draft.

## Classification

`selected`: current selected requirement. `delegated`: selected under explicit owner delegation. `refined`: later decisions clarify or replace part of the early wording. `superseded` / `superseded state`: historical behavior/state must not be implemented as current. `reference`: background/options, not a new selected feature. `scope`: a priority, release boundary, or later expansion. `later`: outside this trial. `validation` / `state-dependent`: selection/context exists but current capability/setup needs checking. `alignment issue`: a real mismatch needs an explicit decision.

## Decision-to-Task Index

Read the full matching Step in the blueprint and the corresponding backlog task before implementation. Task references are stable IDs; a later-only row intentionally has no trial implementation task.

| Blueprint decision | Source summary | Classification | Task IDs | Interpretation / exception |
| --- | --- | --- | --- | --- |
| Step 1 | Prioritize an AI companion, followed by a general assistant, with language tutoring later. | scope | `T001`, `T009`, `T063`, `T064` | Companion first; tutor later. |
| Step 2 | User-selectable personality, with a Pingo-like persona planned for later exploration. | scope | `T039` | Customizable baseline is current; a Pingo-like persona remains later exploration. |
| Step 3 | Hyper-Personalization is the product's core direction. | selected | `T045`, `T048` | - |
| Step 4 | Support automatic learning and explicit memory commands, with user controls to view, edit, delete, or disable memory. | selected | `T044`, `T045`, `T067` | - |
| Step 5 | Support continuous conversation and button-activated speaking. | selected | `T024`, `T030`, `T032` | - |
| Step 6 | Launch with Thai and English, automatic language switching, and mixed Thai-English conversation support. | selected | `T042`, `T061` | - |
| Step 7 | Start with personal use by the owner to test and refine the experience. | refined | `T063` | Owner-only start expanded to owner/invitees in Step 46. |
| Step 8 | Mobile and desktop have equal priority, with a responsive layout suited to each screen size. | selected | `T010`, `T022`, `T061` | - |
| Step 9 | Use a voice-focused main screen with a central circle or waveform, microphone control, accessible conversation text, and captions beneath the visualization (described by the owner as "like Pingo"). | refined | `T022`, `T059`, `T070`-`T077` | R001 adds a default living ball and optional local rigged-2D import; preserve applicable gallery/account settings. |
| Step 10 | Show only the AI's response in the captions beneath the visualization while the AI is speaking. | selected | `T059` | - |
| Step 11 | Minimalist styling, lavender purple as the default primary accent, light/dark/system theme options, and user-selectable accent color. | selected | `T038` | - |
| Step 12 | Use a lavender circle with subtle listening, thinking, and speaking animations. | refined | `T022`, `T040`, `T070`-`T077` | R001 adds a default living ball and optional local rigged-2D import; preserve applicable gallery/account settings. |
| Step 13 | Users select a ready-made circle image from the app's gallery, with the lavender circle as the default before selection. | refined | `T040`, `T070`-`T077` | R001 adds a default living ball and optional local rigged-2D import; preserve applicable gallery/account settings. |
| Step 14 | The full conversation text view shows both user and AI messages and includes a text input and Send button. | selected | `T023` | - |
| Step 15 | Provide one main companion in the first release, with its name, personality, and selected gallery image editable at any time. | refined | `T017`, `T039`, `T040`, `T041`, `T070`-`T077` | R001 adds a default living ball and optional local rigged-2D import; preserve applicable gallery/account settings. |
| Step 16 | Provide a voice library, voice sample previews, and a speaking-speed control. | refined | `T004`, `T041` | Exact route and three speed choices use later decisions. |
| Step 17 | Emotional speech tone adapts to both the configured personality and the conversation context. | selected | `T068` | - |
| Step 18 | Automatically save conversation history with read, resume, and delete actions. | selected | `T028`, `T043`, `T047`, `T048`, `T050` | - |
| Step 19 | Deleting a conversation removes its message history but keeps its summary and learned personalization memory. | selected | `T050` | - |
| Step 20 | Use one account and synchronize the companion, settings, conversation history, and personalization memory across mobile and desktop. | selected | `T017`, `T036`, `T037` | - |
| Step 21 | Support both Google and email/password sign-in. | selected | `T014`, `T015` | - |
| Step 22 | Users can choose manual session startup or automatic listening when opening the conversation page, subject to microphone permission. | selected | `T033` | - |
| Step 23 | Thai and English interface languages, initially following the device language and switchable through Settings. | selected | `T038` | - |
| Step 24 | Open the text conversation in the existing voice screen, using a desktop side panel and a mobile bottom sheet, both supporting reading and typing. | selected | `T022`, `T023` | - |
| Step 25 | Keep Conversation, History, and Settings in the main navigation. | selected | `T022`, `T038`, `T039`, `T044` | - |
| Step 26 | Use a collapsed menu on both mobile and desktop, opened through a Menu button, to keep the conversation screen uncluttered. | selected | `T022` | - |
| Step 27 | AI responses to typed messages are always delivered as both text and speech, independently of voice-session status. | selected | `T023`, `T027`, `T028` | - |
| Step 28 | Disabling memory stops both new learning and use of existing personalization memory. | selected | `T045` | - |
| Step 29 | Let the AI adapt its replies to the conversation context even when this differs from configured traits, while preserving the saved personality settings unchanged. | selected | `T042`, `T068` | - |
| Step 30 | The owner supplied a tentative future business/cost brief, explicitly left the USD 15 subscription price undecided, and requested moving to backend planning. | reference | `T008`, `T064` | Unverified business brief; USD 15 is not a selected subscription price. |
| Step 31 | Select Gemini 3.8 Flash-Lite TTS, Gemini 3.8 Flash, and Gemini 3.5 Transcribe model families. | validation | `T002`, `T003`, `T004` | Selected identifiers require present availability/capability checks. |
| Step 32 | After clarifying inference modes, the owner selected regular Gemini 3.8 Flash. | selected | `T003`, `T026`, `T048` | - |
| Step 33 | Initially select `gemini-3.5-transcribe-live` for continuous conversation and `gemini-3.5-transcribe` for button-activated speaking. | superseded | `T002`, `T025`, `T030` | Step 35 selects completed-audio STT through OpenRouter for both modes. |
| Step 34 | Select OpenRouter as the preferred API gateway. | validation | `T002`, `T003`, `T004`, `T025`, `T026`, `T027` | Gateway selection retained; historical catalog claims require re-verification. |
| Step 35 | Use OpenRouter for every AI stage. | selected | `T002`, `T025`, `T030` | - |
| Step 36 | Select Next.js, TypeScript, and Supabase for accounts and application data, with Cloudflare as the hosting platform. | selected | `T006`, `T012`, `T013`, `T029` | - |
| Step 37 | Generate summaries and automatic personalization updates when the conversation ends or after inactivity. | selected | `T047`, `T048` | - |
| Step 38 | Select 15 minutes of inactivity before scheduling a conversation summary. | selected | `T047`, `T048` | - |
| Step 39 | Maintain one current summary per conversation. | selected | `T047`, `T048` | - |
| Step 40 | Store conversation summaries plus separate learned fact/preference items. | selected | `T044`, `T048` | - |
| Step 41 | Restore a deleted fact/preference only after an explicit user instruction to remember it again. | selected | `T046`, `T067` | - |
| Step 42 | After memory is re-enabled, learn only from subsequent conversation content. | selected | `T045`, `T047` | - |
| Step 43 | Offer an "Enable memory and save this" button when the user explicitly asks to remember something while memory is disabled. | selected | `T044`, `T045`, `T067` | - |
| Step 44 | Allow automatic updates when newly learned information conflicts with existing fact/preference memory, including items the user edited manually. | selected | `T048` | - |
| Step 45 | Do not notify users about automatic memory creation or updates. | selected | `T044`, `T048` | - |
| Step 46 | Select an invite-only trial for the owner and explicitly permitted invitees. | selected | `T016`, `T063` | - |
| Step 47 | Use an allowed-email list. | selected | `T016` | - |
| Step 48 | Manage the allowed-email list in Settings > Trial Access, accessible only to the owner. | selected | `T016`, `T055` | - |
| Step 49 | Revoking trial access preserves the invitee's account data while blocking application access. | selected | `T055` | - |
| Step 50 | Enforce both a daily voice allowance per account and a shared monthly AI budget for the trial. | refined | `T019`, `T020`, `T021` | Limits and exhaustion semantics use subsequent decisions. |
| Step 51 | Set the default daily voice allowance to 30 minutes per account, shared across that account's devices, voice modes, and conversations. | selected | `T019` | - |
| Step 52 | Count elapsed voice-session time, including silence, pauses, and waiting, from session start to session end. | selected | `T019`, `T033` | - |
| Step 53 | Deduct spoken playback time from the daily allowance for typed-message replies outside an active voice session. | selected | `T019`, `T027` | - |
| Step 54 | Set the shared monthly AI inference budget to USD 10 for all trial accounts combined. | validation | `T008`, `T020`, `T062` | Free-tier suitability and actual funding are not guaranteed. |
| Step 55 | Pause both voice and typed AI conversation when the daily allowance is exhausted, until reset. | selected | `T019`, `T021`, `T060` | - |
| Step 56 | Use UTC as the common reset timezone. | selected | `T019`, `T020`, `T056`, `T057` | - |
| Step 57 | Pause all AI calls at shared monthly budget exhaustion, but allow the owner to raise the cap manually in Settings. | selected | `T020`, `T057`, `T060` | - |
| Step 58 | An owner-raised cap applies only to the current UTC calendar month. | selected | `T057` | - |
| Step 59 | Default to automatic listening on entry to the Conversation page after microphone permission is granted and account/usage checks pass. | selected | `T033` | - |
| Step 60 | Continue an active voice session across in-app navigation to History and Settings, with compact persistent controls. | selected | `T033` | - |
| Step 61 | Allow simultaneous voice sessions for the same account across devices and browser tabs. | selected | `T019`, `T036` | - |
| Step 62 | Simultaneous sessions for the same account use one shared conversation, synchronized messages, and shared response context. | selected | `T036` | - |
| Step 63 | Play each AI reply's audio only on the originating device/tab. | selected | `T027`, `T036` | - |
| Step 64 | Use hold-to-talk in button-activated mode: hold to record, release to stop and submit the spoken turn. | selected | `T024` | - |
| Step 65 | Sending a typed message interrupts the current local AI speech and starts processing the new message without waiting for speech completion. | selected | `T023`, `T031` | - |
| Step 66 | If speech generation or playback fails, display available reply text with a manual "Retry audio" action. | refined | `T027`, `T034` | Current-reply Retry audio regenerates TTS; Step 110 removes reusable audio. |
| Step 67 | Reveal whole words progressively during speech. | selected | `T059` | - |
| Step 68 | Start captions on one row and wrap to additional rows when the sentence fills the available width. | selected | `T059` | - |
| Step 69 | Use all four initial personality presets: Warm and gentle, Playful and talkative, Calm and attentive, and Friendly and direct. | selected | `T039` | - |
| Step 70 | New accounts start with Warm and gentle, without a required personality-selection step before the first conversation. | selected | `T039` | - |
| Step 71 | Use sliders for adjustment of personality traits, including playfulness, gentleness, and response length. | selected | `T039` | - |
| Step 72 | Preserve the current saved trait slider values when switching personality presets. | selected | `T039` | - |
| Step 73 | Allow the AI to initiate a conversational follow-up after a period of user silence during an active continuous voice session. | selected | `T035` | - |
| Step 74 | Wait 30 seconds after local AI speech finishes, with no new user speech or sent message, before initiating a proactive follow-up in an eligible active continuous session. | selected | `T035` | - |
| Step 75 | If the user does not answer, allow one additional proactive follow-up after another 30 seconds of silence following the first follow-up's speech. | selected | `T035` | - |
| Step 76 | Enable automatic conversation follow-ups by default and allow users to turn them off or on in Settings. | selected | `T035`, `T037`, `T038` | - |
| Step 77 | After the second unanswered proactive follow-up finishes speaking, wait a further two minutes without user input, then automatically pause the local session's microphone listening and elapsed-session quota accounting. | selected | `T033`, `T035` | - |
| Step 78 | Attempt to continue the existing local voice session when the user switches tabs/apps or locks the screen, where the browser and device support it. | validation | `T033`, `T061` | Continue in background only where the actual browser/device permits. |
| Step 79 | Include the companion picture, session status, captions, and pause/resume and stop controls, with a control menu that users can hide and reveal. | refined | `T078`-`T082` | R001 confirms cross-app presence in the first release; Windows selected; runtime/version evidence pending; Android floating and other desktop OS clients later. |
| Step 80 | Keep the user's transcribed text in conversation history without persistently storing the user's recordings or offering playback of those recordings. | selected | `T024`, `T025`, `T049`, `T060` | - |
| Step 81 | Initially selected temporary caching for generated AI audio and TTS regeneration when unavailable. | superseded | `T027`, `T034` | Step 110 forbids stored/reusable AI audio, replacing the cache choice. |
| Step 82 | Automatically delete message history after seven days, replacing the proposed 90-day period. | selected | `T049` | - |
| Step 83 | Expire the conversation's message history after seven days without a new spoken or typed user turn in that conversation. | selected | `T049` | - |
| Step 84 | Allow users to delete their own account and personal app data from Settings after explicit confirmation. | selected | `T058` | - |
| Step 85 | Wait seven days after confirmed account-deletion requests before permanently deleting the account and personal app data. | selected | `T058` | - |
| Step 86 | Restrict a pending-deletion account to deletion status and explicit cancellation during the seven-day wait. | selected | `T058` | - |
| Step 87 | After permanent account deletion, require the owner to authorize the email again before a fresh account can access the private trial. | selected | `T058` | - |
| Step 88 | Start a new conversation by default when a new voice session begins after all previous sessions have ended. | selected | `T036` | - |
| Step 89 | Switching to another conversation or resuming a different history thread moves every active session for the account to that same shared conversation. | selected | `T036` | - |
| Step 90 | Give a short AI greeting first when a new conversation starts, following the configured personality, then let the user speak. | selected | `T051` | - |
| Step 91 | Personalize the opening greeting with relevant eligible saved preferences or interests when memory is enabled. | selected | `T051` | - |
| Step 92 | Include web search in the first release using Parallel Fast through OpenRouter, with an account-synchronized Web search on/off toggle in Settings. | selected | `T005`, `T054` | - |
| Step 93 | Web search is off by default for new accounts. | selected | `T005`, `T054` | - |
| Step 94 | Display clickable source links only in the chat panel, attached to the relevant web-assisted AI reply. | selected | `T005`, `T054` | - |
| Step 95 | Limit web search to ten actual search calls per account per UTC day, shared across devices, with reset at 00:00 UTC (07:00 Thailand). | selected | `T005`, `T054` | - |
| Step 96 | Retry recoverable transcription or text-reply generation failures automatically once, then show a manual Retry action if still unsuccessful. | selected | `T034` | - |
| Step 97 | Pause microphone listening and elapsed-session quota accounting when connectivity is lost. | selected | `T034` | - |
| Step 98 | The app's product name is Laven AI. | selected | `T022`, `T039` | - |
| Step 99 | Validate voice quality and conversational flow first, including Thai/English speech, interruptions, and response timing. | selected | `T028`, `T061` | - |
| Step 100 | Target first audible AI speech within three seconds after the user finishes speaking under normal conditions, including utterance-end detection and the full selected STT/LLM/TTS pipeline. | validation | `T030`, `T061` | Measure original end-of-user-speech to first-audible target, including silence wait. |
| Step 101 | Plan for one to five participants in the initial private trial, including the owner. | scope | `T063` | One-to-five expected trial participants; not a hard registration cap. |
| Step 102 | Use a custom domain for the private trial of Laven AI. | validation | `T062` | Chosen trial domain remains unpurchased; availability/setup unverified. |
| Step 103 | The desired domain is lavenai.space. | validation | `T062` | Chosen trial domain remains unpurchased; availability/setup unverified. |
| Step 104 | The owner does not yet have accounts for Cloudflare, Supabase, or OpenRouter. | state-dependent | `T007`, `T008`, `T062` | Initial account absence must be refreshed before setup; no provisioning assumed. |
| Step 105 | Keep the project locally and in a private GitHub repository, with Git version history and a remote copy. | alignment issue | `T069` | Blueprint planned private GitHub storage; owner-supplied LavenAi/1 is currently public. |
| Step 106 | The owner does not yet have a GitHub account. | superseded state | `T069` | GitHub account/auth and initial push are now verified; no new GitHub account needed. |
| Step 107 | No fixed deadline for the first usable private trial. | scope | `T001`, `T063` | No fixed launch deadline selected. |
| Step 108 | The owner will test using Android and a web browser. | selected | `T061` | - |
| Step 109 | Google Chrome is the owner's primary test browser for the selected Android and web-browser test surfaces. | selected | `T061` | - |
| Step 110 | Do not store generated AI audio for reuse, replacing the temporary-cache choice. | selected | `T027`, `T034`, `T049`, `T060` | - |
| Step 111 | The owner requested keeping only text. | selected | `T027`, `T034`, `T049`, `T060` | - |
| Step 112 | Default to short, concise replies, roughly one to three sentences. | selected | `T039`, `T042` | - |
| Step 113 | Use short topic-based conversation titles with dates in History. | selected | `T043` | - |
| Step 114 | When switching between continuous conversation and hold-to-talk during local AI speech, stop that speech and change mode immediately. | selected | `T032` | - |
| Step 115 | Offer both flowers/nature/minimal abstract images and cute illustrated characters/animals in the companion-image gallery. | refined | `T040`, `T070`-`T077` | R001 adds a default living ball and optional local rigged-2D import; preserve applicable gallery/account settings. |
| Step 116 | Include an optional free-text field for additional personality/conversation-style instructions in Settings > My Companion, alongside presets and sliders. | selected | `T039`, `T042` | - |
| Step 117 | Give user-written custom personality instructions precedence over conflicting preset/slider style preferences. | selected | `T039`, `T042` | - |
| Step 118 | Include Add memory in Settings > Memory for directly entering and saving a fact/preference. | selected | `T044`, `T067` | - |
| Step 119 | Wait approximately two seconds after detected user speech stops before submitting the utterance for transcription in continuous mode. | selected | `T030`, `T061` | - |
| Step 120 | Retain the original three-second target from actual user speech completion to first audible AI speech, including the approximately two-second utterance-end silence wait. | selected | `T030`, `T061` | - |
| Step 121 | Begin speaking when the first completed sentence is ready while the remaining reply is generated. | selected | `T027`, `T028` | - |
| Step 122 | Speaking over the AI or sending a new message stops both local speech and unfinished generation of the old reply. | selected | `T031` | - |
| Step 123 | In an active continuous session, pressing the microphone control mutes only microphone input. | selected | `T032` | - |
| Step 124 | Continue automatic silence-triggered AI follow-ups while the microphone is manually muted, subject to the saved follow-up toggle and normal access/usage controls. | selected | `T035` | - |
| Step 125 | Correct transcription errors by sending an ordinary new typed message, such as clarifying what the user meant. | selected | `T023` | - |
| Step 126 | Show a brief optional companion-setup screen after first eligible sign-in, offering personality, gallery image, and voice choices with a Skip action. | refined | `T053` | Interview-first sequence is defined by Step 140. |
| Step 127 | Include optional user-introduction questions at the beginning of first eligible sign-in/use, alongside companion setup. | refined | `T052`, `T053` | AI interview in Step 129 replaces form-style quiz. |
| Step 128 | Use approximately three to five introduction questions. | selected | `T052`, `T053` | - |
| Step 129 | The owner proposed having the AI interview new users instead of using a form-style quiz. | selected | `T052`, `T053` | - |
| Step 130 | Use voice as the primary onboarding-interview channel, with readable text and typed-answer fallback. | selected | `T052`, `T053` | - |
| Step 131 | The owner requested revised interview topics and asked for three variants. | reference | `T052` | Three alternatives were proposed; Step 132 selects Variant 1. |
| Step 132 | Select Variant 1, Start with enjoyable things, supplemented with preferred name/nickname, interests/hobbies, expectations of an AI companion, and conversation-style preferences. | selected | `T052`, `T053` | - |
| Step 133 | Include the three language-learning questions during initial onboarding as an optional branch. | selected | `T052`, `T053` | - |
| Step 134 | Save eligible onboarding facts/preferences automatically after interview completion, without an ordinary pre-save review screen. | selected | `T053`, `T067` | - |
| Step 135 | End the completed onboarding interview and start a new normal conversation. | selected | `T036`, `T051`, `T053` | - |
| Step 136 | Start a new interview on the next visit if the app closed before completion. | selected | `T053` | - |
| Step 137 | Allow owner-only adjustment of each trial account's daily allowance, including the owner's account, in Settings > Trial Access. | selected | `T056` | - |
| Step 138 | Apply each owner-set individual allowance override only to the current UTC day. | selected | `T056` | - |
| Step 139 | Display only the existing remaining-time indicator, without additional five-minute/one-minute advance notices, popups, sounds, or AI-spoken warnings. | selected | `T019`, `T033`, `T056` | - |
| Step 140 | Interview first using saved/default companion settings, then offer optional personality, gallery image, and voice customization. | selected | `T053` | - |
| Step 141 | Recommend a personality preset, gallery image, and voice after the interview using the user's interview answers. | selected | `T053`, `T065` | - |
| Step 142 | Stop active conversations immediately when the owner revokes account access, including microphone capture, speech playback, captions, and unfinished generation on all of that account's active surfaces. | selected | `T055`, `T060` | - |
| Step 143 | Discard the unfinished utterance when the user mutes during speech before its audio has been submitted for transcription. | selected | `T032` | - |
| Step 144 | Discard the unsubmitted utterance and switch voice modes immediately when the user changes modes during local recording. | selected | `T032` | - |
| Step 145 | Switch input mode immediately while allowing an already submitted turn to finish transcription, reply generation, and normal text-and-speech delivery when the change occurs before AI playback starts. | selected | `T032` | - |
| Step 146 | Use Laven as the initial companion name for new accounts, editable in Settings > My Companion. | selected | `T017`, `T039` | - |
| Step 147 | Use English as the initial interface fallback when the device language is neither Thai nor English and no user preference exists. | selected | `T038` | - |
| Step 148 | Stop current reply generation and speech immediately when the account's daily allowance is exhausted, without a completion grace period. | selected | `T019`, `T060` | - |
| Step 149 | Stop current response generation and speech immediately for all accounts when the shared monthly AI budget is exhausted. | selected | `T020`, `T021`, `T047`, `T057`, `T060` | - |
| Step 150 | Selecting a voice preview in Settings pauses the active local voice conversation before sample playback. | selected | `T041` | - |
| Step 151 | Do not deduct Settings voice-sample playback from the daily conversation-time allowance. | selected | `T041` | - |
| Step 152 | Starting a voice preview cancels unfinished processing of the local accepted turn, including STT or reply generation, while preserving text already saved. | selected | `T041` | - |
| Step 153 | Voice previews use the currently selected interface language only: Thai when the interface is Thai, English when it is English. | selected | `T041` | - |
| Step 154 | Choose the reply language from the user's typed message, supporting Thai, English, and mixed Thai-English as in voice conversation. | selected | `T042` | - |
| Step 155 | Greet in the selected interface language before the first user input in a new conversation. | selected | `T051` | - |
| Step 156 | Newly saved personality presets, traits, and custom instructions apply to the next reply whose generation has not yet begun, without requiring a new conversation. | selected | `T037`, `T039`, `T042`, `T068` | - |
| Step 157 | Let the current spoken reply finish using its existing voice and speed when new values are saved during speech. | selected | `T041`, `T068` | - |
| Step 158 | Automatically save changes in Settings > My Companion without a Save button. | selected | `T037`, `T039`, `T041` | - |
| Step 159 | Use five discrete labeled levels for playfulness, gentleness, and response length, from Very low to Very high, rather than a 0–100 scale. | selected | `T017`, `T039` | - |
| Step 160 | Initialize new accounts with the Warm and gentle preset, Medium playfulness (3/5), High gentleness (4/5), and Short replies (2/5). | selected | `T017`, `T039` | - |
| Step 161 | Offer three speaking-speed choices: Slow, Normal, and Fast. | selected | `T004`, `T041` | - |
| Step 162 | Use the companion's currently saved personality to guide voice-sample delivery, including expressive tone. | selected | `T004`, `T041`, `T068` | - |
| Step 163 | Show History as a list without a user-facing search field. | selected | `T043` | - |
| Step 164 | Order History by latest accepted user conversation activity first. | selected | `T043` | - |
| Step 165 | Allow manual renaming of automatically titled conversations. | selected | `T043` | - |
| Step 166 | Allow selecting multiple History entries and deleting their message histories together, alongside individual deletion. | selected | `T050` | - |
| Step 167 | Add a Settings toggle to show/hide AI captions, enabled initially and synchronized across the account. | selected | `T038`, `T059` | - |
| Step 168 | No memory search for users; retain their view/edit/delete and memory-toggle controls. | selected | `T044`, `T066` | - |
| Step 169 | Use separate Facts/preferences and Conversation summaries tabs within Settings > Memory, preserving existing management actions and the absence of user search. | selected | `T044`, `T066` | - |
| Step 170 | Add Reset personality: restore Warm and gentle and initial 3/5, 4/5, 2/5 traits, and clear custom instructions. | selected | `T039` | - |
| Step 171 | New accounts start with Normal speaking speed. | selected | `T017`, `T041` | - |
| Step 172 | Limit additional personality instructions to 1,000 characters and show a counter. | selected | `T039` | - |
| Step 173 | Limit developer memory search to the developer's own account and explicitly designated test accounts. | delegated | `T066` | - |
| Step 174 | Confirm Reset personality before applying it. | delegated | `T039` | - |
| Step 175 | Preserve manually saved conversation titles through later automatic title/summary updates. | delegated | `T043` | - |
| Step 176 | Require confirmation before individual or multi-select History deletion. | delegated | `T050` | - |
| Step 177 | Require explicit Save when editing an existing memory item or conversation summary; offer Cancel to discard the edit draft. | delegated | `T044` | - |
| Step 178 | After deletion confirmation, stop all active sessions and unfinished interactive work attached to the selected shared conversation before deleting its message history. | delegated | `T050` | - |
| Step 179 | Cap a single captured utterance at 120 seconds, accommodating longer companion conversation while bounding transient buffers. | delegated | `T024`, `T030` | App limit still requires provider/device validation. |
| Step 180 | Collect initial private-trial feedback outside the app through the owner's existing manual communication channel. | delegated | `T064` | Feedback is manual/outside the app; no messaging integration authorized. |
| Step 181 | If the selected TTS route fails actual Thai voice acceptance tests, prepare an OpenRouter alternative with verified capabilities and cost for owner review before adopting it. | delegated | `T004`, `T008` | Prepare a verified fallback for owner review, not a silent model switch. |
| Step 182 | Allow clearly identified sentence-level captions temporarily in the first prototype if accurate word-to-audio alignment is not ready. | delegated | `T022`, `T027`, `T029`, `T059` | Sentence captions allowed only in prototype; final accurate word captions retained. |

## Later Instructions and Unnumbered Requirements

| Source / need | Mapped tasks or planning artifact | Coverage / remaining check |
| --- | --- | --- |
| Actual online startup; mobile/desktop browser platform reconfirmed | T012, T022, T028-T029, T061-T063 | Real accounts/cloud/AI/deployed evidence required; a local mock does not count as launch |
| Director role; owner is developer; three friends' roles proposed | Backlog People and Review; progress tracker | No agent dispatched by this planning work; named task owners/reviewers remain unassigned |
| Small-task execution and progress visibility | T001; task-backlog.md; progress_tracking.md | Stable IDs, dependencies, acceptance evidence, single-task prompt, and honest status rules |
| Strong creative execution with verified delivery | T010, T022, T038-T042, T059-T063; build-agent-prompt.md | Design freedom within selected behavior; observe mobile/desktop rendering; no silent scope expansion |
| Owner-supplied GitHub repository and authorized initial push | T069; README.md | Initial docs commit exists; public/private alignment is unresolved; no repository visibility change performed |
| Original/licensed gallery assets, accessibility, and reduced-motion behavior | T010, T022, T038, T040, T061 | Assets need provenance; bilingual typography, focus, contrast, touch controls, and actual device checks |
| Safe owner bootstrap, recovery/account linking, RLS, and server-only credentials | T007, T013-T016, T021, T058, T060, T062 | Choose evidenced secure implementation defaults; handle last-owner deletion explicitly |
| Only text kept by the app; transient audio and separate provider retention | T024-T027, T034, T049-T050, T058, T060, T062 | No audio files/caches/replay/log payloads; third-party retention remains separately unverified |
| Durable eligible summary jobs and exact inactivity scheduling | T006, T018, T045-T049, T053, T060, T062 | Idempotency, source eligibility, memory-off boundaries, abandoned onboarding, retries, and late-result guards |
| Cost is all AI stages/jobs/search/previews; target USD 10 shared cap | T008, T019-T021, T041, T054, T056-T057, T060-T061 | Actual reservations/usage/cancellation behavior need evidence; no billing-overshoot guarantee or assumed free funding |
| New-account defaults apply only to new accounts, not overwrite saved ones | T017, T037-T042, T051, T053 | Existing account settings preserved; defaults and saved drafts differentiated |
| Proposed engineering/visual defaults in blueprint Section 6 | T012-T013, T022, T038-T044, T047-T050 | Autosave timing, pagination, field limits, gallery size, and adapter details remain proposals, not falsely confirmed selections |
| Pending explicit-memory requests: duplicate/cancellation/save failure handling | T018, T044-T046, T067 | Specify request identity/lifetime and reject stale confirmation/writes; do not claim a pending save succeeded |
| Initial private trial expected 1-5; no fixed deadline/price | T008, T063-T064 | Expected size is not a registration cap; commercial pricing and public launch remain undecided |
| Extra languages, full tutor, Pingo-like future persona, official purchased mascot, 3D import | Backlog Later Work; R001 | Later work; first-release local 2D import remains selected |
| R001: default ball and optional first-release local rigged-2D import | T070-T077; avatar-plan.md | Owner corrected Oct 10: ball has eyes and NO MOUTH; no ball lip-sync. Imported files local only; supported rig mappings/format/SDK/device evidence pending; no cloud file sync |
| R001: cross-app floating companion and hideable controls | T078-T082; avatar-plan.md | Confirmed in first release; Windows selected; runtime/version evidence pending; T082 required before rollout |
| Team lives in Laos and is exploring global funding | T008; startup-launch-plan.md | No company jurisdiction, grant eligibility, investment, or funded allowance established |

## Remaining Alignment and Validation

1. Repository visibility: Step 105 planned private storage. Current `LavenAi/1` is public, verified via GitHub metadata on October 9, 2026. The owner supplied that repo and authorized a push, but has not explicitly resolved the private/public requirement. T069 records this decision dependency; no visibility change is made here.
2. Models/runtime/email: exact available identifiers, Thai speech quality, voice speed/timing, deployment adapter/runtime, ordinary invitee email delivery, and credentials need the Phase 1 evidence and live checks. Historical links/prices are not treated as current proof.
3. Funding/live evidence: actual provider credit, authorized paid-test allowance, target-device access, deployment/domain setup, and measured costs/latency are pending. These do not justify declaring a mock complete.
4. Detailed defaults: implementation must resolve remaining factual categories, equivalent deleted-fact matching, safe auth linking/recovery, owner deletion, scheduling/metering boundaries, and update ordering without changing selected behavior. Record any material conflict or unsupported target for owner review.

R001 is mapped separately from the original 182 numbered decisions; no new discovery Step numbers were invented. Its pending details are in avatar-plan.md and the tracker.

Mapping coverage means the needs are represented in work assignments. It does not mean all 182 decisions are separate features, all proposed defaults are mandatory, all targets are feasible, or any application requirement has already passed acceptance.
